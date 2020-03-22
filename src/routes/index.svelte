<script>
  import axios from "axios";

  async function login(event) {
    event.preventDefault();
    let res = axios.post(
      "https://62806eb5-9d24-4288-ab86-225eaf036470.mock.pstmn.io/login"
    );
    location.replace("home");
  }
</script>

<!-- Default form login -->
<form class="text-center border border-light p-5" on:submit={login}>

  <p class="h4 mb-4">Sign in</p>

  <!-- Email -->
  <input
    name="email"
    type="email"
    id="defaultLoginFormEmail"
    class="form-control mb-4"
    placeholder="E-mail" />

  <!-- Password -->
  <input
    name="password"
    type="password"
    id="defaultLoginFormPassword"
    class="form-control mb-4"
    placeholder="Password" />

  <div class="d-flex justify-content-around">
    <div>

      <!-- Sign in button -->
      <button class="btn btn-info btn-block my-4" type="submit">Sign in</button>

      <!-- Register -->
      <p>
        Not a member?
        <a href="">Register</a>
      </p>

      <!-- Social login -->
      <p>or sign in with:</p>

      <a href="#" class="mx-2" role="button">
        <i class="fab fa-facebook-f light-blue-text" />
      </a>
      <a href="#" class="mx-2" role="button">
        <i class="fab fa-twitter light-blue-text" />
      </a>
      <a href="#" class="mx-2" role="button">
        <i class="fab fa-linkedin-in light-blue-text" />
      </a>
      <a href="#" class="mx-2" role="button">
        <i class="fab fa-github light-blue-text" />
      </a>

    </div>
  </div>
</form>
<!-- Default form login -->
