<template>

  <div class="jumbotron card bg-dark text-white" id="avatar">
    <div class="col-sm">
      <img src="@/assets/logo.png" alt width="200px" class="rounded-circle" id="avatar" />
      <h1 class="display-4">Registro de pacientes</h1>
    </div>
    <h2 class="lead">consigue tu hora aca</h2>
    <hr class="my-4" />
    <div class="row">
      <!-- aca va el formulario para resistro -->
      <form class="col-sm" @submit.prevent="register">
        <div class="form-group">
          <p>La red de salud mas grande del pais</p>
          <label>Register Name</label>
          <input type="text" class="form-control" required="required" v-model="register_name" />
        </div>
        <div class="form-group">
          <label>Email address</label>
          <input type="email" class="form-control" required="required" v-model="register_email" />
        </div>
        <div class="form-group">
          <label>Password</label>
          <input
            type="password"
            class="form-control"
            required="required"
            v-model="register_password"
          />
        </div>
        <div class="form-group">
          <label>Confirm your Password</label>
          <input
            type="password"
            class="form-control"
            required="required"
            v-model="register_password_confirm"
          />
        </div>
        <button type="submit" class="btn btn-primary">Registro</button>
      </form>

      <!-- aca va el formulario para login  -->
      <form class="col-sm" @submit.prevent="login">
        <div class="form-group">
          <p>Revisas tus horas aca</p>
          <label>Email address</label>
          <input type="email" class="form-control" v-model="login_email" />
        </div>
        <div class="form-group">
          <label>Password</label>
          <input type="password" class="form-control" v-model="login_password" />
        </div>
        <button type="submit" class="btn btn-primary">Login</button>
      </form>
    </div>
  </div>
  
</template>

<script>
// import { db } from "@/firebase";
export default {
  name: "Login",
  data() {
    return {
      login_email: "",
      login_password: "",

      register_email: "",
      register_password: "",
      register_password_confirm: "",
      register_name: "",
    };
  },
  methods: {
    login() {
      this.$store.dispatch("login", {
        email: this.login_email,
        password: this.login_password,
      });
    },
    register() {
      if (this.register_password != this.register_password_confirm) {
        alert("se te moskeo la pass");
        return;
      }
      // aca hacemos el registro que luego enviamos a main para guardar en Data Firebase
      this.$store.dispatch("register", {
        email: this.register_email,
        password: this.register_password,
        name: this.register_name,
      });
    },
  },
};
</script>
<style scoped>




</style>