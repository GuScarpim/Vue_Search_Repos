<template functional>
  <header>
    <h3>Nome</h3>
     <span>{{props.perfil.name || 'Gustavo Scarpim'}}</span>
     <hr />
    <h3>Bio</h3>
    <span>{{props.perfil.bio || 'Dev. FrontEnd React, Vue, React Native, Next, Node'}}</span>
    <hr />
    <h3>Localização</h3>
    <span>{{props.perfil.location || 'São Paulo - SP'}}</span>
    <hr />
    <h3>Blog</h3>
     <a :href="[props.perfil.blog || 'https://gustavoscarpim.com/']"
        target="_blank" class="link">{{props.perfil.blog || 'guscarpim/Portfolio/'}}</a>
    <hr />
  </header>
</template>

<style scoped>
header {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background: #fff;
  flex-wrap: wrap;
  width: 80%;
  margin-top: 20px;
}

hr {
  width: 100%;
  margin-bottom: 10px;
}

h3 {
  margin: 5px 0 0 0 ;
}

span {
  font-weight: 500;
  font-family: "Courier New", Courier, monospace;
  font-size: 16px;
  text-align: center;
  margin-top: 5px;
}

.link {
  text-decoration: none;
  color: #000;
  font-weight: 500;
  font-family: "Courier New", Courier, monospace;
  font-size: 16px;
  text-align: center;
}

.link:hover {
  color: blue;
}

</style>
