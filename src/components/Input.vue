<template>
  <!-- <label>
    <input type="text" @keyup="event => $emit('input', event.target.value)" placeholder="Nome do usuário do github">
    <span>Nome de usuário</span>
  </label> -->
 <section>
    <!-- <form @submit.prevent="event => $emit('input', event.target.value)"> -->
        <h1>Buscar Usuários e repositórios no Github</h1>
        <div class="input-container">
          <input type="text" @keyup="event => $emit('input', event.target.value)" placeholder="Nome do usuário do github">
          <!-- @keyup="event => $emit('input', event.target.value)"  -->
          <label class="label" for="name">Nome</label>
        </div>
        <!-- <button type="submit">Pesquisar</button> -->
    <!-- </form> -->
</section>
</template>

<script>
export default {
  name: 'InputDataComponent'
}
</script>

<style scoped>
/* Estrutura */
.input-container {
  position: relative;
}

input {
  border: 0;
  border-bottom: 2px solid #9e9e9e;
  outline: none;
  transition: .2s ease-in-out;
  box-sizing: border-box;
}

label {
  top: 0;
  left: 0; right: 0;
  color: #616161;
  display: flex;
  align-items: center;
  position: absolute;
  font-size: 1rem;
  cursor: text;
  transition: .2s ease-in-out;
  box-sizing: border-box;
}

input,
label {
  width: 100%;
  height: 3rem;
  font-size: 1rem;
}

/* Interation */
input:valid,
input:focus {
  border-bottom: 2px solid #26a69a;
}

input:valid + label,
input:focus + label {
  color: #26a69a;
  font-size: .8rem;
  top: -30px;
  pointer-events: none;
}

h1 {
    color: #616161;
    text-align: center;
    margin-bottom: 30px;
}

section {
    margin: 15px;
    box-shadow: 0 2px 2px 0 rgba(0,0,0,0.14), 0 1px 5px 0 rgba(0,0,0,0.12), 0 3px 1px -2px rgba(0,0,0,0.2);
    padding: 20px;
    border-radius: 0 0 2px 2px;
    background-color: #FFF;
}
/* label input {
  font: 18px Helvetica, Arial, sans-serif;
  box-sizing: border-box;
  display: block;
  border: none;
  padding: 20px;
  width: 300px;
  margin-bottom: 20px;
  font-size: 18px;
  outline: none;
  transition: all 0.2s ease-in-out;
}
label input::placeholder {
  transition: all 0.2s ease-in-out;
  color: #999;
  font: 18px Helvetica, Arial, sans-serif;
}
label input:focus, label input.populated {
  padding-top: 18px;
  padding-bottom: 12px;
}
label input:focus::placeholder, label input.populated::placeholder {
  color: transparent;
}
 label input:focus + span,  label input.populated + span {
  opacity: 1;
  top: 30px;
}
 label span {
  color: #4080d0;
  font: 13px Helvetica, Arial, sans-serif;
  position: absolute;
  top: 0px;
  left: 20px;
  opacity: 0;
  transition: all 0.2s ease-in-out;
} */
</style>
