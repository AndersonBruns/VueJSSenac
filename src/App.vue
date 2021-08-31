<template>
  <div>
    <h1> Meu projeto VueJS</h1>
    <!-- Customizar um componente dinamicamente, necessita por dois pontos na frente -->
    <p :title="info">Autor: {{autor}} - {{criacao}}</p>
    
    <button @click="showInfo()">Mostrar/Esconder informações</button>
    <div v-if="mostrarInfoComplementar">
      <h2>Informação adicional</h2>

     <form @submit.prevent="addProject()">
        <label for="nome">Nome:</label><br/>
        <input type="text" id="nome" autofocus required v-model="projeto.nome"/><br/>
        <label for="tamanho">Tamanho:</label><br/>
        <input type="number" id="tamanho" required min="0" max="100" v-model="projeto.tamanho"/><br/>
        <input type="submit" id="btn" value="Adicionar projeto"/>
      </form> 

      <ul>
          <li v-for="p in projetos" :key="p.nome"> {{p.nome}} <button @click="remove(p)"> Remover </button></li>
      </ul>
    </div>

    </div>
</template>

<script>

export default {
  data(){
    return { //JSON
      autor: 'Anderson Bruns',
      //criacao: 'Criado em: ' + new Date().toLocaleString()
      criacao: `Criado em: ${new Date().toLocaleString()}`,
      info: 'Posso colocar uma informação customizada',
      mostrarInfoComplementar: true,
      projetos: [
        {nome: 'HTML', tamanho: 100},
        {nome: 'CSS', tamanho: 80},
        {nome: 'JS', tamanho: 200}
        ],

        projeto:{
          nome: null,
          tamanho: 0
        }
    }
  },

  methods:{
    showInfo(){
      this.mostrarInfoComplementar = !this.mostrarInfoComplementar;
    },

    addProject(){
      this.projetos.push({
        nome: this.projeto.nome,
        tamanho: this.projeto.tamanho
      })
    },

    remove(projetoRemove){
      if(confirm("Deseja remover?")){
        this.projetos.splice(this.projetos.indexOf(projetoRemove), 1)
      }
    }

  },

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
}
</style>
