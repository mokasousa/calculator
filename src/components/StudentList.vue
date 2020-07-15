<template>
  <div class="container">
    <h2 class="heading-secondary">Notas mínimas necessárias para a prova 3</h2>
    <div class="list-view">
        <div class="list-view-item" v-for="student in list" v-bind:key="student.id" v-bind:class="student.status">
            <p class="text">{{student.name}} <b>{{student.p3}}</b></p>
            <button v-on:click="$emit('delete-student', student.id)">X</button>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'StudentList',
  props: ['list']
}
</script>
<style scoped>
  .list-view-item{
    border-radius: 4px;
    padding: 1rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin: 1rem auto;
    width: 70vw;
  }
  .not-pass{
    background: #f7797d;
  }
  .pass{
    background: #ADD9EA;
  }
  button{
    background-color: transparent;
    border: none;
    cursor: pointer;
  }
  button:focus{
    outline: none;
  }

</style>
