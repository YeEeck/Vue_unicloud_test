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
    <a-button type="primary" @click="login">登录</a-button><br /><br />
    <img v-if="loadingS" src="../assets/loading.gif" class="load_img" />
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
      res: "",
      tipClass: "normal_tip",
      loadingS: false,
    };
  },
  methods: {
    login() {
      this.res = "";
      this.tipClass = "normal_tip";
      this.loadingS = true;
      PostTest({ username: this.username, password: this.password }).then(
        (res) => {
          if (res.data.status == "true") {
            this.res = "登录成功";
            this.tipClass = "right_tip";
            this.loadingS = false;
          } else {
            this.res = "用户名或密码错误";
            this.tipClass = "error_tip";
            this.loadingS = false;
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

input {
  outline: none;
  border-width: 1px;
  border-radius: 10px;
  padding-left: 1em;
}

.load_img {
}
</style>