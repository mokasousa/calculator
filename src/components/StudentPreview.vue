<template>
  <div>
    <div v-if='!studentView'></div>
    <div v-else v-bind:class="studentView.status">
      <h2 class="heading-secondary">{{studentView.name}}</h2>
      <p>{{studentView.p3}}</p>
      <p v-show="studentView.status === 'not-pass'">🖌️ Precisa de reforço!</p>
      <p v-show="studentView.status === 'pass'">⭐ Está indo muito bem!</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'StudentPreview',
  props:{
    'studentView':{
      type: Object,
      default: () => ({}) 
    }
  }
}
</script>

<style scoped>
  .not-pass{
    width: 50vw;
    margin: 2vh 5vh;
    min-width: 300px;
    background: #f7797d;
    padding: 15%;
    display: flex;
    flex-direction: column;
    align-items: center;
    border-radius: 4px;
  }
  .pass{
    width: 50vw;
    margin: 2vh 5vh;
    min-width: 300px;
    background: #ADD9EA;
    padding: 15%;
    display: flex;
    flex-direction: column;
    align-items: center;
    border-radius: 4px;
  }
  p{
    margin-bottom: 3%;
  }
</style>