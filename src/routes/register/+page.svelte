<script>
  import Header from "../Header.svelte";


  let missingRequirements = [];
  let passwordActual, passwordConfirm, matching = true, text = "Ok.", display, color;
  let userData = {
    email:'',
    username:'',
    password: '',
    dob: '',
  }

  function passwordReqCheck() {
    missingRequirements = [];
    const requirements = [
        { name: 'an Uppercase letter', regex: /[A-Z]/ },
        { name: 'a Lowercase letter', regex: /[a-z]/ },
        { name: 'a Digit', regex: /\d/ },
        // { name: 'a Special character', regex: /[!@#$%^&*()_+\-=\[\]{};':"\\|,.<>\/?]+/ },
    ];
    requirements.forEach(req => {
      if (!req.regex.test(passwordActual)) {
        missingRequirements.push(req.name);
        console.log("added " + req.name)
      }
    })
    if (passwordActual.length < 8) {
      missingRequirements.push("at least 8 characters");
    }
  }
  function notMatching() {
    if (passwordConfirm.trim() === '' || passwordConfirm !== passwordActual) {
      matching = false;
    }
    else {
      matching = true;
    }
  }
  function validateDOB() {
    const dob = new Date(userData.dob);
    const today = new Date();
    const age = Math.floor((today - dob) / (1000 * 60 * 60 * 24 * 365.25));
    if (age > 12) {return true}
    else {return false}
  }
  function send() {
      fetch('http://localhost:3000/api/register', {
        method: 'POST',
        headers: {
          'Accept': 'application/json',
          'Content-Type': 'application/json'
        },
        body: JSON.stringify({
          userData
        })
      })
      .then((resp => resp.json()))
      .then(
        (resp) => {
          if (resp['is_ok'] == "true") {
            text = "Ok.";
            display = "block";
            color = "green";
          }
          else {
            color = "red";
            text = resp['reason'];
            display = "block";
          }
        }
      ).catch(
        (e) => console.log(e)
      )
  }
</script>

<Header />
<link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Poppins" />
<div class="body">

  <div class="container">
    
    <div class="form_cont">
      
      <div class="form_label">Email</div>
      <input class="form_input" type="text" bind:value="{userData.email}"/>
      <div class="form_label">Username</div>
      <input class="form_input" type="text" bind:value="{userData.username}"/>

      <div class="form_label">Date of Birth</div>
      <input class="form_input" type="date" id="dob" bind:value={userData.dob} on:change={validateDOB}>

      <div class="form_label">Password</div>
      <input class="form_input" type="password"  bind:value="{passwordActual}" on:input={passwordReqCheck}/>
      {#if missingRequirements.length > 0}
        <div>
          <p>Password must have:</p>
          <ul>
            {#each missingRequirements as requirement}
              <li>{requirement}</li>
            {/each}
          </ul>
        </div>
      {/if}
      <div class="form_label">Confirm Password</div>
      <input class="form_input" type="password" bind:value="{passwordConfirm}" on:input={notMatching}/>
      {#if !matching}
        <div>
          <p>Passwords do not match</p>
        </div>
      {/if}
      <input class="form_button" type="button" value="Send" on:click={send}/>

      <div class="form_status" style:display={display} style:color={color}>{text}</div>


    </div>

  </div>
</div>

<style>
  .body {
    background-color: #020b0f;
    height: 100%;
    width: 100%;
  }
  .container {
    /* height: 100%; */
    width: 100%;
    /* margin: 30px 0px; */
    background-color: #020b0f;
    align-items: center;
    display: flex;
    justify-content: center;
    transform: translateY(20px);
  }
  .form_cont {
    background-color: #27007d;
    padding: 10px 0px;
    height: fit-content;
    width: 30%;
    border-radius: 10px;
    display: flex;
    justify-content: center;
    flex-direction: column;
  }
  .form_input {
    color: white;
    background-color: #3700ae;
    height: 30px;
    width: 80%;
    padding: 5px;
    margin: 5px 10%;
    border: none;
    font-size: 150%;
  }
  .form_label {
    color: white;
    margin: 5px 10%;
    font-size: 20px;
    font-family: Arial, Helvetica, sans-serif;
  }
  .form_input:active,
  :hover,
  :focus {
    outline: none;
    outline-offset: 0;
  }
  .form_button {
    background-color: aliceblue;
    width: 40%;
    margin-top: 10px;
    margin-left: 10%;
    border: none;
    border-radius: 10px;
    height: 40px;
    font-size: 20px;
  }

  .form_status {
    display: none;
    color: white;
    margin: 5px 10%;
    font-size: 20px;
    font-family: Arial, Helvetica, sans-serif;
  }
  .form_cont p, ul {
    color: white;
    margin: 5px 10%;
    font-size: 10px;
    font-family: Arial, Helvetica, sans-serif;
  }
</style>
