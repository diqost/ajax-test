<template>
  <div id="app">
    <user-card v-for="user in users" :user="user" :key="user.email"></user-card>
  </div>
</template>

<script>
import UserCard from './components/UserCard'
export default {
  data(){
    return {
      users: []
    }
  },
  name: 'app',
  components: {
    UserCard
  },
  mounted(){
    this.axios.get('https://randomuser.me/api?results=50').then((response)=>{
      console.log('response', response.data)
      this.users = response.data.results
    }).catch(err=>{
      console.log('errr', err)
    })

  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
