<template>
  <div
    class="login"
    :class="{ login__signin: isSignIn, login__signup: isSignUp }"
  >
    <login-tabs @click.native="switchState" />
    <login-form />
  </div>
</template>
<script>
import { ref, computed } from "@vue/composition-api";
import LoginTabs from "../components/LoginTabs";
import LoginForm from "../components/LoginForm";
export default {
  name: "login",
  components: {
    LoginTabs,
    LoginForm
  },
  setup() {
    const state = ref(2);
    console.log(state.value);

    const isSignIn = computed(() => state.value === 1);
    console.log(isSignIn.value);

    const isSignUp = computed(() => state.value === 2);
    console.log(isSignUp.value);

    const switchState = () => (state.value = state.value === 1 ? 2 : 1);
    console.log(switchState());
    return {
      state,
      isSignIn,
      isSignUp,
      switchState
    };
  }
};
</script>
<style lang="scss" scoped>
.login {
  width: 100%;
  color: white;
  font-size: 14px;
}
</style>
