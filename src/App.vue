<template>
  <div id="app">
    <Header />
    <Note @onAddNote="onAddNote($event)" />
    <List :list-of-target="list" @targetlist="list = $event" />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import List from './components/List.vue';
import Note from './components/Note.vue';

export default {
  name: 'App',
  components: {
    Header,
    List,
    Note
  },
  data() {
    return {
      list: []
    }
  },
  methods: {
    onAddNote($event) {
      this.list = [...this.list, $event]
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;700&display=swap');

body {
  background-color: #010101;
  overflow-x: hidden;
  font-family: 'Poppins', sans-serif;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>

