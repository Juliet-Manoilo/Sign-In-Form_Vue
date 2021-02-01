<template>
  <section class="SignIn">
    <div class="SignIn__left-block">
      <div class="SignIn__container">
  <splide :options="options" style="max-width: 90%;">
    
  <splide-slide>
    <div class="SignIn__Slide">
    <img src="../assets/slide1.png" class="SignIn__slide-img" alt="slide">
    <h2 class="SignIn__title-slide">Tokenplace</h2>
    <p class="SignIn__subtitle">Multi-exchange Trading Terminal</p></div>
  </splide-slide>
  <splide-slide >
    <div class="SignIn__Slide">
    <img src="../assets/slide2.png" class="SignIn__slide-img" alt="slide">
    <h2 class="SignIn__title-slide">Fund Platform</h2>
    <p class="SignIn__subtitle">Hedge funds wealth management</p></div>
  </splide-slide>
  <splide-slide>
    <div class="SignIn__Slide">
    <img src="../assets/slide3.png" class="SignIn__slide-img" alt="slide">
    <h2 class="SignIn__title-slide">Noviscient</h2>
    <p class="SignIn__subtitle">Management Platform</p></div>
  </splide-slide>
</splide>
    </div></div>
    <div class="SignIn__right-block"></div>
    <a href="/" class="SignIn__logo-link"><img src="../assets/logo.png" alt="logo" class="SignIn__logo-img"></a>
    <div class="SignIn__form-wrapper">
      <h1 class="SignIn__title">Sign in</h1>
      <p class="SignIn__sign-up">Don’t have an account? <a target="_blank" href="#" class="SignIn__sign-up-link">Sign up now</a></p>
    <form action="#" method="POST" class="SignIn__form" @submit.prevent="login">
       <label for="Email" class="SignIn__email-label">Email</label>
       <p class="SignIn__error-email">Invalid Email</p>
      <input
                required
                v-model="email" 
                type="email"
                class="SignIn__input-email"
                name="Email"
                id="Email"
                minlength="3"
                pattern="[a-z0-9._%+-]+@[a-z0-9.-]+\.[a-z]{2,4}"
              />
              <label for="Password" class="SignIn__password-label">Password</label><p class="SignIn__error-password">Invalid Email</p>
     <input required v-model="password" type="password" name="Password" id="password" minlength="3" class="SignIn__input-password"/>
     <span class="SignIn__password-placeholder"><a href="#" class="SignIn__forgot-password">Forgot your password?</a> </span>
    <input type="submit" value="Sign in" :disabled="isDisabled" class="SignIn__btn"/>
    </form></div>
    <div class="SignIn__Links">
      <a href="#" class="SignIn__link">Contact</a><a href="" class="SignIn__link">Privacy</a>
      <a href="" class="SignIn__link">Terms</a>
    </div>
  </section>
</template>

<script>

import { Splide, SplideSlide } from '@splidejs/vue-splide';
import '@splidejs/splide/dist/css/themes/splide-default.min.css';
export default {
  components: { Splide, SplideSlide  },
  name: 'SignIn',
  data() {
		return {
			options: {
      type: 'loop',
			rewind : true,
			width  : '100%',
      perPage: 1,
      arrows: false,
      height: 500,  
},
    data: {
    login: "",
    password:"" 
  },
  computed: {
    isDisabled() {
      if (this.email.length !== 0 && this.password.length !== 0) {
        return false;
      } else {
        return true;
      }
    }
  },
  methods: {
      login: function () {
        let email = this.email 
        let password = this.password
        this.$store.dispatch('login', { email, password })
       .then(() => this.$router.push('/'))
       .catch(err => console.log(err))
      }
    }
    };
    
	},
  }
</script>


<style scoped lang="scss">
@import "../styles/style.scss";

.SignIn {
  min-height: 900px;
  z-index: 10;
  font-family: $main-font;
  position: relative;
  &__left-block {
    max-width: 45%;
    margin: 20px;
    background-color: $blue;
    background-image: url("../assets/background-slider.png");
    display: inline-block;
    color: $white;
    border-radius: 15px;
    min-height: 80vh;
    background-size: cover;
    text-align: center;
    
    
  }
  &__right-block {
    min-width: 39%;
    display: inline-block;
    position: absolute;
    left: 53%;
    top: 0;
    display: flex;
    flex-direction: column;
  }
 &__slide-img {
   margin-bottom: 50px;
   position: relative;
  box-shadow: 0px 10px 50px rgba(0,0,0,0.30), 0 10px 12px rgba(0,0,0,0.22);
 }
 &__title-slide {
   margin-bottom: 30px;
   letter-spacing: 1px;
 }
 &__subtitle {
   letter-spacing: 1px;
 }
&__logo-link {
  width: 15%;
  position: absolute;
  top: 5%;
  left: 52%;
}
&__logo-img {
  width: 100%;
}
&__container {
  padding-top: 20%;
}
&__form-wrapper {
  position: absolute;
  left: 52%;
  top: 20%;
}
&__title {
  margin-bottom: 30px;
}
&__sign-up-link {
  color: $blue;
  margin-bottom: 50px;
  &:hover {
    color: $blue-hover;
  }
}
&__input-email {
  width: 420px;
  height: 50px;
  border: 1px solid $light-grey;
  border-radius: 8px;
  margin-bottom: 30px;
  outline:none;
  &:hover {
    border: 1px solid $blue;
  }
  &:focus {
     border: 1px solid $blue;
  }
  &:invalid .SignIn__error-email {
  visibility: visible;
  }
  &:valid {
    border: 1px solid $green;
  }
  &:invalid {
    border: 1px solid $red;
  }

}
&__email-label {
  margin-bottom: 15px;
  display: inline-block;
  margin-right: 250px;
}
&__password-label {
  margin-bottom: 15px;
  display: inline-block;
  margin-right: 222px;
}
&__input-password {
 width: 420px;
  height: 50px;
  border: 1px solid $light-grey;
  border-radius: 8px;
  margin-bottom: 30px;
  outline:none;
  &:hover {
    border: 1px solid $blue;
  }
  &:focus {
     border: 1px solid $blue;
  }
  &:invalid {
    border: 1px solid $red;
  }
  &:valid {
    border: 1px solid $green;
  
}}
&__password-placeholder {
  color: $grey-text;
  font-size: $text-size;
  position: absolute;
  top: 72%;
  right: 5%;
}
&__btn {
  outline: none;
  width: 420px;
  height: 52px;
  border-radius: 8px;
  background-color: $blue;
  color: $white;
  border: none;
  font-size: $btn-size;
  cursor: pointer;
  font-weight: 600;
  box-shadow: 0px 20px 30px rgba(0, 60, 255, 0.301);
  &:disabled{
  background-color: $grey-btn;
}
&:hover {
  background-color: $blue-btn-hover;
}}
&__error-email {
  color: $red;
  font-size: $error-size;
  font-weight: 400;
  display: inline-block;
  visibility: hidden;
}
&__error-password {
  color: $red;
  font-size: $error-size;
  font-weight: 400;
  display: inline-block;
  visibility: hidden;
}
&__Links {
  position: absolute;
  bottom: 15%;
  left: 52%;
}
&__link {
  margin-right: 20px;
  color: $grey-text;
  font-weight: 600;
  &:last-child {
    margin-right: 0;
  }
  &:hover {
    color: $black;
  }
}
}
.SignIn__input-email:invalid .SignIn__error-email {
  visibility: visible;
}



</style>
