<template>
  <div id="app">
<!--    <my-component />-->
<!--    <hr>-->
<!--    <user-card />-->
<!--    <hr>-->
<!--    <user-search />-->
    <photo-redactor />
  </div>
</template>

<script>

// import MyComponent from "./components/MyComponent";
// import UserCard from "./components/UserCard";
// import UserSearch from "./components/UserSearch";
import PhotoRedactor from "./components/PhotoRedactor";

export default {
  name: 'App',
  components: {
    // MyComponent,
    // UserCard,
    // UserSearch,
    PhotoRedactor
  }
}
</script>
