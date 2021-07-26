<template>
  <div class="user-card">
    <h1>I'm going to learn you how to earn 1000$ by hour</h1>
    <div class="main-information">
      <img src="../assets/images/коуч.jpg" alt="" width="500px">
      <div class="info">
        <h2>{{getFullName}}</h2>
        <strong>Business-couch</strong>
        <ul>
          <li>some text here line 1</li>
          <li>some text here line 2</li>
          <li>some text here line 3</li>
        </ul>
      </div>
    </div>
    
    <p>Students: {{users.length}}</p>
    <ul>
      <li 
          v-for="(user, index) in users"
          :key="index"
      >
        {{ `${index} ${getFullNameMethod(user)}` }}
      </li>
    </ul>
    
    <button type="button" @click="currentPage++">Prev</button>
    <button
        type="button"
        v-for="page in pages"
        :key="page"  
        @click="currentPage = page"
    >
      {{page}}
    </button>
    <button type="button" @click="currentPage--">Next</button>
    <p>Page {{currentPage}} of {{pages}}</p>
  </div>
</template>

<script>
export default {
  name: "UserCard",
  data() {
    return {
      firstName: "Max",
      secondName: "God",
      lastName: "Awesome",
      users: [
        {
          firstName: "lol_1",
          secondName: "lal_1",
          lastName: "lul_1",
        },
        {
          firstName: "lol_2",
          secondName: "lal_2",
          lastName: "lul_2",
        },
        {
          firstName: "lol_3",
          secondName: "lal_3",
          lastName: "lul_3",
        }  
      ],
      pages: 3,
      currentPage: 1
    }
  },
  computed: {
    getFullName() {
      // const whiteSpace = " ";
      // return this.firstName.toUpperCase() + whiteSpace + this.secondName.toUpperCase() + whiteSpace + this.lastName.toUpperCase();
      return `${this.firstName} ${this.secondName} ${this.lastName}`.toUpperCase();
    }
  },
  methods: {
    getFullNameMethod(user) {
      return `${user.firstName} ${user.secondName} ${user.lastName}`;
    },
    loadUsers(page) {
      console.log(`Loading of users for page ${page}`)
    }
  },
  watch: {
    currentPage(newValue, oldValue) {
      console.log(newValue, oldValue);
      this.loadUsers(newValue);
    }
  }
}
</script>

<style land="scss" scoped>
  .user-card {
    margin-top: 40px;
  }
  .main-information {
    display: flex;
  }
  .info {
    margin-left: 50px;
  }
  h2 {
    margin-bottom: 14px;
  }
</style>