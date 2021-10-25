<template>
    <div class="cta">
        <div id="cta">
            <div class="logoLg">
                <div id="logoLg">
                    <slot name="logoLg"></slot>
                </div>
            </div>
            <h1><slot name="title"></slot></h1>
            <p> <slot name="info"></slot></p>
            <form @submit="checkForm" novalidate="true">
                  <input type="email" placeholder="Email Address"  v-model="email" :class="{active}">
                <button type="submit"><img src="../assets/images/icon-arrow.svg" alt="svg"></button>
     <p v-if="errors.length" id="message">
    <ul>
      <p v-for="error in errors" :key="error.id" class="error">{{ error }}</p>
    </ul>
  </p>     </form>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            errors: [],
            email: null,
            active:false
        }
    },
    methods: {
              checkForm: function (e) {
      this.errors = [];

      if (!this.email) {
        this.errors.push('Please provide a valid email');
        this.active = true;
      } else if (!this.validEmail(this.email)) {
        this.errors.push('Please provide a valid email');
      }

      if (!this.errors.length) {
        return true;
      }

      e.preventDefault();
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
    background-position: 196px;
}
</style>
