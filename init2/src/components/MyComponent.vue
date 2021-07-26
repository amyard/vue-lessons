<template>
  <div class="root">
    Hello - {{text}}
    <hr>
    Email - {{email}} / Password - {{password}}
    <hr>
    <label>
      Enter email:
      <input 
          type="email" 
          v-bind:value="email"
          v-on:input="emailInput"
      >
    </label>
    <label>
      Enter  password:
      <input 
          type="password" 
          :value="password"
          @input="passwordInput($event.target.value)"
      >
    </label>

    <hr>
    <p>
      Выберите кол-во продуктов:
    </p>
    <button
        type="button"
        @click="decreaseCount"
    >
      -
    </button>
    <input
        type="number"
        :value="count"
        :min="minCount"
        :max="maxCount"
    >
    <button
        type="button"
        @click="increaseCount"
    >
      +
    </button>


  </div>
</template>

<script>
export default {
  name: "MyComponent",
  data() {
    return {
      text: "text here will be",
      email: "aasd@asdf.com",
      password: "password",
      
      count: 1,
      maxCount: 10,
      minCount: 1

    }
  },
  methods: {
    emailInput(event) {
      this.email = event.target.value;
    },
    passwordInput(value) {
      this.password = value;
    },
    increaseCount() {
      if (this.count < this.maxCount) {
        this.count++
      }
    },
    decreaseCount() {
      if (this.count > this.minCount) {
        this.count--
      }
    }

  }
}
</script>

<style scoped>

</style>