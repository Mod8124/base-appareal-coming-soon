<template>
    <section class="cta">
        <div id="cta">
            <div class="logoLg">
                <div id="logoLg">
                    <slot name="logoLg"></slot>
                </div>
            </div>
            <h1><slot name="title"></slot></h1>
            <p> <slot name="info"></slot></p>
            <form @submit.prevent="checkForm" novalidate="true">
                  <input type="email" placeholder="Email Address"  v-model="email" :class="showError? 'active':''">
                <button type="submit"><img src="../assets/images/icon-arrow.svg" alt="svg"></button>
     <p v-if="showError" id="message">
    <ul>
      <p  class="error">{{ errors }}</p>
    </ul>
  </p>     </form>
        </div>
    </section>
</template>

<script>
export default {
    data() {
        return {
            errors: "Please a provide a valid email",
            email: null,
            active:false,
            showError:false
        }
    },
    methods: {
          checkForm: function () {

          if(!this.validEmail(this.email)) {
            this.showError= true
          }
    },
    validEmail: function (email) {
      var re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      return re.test(email);
    }
  }
  }


</script>

<style scoped>
.active {
    background-image: url('../assets/images/icon-error.svg');
    background-repeat: no-repeat;
    background-position: 90%;
    outline: 1px solid hsl(0, 93%, 68%);

}
</style>
