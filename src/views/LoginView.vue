<template>
  <form>
    <h1>Login</h1>
    <div id="login" class="from-group mb-2">
        <input type="text" class="form-control" name="username" v-model="input.username" placeholder="Username" />
    </div>
    <div class="from-group mb-2">
      <input type="password" class="form-control" name="password" v-model="input.password" placeholder="Password" />
    </div>
    <button type="button" class="btn btn-primary btn-success" v-on:click="login()">Login</button>
  </form>

</template>

<script>
    export default {
        name: 'Login',
        data() {
            return {
                input: {
                    username: "",
                    password: ""
                }
            }
        },
        methods: {
            login() {
                if(this.input.username != "" && this.input.password != "") {
                    if(this.input.username == this.$parent.mockAccount.username && this.input.password == this.$parent.mockAccount.password) {
                        this.$emit("authenticated", true);
                        this.$router.replace({ name: "secure" });
                    } else {
                        console.log("The username and / or password is incorrect");
                    }
                } else {
                    console.log("A username and password must be present");
                }
            }
        }
    }
</script>
