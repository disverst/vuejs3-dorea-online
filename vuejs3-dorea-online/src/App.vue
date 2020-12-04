<template>
  <div id="app">
  @ {{ user.username }} - {{ fullName }}
    <stong>Followers:</stong> {{ followers }}
    <button v-on:click="followUser">
      Follow
    </button>
  </div>
</template>

<script>
export default {
  name: 'App',
  data () {
    return {
      followers: 0,
      user: {
        id: 1,
        username: 'SerhiiHorbachov',
        firstName: 'Serhii',
        lastName: 'Horbachov',
        email: 'serg@gmail.com',
        isAdmin: true
      }
    }
  },
  watch: {
    followers (newFollowerCount, oldFollowerCount) {
      if (oldFollowerCount < newFollowerCount) {
        console.log(`${this.user.username} has gained a follower`)
      }
    }
  },
  computed: {
    fullName () {
      return `${this.user.firstName} ${this.user.lastName}`
    }
  },
  methods: {
    followUser () {
      this.followers++
    }
  },
  mounted () {
    this.followUser()
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  line-height: 30px;

  display: flex;
  flex-direction: column;
}
</style>
