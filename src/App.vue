<template>
  <div>
    <h1> Meu projeto VueJS</h1>
    <!-- Customizar um componente dinamicamente, necessita por dois pontos na frente -->
    <p :title="info">Autor: {{autor}} - {{criacao}}</p>
    
    <button @click="showInfo()">Mostrar/Esconder informações</button>
    <div v-if="mostrarInfoComplementar">
      <h2>Informação adicional</h2>

      <ul>
          <li v-for="p in projetos" :key="p.nome"> {{p.nome}}</li>
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
        ]
    }
  },

  methods:{
    showInfo(){
      this.mostrarInfoComplementar = !this.mostrarInfoComplementar;
    }
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
}
</style>
