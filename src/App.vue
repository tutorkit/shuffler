<template>
  <div id="app">
    <section class="section">
      <div class="container">
        <h1 class="title">{{appName}}</h1>
        <Source />
      </div>
      <div class="container">
        <Shuffler />
      </div>
    </section>
  </div>
</template>

<script>
import Source from './components/Source.vue'
import Shuffler from './components/Shuffler.vue'

export default {
  components: {
    Source,
    Shuffler
  },
  name: 'app',
  data () {
    return {
      appName: 'TutorKit',
      msg: 'My first website with <strong>Bulma</strong>!'
    }
  }
}
</script>

<style lang="scss">
  @import "../node_modules/bulma/bulma.sass";
</style>

<style>
#app {
  font-family: 'Noto Sans CJK KR', 'NanumGothic', Helvetica, Arial, sans-serif;
  color: #2c3e50;
  width: 720px;
}
</style>

<style scoped>
ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
