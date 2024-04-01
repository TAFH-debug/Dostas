<script>
  import Header from "../Header.svelte";

  let loginb, passwordb, text = "Ok.", display, color;

  function send() {
    fetch('http://localhost:3000/api/login', {
      method: 'POST',
      headers: {
        'Accept': 'application/json',
        'Content-Type': 'application/json'
      },
      body: JSON.stringify({
        login:  loginb,
        password: passwordb
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
      <div class="form_label">Login</div>
      <input class="form_input" type="text" bind:value="{loginb}"/>
      <div class="form_label">Password</div>
      <input class="form_input" type="text" bind:value="{passwordb}"/>
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
    height: 100%;
    width: 100%;
    background-color: #020b0f;
    align-items: center;
    display: flex;
    justify-content: center;
  }
  .form_cont {
    background-color: #27007d;
    height: 50%;
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
</style>
