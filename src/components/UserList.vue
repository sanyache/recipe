<template>
    <div v-if="users.length" class="userlist">
        <h2>Users</h2>
        <div v-for="user in users" :key=user.id class="userCard" :id="user.id">
            <ul>
                <li>{{ user.name }}</li>
                <li>{{ user.email }}</li>
                <li>{{ user.phone }}</li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
  data() {
    return {
      users: [],
    }
  },
  mounted() {
    this.getUsers()
  },
  methods: {
      async getUsers(){
        try {
          const response = await this.axios.get('https://jsonplaceholder.typicode.com/users')
          this.users.push(...response.data)
        } catch(error) {
            console.log(error)
        } 
         
      }
  }
}
</script>
<style scoped>
  .userlist {
    margin-top: 20px; 
    display: flex;
    flex-direction: column;
    align-items: center; 
  }
  .userlist ul {
    list-style: none;
    margin: 10px;
  }
  .userCard {
    display: flex;  
    justify-content: left;
    width: 300px;
    background: cornflowerblue;
    margin: 10px 0;
  }
  h2 {
    text-align: center;  
  }
</style>

