<template src="./html/Home.html">
</template>

<script>
import { required, email, minLength } from "vuelidate/lib/validators";
export default {
  data() {
    return {
      users: {
        nombre: "",
        apellido: "",
        email: "",
        password: "",
        confirmpassword: "",
      },
      enviar: false,
    };
  },
  validations: {
    users: {
      nombre: { required },
      apellido: { required },
      email: { required, email },
      password: { required, minLength: minLength(6) },
      confirmpassword: { required, minLength: minLength(6) },
    },
  },
  methods: {
    boton() {
      var contra = this.users.password;
      var Comfirmcontra = this.users.confirmpassword;
      this.enviar = true;
      if (this.$v.$invalid) {
        return console.error("complete los campos requiridos");
      }
      if (contra == Comfirmcontra) {
        this.$router.push("/about");
      } else {
        alert("Password incorret");
      }
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.color {
  color: red;
}

.seccion {
  width: 400px;
  background: rgb(73, 67, 58);
  padding: 30px;
  margin: auto;
  margin-top: 100px;
  border-radius: 4px;
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
  color: white;
  box-shadow: 7px 13px 37px #000;
}
.seccion h4 {
  font-size: 25px;
  margin-bottom: 20px;
  text-align: center;
}

.control {
  width: 100%;
  background: #24303c;
  padding: 10px;
  border-radius: 4px;
  margin-bottom: 12px;
  border: 1px solid #1f53c5;
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
  font-size: 18px;
  color: white;
}

.seccion p {
  height: 40px;
  text-align: center;
  font-size: 18;
  line-height: 40px;
}
.seccion a {
  color: white;
  text-decoration: none;
}
.seccion a:hover {
  color: white;
  text-decoration: underline;
}

.seccion .boton {
  width: 100%;
  background: #1f53c5;
  border: none;
  padding: 12px;
  color: white;
  margin: 16px 0;
  font-size: 16px;
}
</style>