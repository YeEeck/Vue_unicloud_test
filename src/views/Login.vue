<template>
  <div class="container">
    <input
      type="text"
      v-model="username"
      class="username_input"
      placeholder="用户名"
    /><br /><br />
    <input
      type="password"
      v-model="password"
      class="username_input"
      placeholder="密码"
    /><br /><br />
    <button @click="login">登录</button><br /><br />
    <span v-bind:class="tipClass">{{ res }}</span>
  </div>
</template>

<script>
import { PostTest } from "../network/login";

export default {
  data() {
    return {
      username: "",
      password: "",
      res: "waiting...",
      tipClass: "normal_tip",
    };
  },
  methods: {
    login() {
      this.res = "waiting...";
      this.tipClass = "normal_tip";
      PostTest({ username: this.username, password: this.password }).then(
        (res) => {
          if (res.data.status == "true") {
            this.res = "登录成功";
            this.tipClass = "right_tip";
          } else {
            this.res = "用户名或密码错误";
            this.tipClass = "error_tip";
          }
        }
      );
    },
  },
};
</script>

<style>
.username_input {
  width: fit-content;
}

.container {
  margin-top: 1em;
}

.error_tip {
  color: red;
  font-weight: bold;
}

.right_tip {
  color: #42b983;
  font-weight: bold;
}
</style>