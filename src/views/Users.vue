<template>
  <div class="quiz">
    <!-- <img alt="Vue logo" src="../assets/logo.png"> -->
    
    <h2>Users</h2>

    <div class="info">
      <!-- <pre>{{ users }}</pre> -->
      <ul class="users">
          <li v-for="(u,i) in users" :key="i">
              <img :src="u.picture.thumbnail" :alt="u.name.first + ' ' +u.name.last">
              <div>
                <p>{{u.name.first + ' ' +u.name.last}}</p>
                <a href="#">{{u.email}}</a>
                </div>
          </li>
      </ul>
    </div>

    <div class="addMore" @click="addMoreUsers()">Add More!</div>

  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios';
export default {
  name: 'Users',
  data(){
    return {
        numUsers: 2,
        users:[],
    }
  },
  methods: {
    addMoreUsers(){
      this.numUsers = this.numUsers += 2;
      axios.get('https://randomuser.me/api/?results='+this.numUsers).then(response => {
          this.users = response.data.results;
          localStorage.setItem('users',this.users);
      })
    }
  },
  mounted(){
    this.ls = localStorage.getItem('users');
    if(this.ls === ''){
        alert('vazio');
    } 
    if(this.ls !== ''){
        axios.get('https://randomuser.me/api/?results='+this.numUsers).then(response => {
            this.users = response.data.results;
            localStorage.setItem('users',this.users);
        })
    }
    
  },
  components: {
    // HelloWorld
  }
}
</script>

<style>
pre {
    text-align: left;
}
.users {
    width:420px;
    max-width:420px;
}
.users li {
    max-width: 420px;
    width: 100%;
    display: flex;
    flex-wrap: wrap;
    box-shadow: 0px 3px 7px 2px rgb(0 0 0 / 20%);
    border-radius: 10px;
    margin-bottom: 30px;
    padding: 20px;
}
.users img {
    border-radius: 50%;
    width:50px;
    height:50px;
}
.users p {
    width: 100%;
    float: left;
    padding: 0;
    margin: 0;
}
.users li > div {
    display: flex;
    justify-content: flex-start;
    flex-direction: column;
    align-items: flex-start;
    width: calc(100% - 50px);
    text-align: left;
    padding-left:15px;
}
.users a {
    width: 100%;
    float: left;
}
</style>