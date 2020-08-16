<template>
  <div class="card">
    <avatar circle size="sm" :img="userData.avatar_url"/>
    <user :perfil="perfilUsuario"/>
    <!-- <div class="repositorios">
      <ul id="listRepos" v-if="userRepositories.length > 0">
      <h4>Repositórios</h4>
      <small>Total de repositórios: {{userRepositories.length}}</small>
      <hr>
        <li v-for="repository in userRepositories" :key="repository.id">{{repository.name}}</li>
      </ul>
    </div> -->
      <ul id="myList" v-if="userRepositories.length > 0">
      <h4>Repositórios</h4>
      <small>Total: {{userRepositories.length}}</small>
      <hr>
        <li v-for="repository in userRepositories" :key="repository.id">{{repository.name}}</li>
      </ul>
  </div>
</template>

<script>
import Axios from 'axios';
import Avatar from "./Avatar";
import User from "./User";
export default {
  components: { Avatar, User },
  name: "",
  props: {
    userName: String
  },
  data: () => ({
    userData: "",
    userRepositories: []
  }),
  computed: {
    perfilUsuario () {
      return {
        name: this.userData.name,
        bio: this.userData.bio,
        location: this.userData.location,
        blog: this.userData.blog
      };
    }
  },
  methods: {
    getUser(name) {
      fetch(`https://api.github.com/users/${name}`, {
        headers: {
          Accept: "application/json",
          "Content-Type": "application/json"
        },
        method: "GET"
      })
        .then(response => response.json().then(x => (this.userData = x)))
        .catch(error => console.log(error));
    },
    getRepos(name) {
      fetch(`https://api.github.com/users/${name}/repos`, {
        headers: {
          Accept: "application/json",
          "Content-Type": "application/json"
        },
        method: "GET"
      })
        .then(response => response.json().then(x => (this.userRepositories = x)))
        .catch(error => console.log(error));
    },
    // getUser(name) {
    //   Axios.get(`https://api.github.com/users/${name}`, {
    //     headers: {
    //       Accept: "application/json",
    //       "Content-Type": "application/json"
    //     },
    //   })
    //     .then(response => response.json().then(x => (this.userData = x)))
    //   .catch(error => console.log(error))
    // },

    // getRepos(name) {
    //   Axios.get(`https://api.github.com/users/${name}/repos`, {
    //     headers: {
    //       Accept: "application/json",
    //       "Content-Type": "application/json"
    //     },
    //   })
    //   .then(response => response.json().then(x => (this.userRepositories = x)))
    //   .catch(error => console.log(error))
    // },
  },

  watch: {
    userName(context) {
      this.getUser(context);
      this.getRepos(context);
    }
  }
};
</script>

<style>
  .repositorios {
    display: flex;
    justify-content: flex-start;
    align-self: flex-start;
    flex-direction: column;
    width: 92%;
  }

  .repositorios h4 {
    text-align: center;
  }

  .card {
    max-width: 70ch;
    margin-top: 40px;
    display: flex;
    flex-direction: column;
    align-items: center;
    background: #fff;
    flex-wrap: wrap;
    border-radius: 5px;
    background-size: cover;
    background-position: center center;
    box-shadow: 30px 30px 30px -5px rgba(0, 0, 0, 0.3);
    transition: box-shadow 0.5s;
    will-change: transform;
    border: 15px solid white;
  }

  .card:hover {
    box-shadow: 30px 30px 30px 35px rgba(0, 0, 0, 0.3);
  }

  ul > h4 {
    margin-bottom: 2px;
  }

  #listRepos {
    position: absolute;
    width: 80vw; 
  }
  #listRepos li {
    visibility: hidden;
    -webkit-animation: fadeIn 2s ease-in-out;
    -moz-animation: fadeIn 2s ease-in-out;
    -o-animation: fadeIn 2s ease-in-out;
    animation: fadeIn 2s ease-in-out;
  }
  #listRepos li:nth-child(2n) {
    background-color: #444;
    color: #2de;
    padding: 6px 0;
    list-style: none;
  }

  #listRepos li:nth-child(2n+1) {
    background-color: #333;
    color:white;
    padding: 6px 0;
    list-style: none;
  }

  @-webkit-keyframes fadeIn {
  0% { opacity: 0; }
  100% { opacity: 1; } 
  }
  @-moz-keyframes fadeIn {
  0% { opacity: 0;}
  100% { opacity: 1; }
  }
  @-o-keyframes fadeIn {
  0% { opacity: 0; }
  100% { opacity: 1; }
  }
  @keyframes fadeIn {
  0% { opacity: 0; }
  100% { opacity: 1; }
  }
</style>
