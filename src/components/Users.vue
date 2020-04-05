<template>
  <div id="body">
    <b-button @click="fetchUsers">Fetch users!</b-button>
    <b-modal v-model="modalShow" size="sm" centered hide-footer no-close-on-backdrop no-close-on-esc hide-header>
      <img alt="Vue logo" src="../assets/logo.png">
    </b-modal>
    <div id="userList">
      <ul>
        <li v-for="user in users" :key="user.id">
          {{ user.name }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
  export default {
    name: "Users",
    data() {
      return {
        users: [],
        modalShow: false
      }
    },
    methods: {
      fetchUsers: function () {
        this.users = []
        this.modalShow = true
        const baseURI = 'https://jsonplaceholder.typicode.com/users'
        this.$axios.get(baseURI)
        .then((result) => {
          this.users = result.data
          this.modalShow = false
        })
      }
    }
  }
</script>

<style>
#userList {
  display: flex;
  justify-content: center;
  text-align: left;
}
</style>

