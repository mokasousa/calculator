<template>
    <div class="container">
      <h2 class="heading-secondary">Verifique se seu aluno pode aprovar</h2>
      <form @submit.prevent="getGrade">
        <div class="form-group">
            <label for="name">Nome do Aluno</label>
            <input v-model="name" type="text" name="name" class="input text" maxlength="35" required>
        </div>
        <div class="form-group">
            <label for="p1">Prova 1</label>
            <input v-model="p1" type="number" name="p1" class="input number" min="0" max="10" step="0.1" required>
        </div>
        <div class="form-group">
            <label for="p2">Prova 2</label>
            <input v-model="p2" type="number" name="p2" class="input number" min="0" max="10" step="0.1" required>
        </div>
        <input type="submit" value="Obter nota mínima" class="btn-submit">
      </form>
    </div>
</template>

<script>
export default {
  name: 'StudentCalc',
  data(){
    return{
        name:'',
        p1:null,
        p2:null,
    }
  },
  methods:{
    getGrade(){
      let status='';
      const id = Date.now();
      const p3 = ((6.2 - this.p1 * 0.25 - this.p2 * 0.25)*2).toFixed(1);
      p3 <= 10 
          ? status='pass'
          : status='not-pass';
      const student = {
        id,
        name:this.name,
        p3,
        status
      };
      this.$emit('add-student', student);
      this.name = '';
      this.p1 = null;
      this.p2 = null;
    }
  }
}
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
  align-items: stretch;
  font-size: 0.9rem;
  color: #888888;
}
.form-group{
    display: flex;
    flex-direction: column;
    margin-bottom: 2vh;
}
label{
  margin-bottom: 0.8vh;
  transition: all .3s;
}
.input{
  border: none;
  border-bottom: 1px solid #888;
  padding: .5rem;
  background-color: #fff;
  transition: all .3s;
  background-color: transparent;
}
.input:focus{
  border-bottom: 2px solid #ADD9EA;
  outline: none;
}
.input:focus:invalid{
  border-bottom: 2px solid #f7797d;
  outline:none;
}
.number::-webkit-inner-spin-button,
.number::-webkit-outer-spin-button{
  -webkit-appearance: none;
}
input[type=number] {
  -moz-appearance: textfield;
}
.btn-submit{
  background-color: #C6FFDD;
  border: unset;
  border-radius: 15px;
  padding: .5rem 1rem;
  box-shadow: 0px 3px 1px #ADD9EA;
  font-weight: bold;
  color: inherit;
  transition: all .3s;
  outline: none;
  font-size: .9rem;
  margin: 1rem;
}
.btn-submit:hover{
  transform: translateY(-1px);
  box-shadow: 0px 4px 1px #ADD9EA;
  outline: none;
}
.btn-submit:active{
  box-shadow: 0px 2px 1px #ADD9EA;
  transform: translateY(2px);
  outline: none;
}
</style>