<script>
    import Header from "../Header.svelte";
  
  </script>
  
  <Header/>
  <link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Poppins">
  <div class="body">
      <div class="container">
        <div class="form_cont">
            <div class="form_label">Login</div>
            <input class="form_input" type="text"/>
            <div class="form_label">Password</div>
            <input class="form_input" type="text"/>
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
        background-color: #3700ae;
        height: 20px;
        width: 80%;
        padding: 5px;
        margin: 5px 10%;
    }

    .form_label {
        margin: 5px 10%;
        font-size: 20px;
        font-family: Arial, Helvetica, sans-serif;
    }

    .form_input:active, :hover, :focus {
        outline: none;
        outline-offset: 0;
    }
  </style>
  