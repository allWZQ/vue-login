<template>
  <span class="login_checkbox">
    <input :id="id" type="checkbox" />
    <label :for="id">{{ label }}</label>
  </span>
</template>
<script>
import { ref } from "@vue/composition-api";
let GID = 1;
export default {
  props: {
    label: {
      type: String
    }
  },
  setup() {
    const id = ref(`login-checkbox-${GID++}`);
    return {
      id
    };
  }
};
</script>
<style lang="scss" scoped>
.login_checkbox input {
  display: none;
}
.login_checkbox label::before,
.login_checkbox label::after {
  content: "";
  display: inline-block;
  margin-right: 5px;
  margin-top: 4px;
  width: 14px;
  height: 14px;
  //垂直对齐
  vertical-align: top;
}
.login_checkbox label::before {
  border-radius: 3px;
  background-color: white;
  box-shadow: 0px 1px 1px #0066d0;
}
//打勾图标
.login_checkbox label::after {
  content: "\f00c";
  position: relative;
  display: none;
  z-index: 10;
  margin-right: -14px;
  width: 12px;
  height: 12px;
  padding: 1px;
  font: normal normal normal 12px/1 FontAwesome;
  color: #007dff;
  float: left;
}
.login_checkbox input:checked + label::after {
  display: inline-block;
}
</style>
