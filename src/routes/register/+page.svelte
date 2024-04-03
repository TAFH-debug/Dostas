<script>
  import Header from "../Header.svelte";
  import { onMount } from 'svelte';
  const today = new Date();
  let passwordConfirm, validAge = true, validEmail = true, validUsername = true, matching = true, text = "Ok.", display, color, passwordError = [], usernameError = [];
  let userData = {
    email:'',
    username:'',
    password: '',
    birthdate: '',
  }

  onMount(() => {
    const todayFormatted = `${today.getFullYear()}-${String(today.getMonth() + 1).padStart(2, '0')}-${String(today.getDate()).padStart(2, '0')}`;
    document.getElementById('birthdate').max = todayFormatted;
  });
  function emailCheck() {
    const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    validEmail = (emailRegex.test(userData.email)) ? true : false;
  }
  function usernameCheck() {
    usernameError= [];
    const requirements = [
      { name: 'can only have letters (a-z, A-Z) and underscores (_).', regex: /^[A-Za-z_]+$/ },
      { name: 'can only start with letters', regex: /^[A-Za-z]/ },
      { name: 'must between 3 and 20 characters', regex: /^.{3,20}$/ }
    ];
    requirements.forEach(req => {
      if (!req.regex.test(userData.username)) {
        usernameError.push(req.name);
      }
    });
    if (validUsername) {
      // sadasdsadsads
      // Проверить если имя уже существует
    }
  }
  function birthdateCheck() {
    const birthdate = new Date(userData.birthdate);
    var age = today.getFullYear() - birthdate.getFullYear();
    var m = today.getMonth() - birthdate.getMonth();
    if (m < 0 || (m === 0 && today.getDate() < birthdate.getDate())) {
      age--;
    }
    validAge = age >= 13;
  }
  function passwordReqCheck() {
    passwordError = [];
    const requirements = [
        { name: 'an Uppercase letter', regex: /[A-Z]/ },
        { name: 'a Lowercase letter', regex: /[a-z]/ },
        { name: 'a Digit', regex: /\d/ },
        { name: 'no Spaces', regex: /\s/, inverse: true },
        // { name: 'a Special character', regex: /[!@#$%^&*()_+\-=\[\]{};':"\\|,.<>\/?]+/ },
    ];
    if (userData.password.length >= 8) {
      requirements.forEach(req => {
        if (req.inverse) {
          if (req.regex.test(userData.password)) {
            passwordError.push(req.name);
          }
        } 
        else {
          if (!req.regex.test(userData.password)) {
            passwordError.push(req.name);
          }
        }
      })
    }
    else {
      passwordError.push("at least 8 characters");
    }
  }
  function passwordMatchCheck() {
    if (passwordConfirm.trim() === '' || passwordConfirm !== userData.password) {
      matching = false;
    }
    else {matching = true;}
  }

  // Talim/Damir, ti dolzhen sdelat eto!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
  function register() {
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
      <input class="form_input" type="text" bind:value="{userData.email}" on:change={emailCheck}/>
      {#if !validEmail}
        <div>
          <p>Invalid email</p>
        </div>
      {/if}
      <div class="form_label">Username</div>
      <input class="form_input" type="text" bind:value="{userData.username}" on:change={usernameCheck}/>
      {#if usernameError.length > 0}
        <div>
          <ul>
            {#each usernameError as error}
              <li>{error}</li>
            {/each}
          </ul>
        </div>
      {/if}
      <div class="form_label">Date of Birth</div>
      <input class="form_input" type="date" id="birthdate" bind:value={userData.birthdate} on:change={birthdateCheck} min="1900-01-01">
      <div class="form_label">Password</div>
      <input class="form_input" type="password"  bind:value="{userData.password}" on:input={passwordReqCheck}/>
      {#if passwordError.length > 0}
        <div>
          <p>Password must have:</p>
          <ul>
            {#each passwordError as requirement}
              <li>{requirement}</li>
            {/each}
          </ul>
        </div>
      {/if}
      <div class="form_label">Confirm Password</div>
      <input class="form_input" type="password" bind:value="{passwordConfirm}" on:input={passwordMatchCheck}/>
      {#if !matching}
        <div>
          <p>Passwords do not match</p>
        </div>
      {/if}
      <input class="form_button" type="button" value="Register" on:click={register}/> <!--pomenyayte zdes-------------------------------------------->

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
    font-size: 100%;
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