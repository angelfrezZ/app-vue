<template>
  <form @submit.prevent="boton" class="container">
    <div class="mb-3">
      <label for="exampleInputEmail1" class="form-label">Email address</label>
      <input
        v-model="user.text"
        type="email"
        class="form-control"
        id="exampleInputEmail1"
        aria-describedby="emailHelp"
      />
      <div v-if=" enviar && !$v.user.text.required">campo requirido</div>
      <div v-if=" enviar && !$v.user.text.minLength">debes tener al menos 2 caracteres</div>
    </div>
    <div class="mb-3">
      <label for="exampleInputPassword1" class="form-label">Password</label>
      <input
        v-model="user.password"
        type="password"
        class="form-control"
        id="exampleInputPassword1"
      />
      <div v-if=" enviar && !$v.user.password.required">campo requirido</div>
      <div v-if=" enviar && !$v.user.password.minLength">debes tener mas de 6 caracteres

      </div>
    </div>
    <button type="submit" class="btn btn-primary">Submit</button>
  </form>
</template>

<script>
import { required, minLength } from "vuelidate/lib/validators";
export default {
  data() {
    return {
      enviar: false,
      user: {
        text: "",
        password: "",
      },
    };
  },
  validations: {
    user: {
      text: { required, minLength: minLength(2) },
      password: { required, minLength: minLength(6) },
    },
  },
  methods: {
    boton() {
      this.enviar = true;
      this.$v.touch
      if (this.$v.$invalid) {
        return false;
      }
      alert("validacion pasada");
    },
  },
};
</script>

<style>
</style>