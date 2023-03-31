<template>
  <v-row style="margin: 0;">
    <v-main class="justify-center align-center">
      <form @submit.prevent>
        <svg class="logo" width="48" height="36" viewBox="0 0 48 36" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path
            d="M19.0035 11.7837L15.2315 7.95898C12.6876 10.5273 11.1111 14.0804 11.1111 18.0006C11.1111 21.9212 12.6907 25.466 15.2315 28.0462L19.0035 24.2163C18.0471 23.2446 17.3095 22.0453 16.8793 20.7084H31.122C30.6918 22.0453 29.9542 23.2446 28.9947 24.2163L32.7698 28.0462C35.3156 25.466 36.8867 21.9212 36.8867 18.0006C36.8867 14.0804 35.3156 10.5273 32.7698 7.95898L28.9947 11.7837C29.9542 12.755 30.6918 13.9567 31.122 15.2931H16.8793C17.3095 13.9567 18.0471 12.755 19.0035 11.7837Z"
            fill="#101828"/>
          <path
            d="M36.8477 3.82626C40.4372 7.45826 42.6538 12.4719 42.6538 18.0006C42.6538 23.5293 40.4372 28.5449 36.8477 32.167L40.622 36C45.1813 31.386 48 25.0204 48 18.0006C48 10.9796 45.1813 4.61522 40.622 0L36.8477 3.82626ZM11.1492 3.82626L7.37447 0C2.82185 4.61522 0 10.9796 0 18.0006C0 25.0204 2.82185 31.386 7.37447 36L11.1559 32.1737C7.5663 28.5449 5.34617 23.5293 5.34617 18.0006C5.34617 12.4735 7.5663 7.45826 11.1492 3.82626Z"
            fill="#101828"/>
        </svg>
        <h1>Log in to your account</h1>
        <div class="input-item">
          <span>Email</span>
          <input v-model="email" :class="{'error-wrap' : emailError}" autofocus minlength="5"
                 placeholder="name@hoteldomain.com" required type="email">
          <span v-if="emailError" class="error-text">
            Please check email address
          </span>
        </div>
        <div class="input-item">
          <span>Password</span>
          <input v-model="password" :class="{'error-wrap' : passwordError}" minlength="8" placeholder="••••••••" required
                 type="password">
          <span v-if="passwordError" class="error-text">
            Please fill in your password
          </span>
        </div>
        <v-row align-content="center" justify="space-between" class="checkbox-label">
          <div class="checkbox" @click="checkbox = !checkbox">
            <div :class="{'checkbox-wrap-active' : checkbox}" class="checkbox-wrap">
              <svg v-if="checkbox" fill="none" height="12" viewBox="0 0 12 12" width="12"
                   xmlns="http://www.w3.org/2000/svg">
                <path d="M10 3L4.5 8.5L2 6" stroke="#7F56D9" stroke-linecap="round" stroke-linejoin="round"
                      stroke-width="1.6666"/>
              </svg>
            </div>
            <span>Remember me</span>
          </div>
          <nuxt-link to="/" exact no-prefetch>
            Forgot password
          </nuxt-link>
        </v-row>
        <button type="submit" @click="fieldsCheck()">Sign in</button>
        <p class="text-support">
          Can’t log in to your account?
          <nuxt-link to="/" no-prefetch exact>
            Ask support
          </nuxt-link>
        </p>
      </form>
    </v-main>
    <img src="~/assets/img/section.webp" alt="Background image">
  </v-row>
</template>

<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      email: '',
      password: '',
      checkbox: false,

      emailError: false,
      passwordError: false,
    }
  },
  methods: {
    fieldsCheck(){
      this.emailError = this.email.length < 5;
      this.passwordError = this.password.length < 8;
    },
  }
}
</script>

<style scoped lang="scss">

img {
  width: 50%;
  height: 100vh;
  object-fit: cover;

  @media screen and (max-width: 768px){
    display: none;
  }
}

h1 {
  @include style-font(30, 600, 127%);
  margin: rem(24) 0 rem(32);
  color: rgba(16, 24, 40, 1);
}

form {
  width: rem(360);
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;

  .logo {
    width: rem(48);
    height: rem(36);
  }
}

.input-item {
  margin-bottom: rem(20);
  display: flex;
  flex-direction: column;
  gap: rem(6);
  width: 100%;

  &:last-child {
    margin-bottom: rem(24);
  }

  input {
    width: 100%;
    padding: rem(10) rem(14);
    background: #FFFFFF;
    border: 1px solid rgba(208, 213, 221, 1);
    box-shadow: 0 1px 2px rgba(16, 24, 40, 0.05);
    border-radius: 8px;
    @include style-font(16, 400, 150%);
    color: rgba(16, 24, 40, 1);
    transition: .2s;

    &::placeholder {
      color: rgba(152, 162, 179, 1);
    }
  }

  span {
    color: rgba(52, 64, 84, 1);
    @include style-font()
  }

  .error-text {
    color: rgba(240, 68, 56, 1);
    @include style-font(14, 400);
  }

  .error-wrap {
    border-color: rgba(253, 162, 155, 1);
  }
}

.checkbox {
  display: flex;
  align-items: center;
  cursor: pointer;

  span {
    color: rgba(52, 64, 84, 1);
    @include style-font(14);
    margin-left: rem(8);
  }

  &-wrap {
    width: rem(16);
    height: rem(16);
    border: 1px solid rgba(208, 213, 221, 1);
    border-radius: 4px;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: .2s;

    svg {
      width: rem(12);
      height: rem(12);
    }
  }

  &-wrap-active {
    border-color: rgba(127, 86, 217, 1);
  }
}

.checkbox-label {
  width: 100%;
  margin: rem(24) 0;

  a {
    color: rgba(105, 65, 198, 1);
    @include style-font(14, 600);
  }
}

button {
  width: 100%;
  text-align: center;
  color: #FFFFFF;
  padding: rem(10) 0;
  background: rgba(127, 86, 217, 1);
  border-radius: 8px;
  border: 1px solid rgba(127, 86, 217, 1);
  margin-bottom: rem(32);
}

.text-support {
  color: rgba(71, 84, 103, 1);
  @include style-font(14, 400);

  a {
    color: rgba(105, 65, 198, 1);
    @include style-font(14, 600);
  }
}

</style>
