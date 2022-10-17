<template>
  <div>
    <div class="card" v-if="loading === false">
      <avatar circle size="sm" :img="userData.avatar_url" />
      <user :perfil="perfilUsuario" />
      <div class="repositorios">
        <ul id="myList" v-if="userRepositories.length > 0">
          <h4>Repositórios</h4>
          <small>Total: {{ userRepositories.length }}</small>
          <hr />
          <li v-for="repository in userRepositories" :key="repository.id">
            {{ repository.name }}
          </li>
        </ul>
      </div>
    </div>
    <div
      v-if="loading"
      style="margin-top: 40px; align-items: center; justify-content: center"
    >
      <cube-spin v-if="loading" />
    </div>
  </div>
</template>

<script>
import Avatar from './Avatar'
import User from './User'
import CubeSpin from 'vue-loading-spinner/src/components/RotateSquare2'
export default {
  components: { Avatar, User, CubeSpin },
  name: '',
  props: {
    userName: String,
  },
  data: () => ({
    userData: '',
    userRepositories: [],
    loading: false,
  }),
  computed: {
    perfilUsuario() {
      return {
        name: this.userData.name,
        bio: this.userData.bio,
        location: this.userData.location,
        blog: this.userData.blog,
      }
    },
  },
  methods: {
    getUser(name) {
      this.loading = true
      fetch(`https://api.github.com/users/${name}`, {
        headers: {
          Accept: 'application/json',
          'Content-Type': 'application/json',
        },
        method: 'GET',
      })
        .then((response) => {
          response.json().then((x) => (this.userData = x))
          this.loading = false
        })
        .catch((error) => {
          console.log(error)
          this.loading = false
        })
    },
    getRepos(name) {
      fetch(`https://api.github.com/users/${name}/repos`, {
        headers: {
          Accept: 'application/json',
          'Content-Type': 'application/json',
        },
        method: 'GET',
      })
        .then((response) =>
          response.json().then((x) => (this.userRepositories = x))
        )
        .catch((error) => console.log(error))
    },
  },

  watch: {
    userName(context) {
      this.getUser(context)
      this.getRepos(context)
    },
  },
}
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
  margin-bottom: 40px;
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

#listRepos li:nth-child(2n + 1) {
  background-color: #333;
  color: white;
  padding: 6px 0;
  list-style: none;
}

@-webkit-keyframes fadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
@-moz-keyframes fadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
@-o-keyframes fadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
@keyframes fadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
</style>
