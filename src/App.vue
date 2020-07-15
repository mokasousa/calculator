<template>
  <div id="app">
    <header class="header">
      <h1 class="heading-primary" data-text="Calculadora do Bentinho">
        Calculadora do Bentinho
      </h1>
    </header>
    <div>
      <div class="align-responsive">
        <StudentCalc v-on:add-student=addStudent />
        <StudentPreview v-bind:studentView='studentView'/>
      </div>
      <StudentList v-bind:list='list' v-on:delete-student=deleteStudent v-if='list.length > 0' />
    </div>
    <div class="findme">
      <p>Criado com 🤍 por Mônica Sousa.</p>
      <div class="links">
        <a href="http://github.com/mokasousa">
            Github
        </a>
        <a href="http://linkedin.com/in/mosousa">
            Linkedin
        </a>
        <a href="https://app.talento.laboratoria.la/profile/vxpWQ9ZnM8coLZ0ENsGjQYXtWDN2">
            App de Talentos
        </a>
      </div>
    </div>
  </div>
</template>

<script>
import StudentCalc from './components/StudentCalc.vue'
import StudentPreview from './components/StudentPreview.vue'
import StudentList from './components/StudentList.vue'

export default {
  name: 'App',
  components: {
    StudentCalc,
    StudentPreview,
    StudentList
  }, 
  data() {
    return{
      list:[],
      studentView: { 
        type: Object, 
        default: () => ({}) 
      }
    }
  },
  methods:{
    deleteStudent(id){
      this.list = this.list.filter(el => el.id !== id)
    },
    addStudent(student){
      this.studentView = student      
      this.list = [...this.list, student].sort((a, b) => a.name < b.name ? -1 : 1)
    }
  }
}
</script>

<style>
  *{
    box-sizing: border-box;
    margin:0;
    padding:0;
  }

  body {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    color: #404040;
    min-height: 100vh;
    height: auto;
    overflow: auto;
    background: url(./assets/plush-design-studio-photo-unsplash.jpg);
    background-size: cover;
    background-position: bottom;
  }

  #app{
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }
  
  .container{
    width: fit-content;
    margin: 3vh auto;
    padding: 1rem;
    background-color: rgb(255,255,255, .8);
    border-radius: 4px;
    max-width: 80vw;
  }

  .align-responsive{
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: center;
  }

  .header {
    height: 20vh;
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
    padding: 5%;
  }

  .heading-primary{
    font-size: 2.5rem;
    text-transform: uppercase;
    background-image: linear-gradient(to right,#f7797d, #FBD786, #C6FFDD);
    background-clip: text;
    -webkit-background-clip: text;
    color: transparent;
    position: relative;
  }

  .heading-primary:after{
    position: absolute;
    top:0;
    left:0;
    z-index:-1;
    background:none;
    content: attr(data-text);
    text-shadow: 3px 3px 3px #C0C0C0;
  }

  .heading-secondary{
    font-size: 1rem;
    text-transform: uppercase;
    margin-bottom: 2rem;
  }

  .findme{
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    width: 100%;
    bottom: 0;
    padding: 1rem;
  }

  .links{
    display: flex;
    align-items: center;
  }

  .links a,
  .links a:link,
  .links a:visited{
    text-decoration: none;
    font-weight: bold;
    color:inherit;
    margin: 1vw;
  }

  .links a:hover{
    color: #ADD9EA;
  }

</style>
