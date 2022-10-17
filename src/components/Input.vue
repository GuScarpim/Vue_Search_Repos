<template>
  <section>
    <form @submit.prevent="(event) => $emit('input', nameData)">
      <h1>Buscar Usuários e repositórios no Github</h1>
      <div class="input-container">
        <input
          type="text"
          v-model="nameData"
          placeholder="Insira um nome de usuário do GitHub"
        />
        <label class="label" for="name">Nome</label>
      </div>
      <div class="positionBtn">
        <button type="submit" class="btnSearch">Pesquisar</button>
      </div>
    </form>
  </section>
</template>

<script>
export default {
  name: 'Input',
  data() {
    return {
      nameData: '',
    }
  },
}
</script>

<style scoped>
.btnSearch {
  margin-top: 20px;
  width: 120px;
  height: 40px;
  font-size: 1.2rem;
  background-color: #54a89a;
  width: 100%;
  border: none;
  border-radius: 30px;
  color: #fff;
  cursor: pointer;
}

.btnSearch:hover {
  background-color: #459689;
  color: #f3f3f9;
}

.positionBtn {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.input-container {
  position: relative;
}

input {
  border: 0;
  border-bottom: 2px solid #9e9e9e;
  outline: none;
  transition: 0.2s ease-in-out;
  box-sizing: border-box;
}

label {
  top: 0;
  left: 0;
  right: 0;
  color: #616161;
  display: flex;
  align-items: center;
  position: absolute;
  font-size: 1rem;
  cursor: text;
  transition: 0.2s ease-in-out;
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
  font-size: 0.8rem;
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
  box-shadow: 0 2px 2px 0 rgba(0, 0, 0, 0.14), 0 1px 5px 0 rgba(0, 0, 0, 0.12),
    0 3px 1px -2px rgba(0, 0, 0, 0.2);
  padding: 20px;
  border-radius: 0 0 2px 2px;
  background-color: #fff;
}
</style>
