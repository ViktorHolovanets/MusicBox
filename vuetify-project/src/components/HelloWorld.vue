<template>
  <div class="main">
    <input type="checkbox" id="chk" aria-hidden="true">

    <div class="login">
      <form class="form">
        <label for="chk" aria-hidden="true">Log in</label>
        <input class="input" type="email" name="email" placeholder="Email" required="">
        <input class="input" type="password" name="pswd" placeholder="Password" required="">
        <button>Log in</button>
      </form>
    </div>

    <div class="register">
      <form class="form">
        <label for="chk" aria-hidden="true">Register</label>
        <input class="input" type="text" name="txt" placeholder="Username">
        <input class="input" type="email" name="email" placeholder="Email">
        <input class="input" type="password" name="pswd" placeholder="Password">
        <button>Register</button>
      </form>
    </div>
  </div>
</template>

<script setup lang="ts">
import {onMounted} from 'vue';
import axios from "axios";

onMounted(async () => {

  let test = await axios.get("http://localhost/api/admin/users/pagination?Page=1&size=10", fun());
  console.log(test);
});
</script>
<style scoped>
.main {
  position: relative;
  display: flex;
  flex-direction: column;
  background-color: #240046;
  max-height: 420px;
  overflow: hidden;
  border-radius: 12px;
  box-shadow: 7px 7px 10px 3px #24004628;
}

.form {
  display: flex;
  flex-direction: column;
  gap: 14px;
  padding: 24px;
}

/*checkbox to switch from sign up to login*/
#chk {
  display: none;
}

/*Login*/
.login {
  position: relative;
  width: 100%;
  height: 100%;
}

.login label {
  margin: 25% 0 5%;
}

label {
  color: #fff;
  font-size: 2rem;
  justify-content: center;
  display: flex;
  font-weight: bold;
  cursor: pointer;
  transition: .5s ease-in-out;
}

.input {
  width: 100%;
  height: 40px;
  background: #e0dede;
  padding: 10px;
  border: none;
  outline: none;
  border-radius: 4px;
}

/*Register*/
.register {
  background: #eee;
  border-radius: 60% / 10%;
  transform: translateY(5%);
  transition: .8s ease-in-out;
}

.register label {
  color: #573b8a;
  transform: scale(.6);
}

#chk:checked ~ .register {
  transform: translateY(-60%);
}

#chk:checked ~ .register label {
  transform: scale(1);
  margin: 10% 0 5%;
}

#chk:checked ~ .login label {
  transform: scale(.6);
  margin: 5% 0 5%;
}

/*Button*/
.form button {
  width: 85%;
  height: 40px;
  margin: 12px auto 10%;
  color: #fff;
  background: #573b8a;
  font-size: 1rem;
  font-weight: bold;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: .2s ease-in;
}

.form button:hover {
  background-color: #6d44b8;
}
</style>
