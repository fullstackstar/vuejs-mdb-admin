<template>
  <mdb-container class="right-panel">
    <h2>Detail:</h2>
    <div v-show="this.title==='Users'">
      <p><span class="green-text">id:</span> {{ detail.id }}</p>
      <p><span class="green-text">name:</span> {{ detail.name }}</p>
      <p><span class="green-text">username:</span> {{ detail.username }}</p>
      <p><span class="green-text">email:</span> {{ detail.email }}</p>
    </div>
    <div v-show="this.title==='Posts'">
      <p><span class="green-text">id:</span> {{ detail.id }}</p>
      <p><span class="green-text">Title:</span> {{ detail.title }}</p>
      <p><span class="green-text">Content:</span> {{ detail.body }}</p>
    </div>
  </mdb-container>
</template>

<script>
  import { mdbContainer } from 'mdbvue';
  export default {
    name: 'LeftPanel',
    components: {
      mdbContainer
    },
    props: {
      title: String,
      detail: Object
    },
    mounted(){
      console.log(this.title)
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
</style>
