<template>
  <div class="note">
    <form ref="form" @submit.prevent="addNote">
      <label for="name">
        Name :
      </label>
      <input v-model="name" type="text" name="name" />
    </form>
  </div>
</template>

<script>
export default {
  name: 'Note',
  data() {
    return {
      name: ''
    }
  },
  methods: {
    addNote() {
      this.$emit('onAddNote', {
        id: Math.floor(Math.random() * 1000),
        name: this.name,
        status: false
      })
      this.name = ''
    }
  }
}
</script>

<style scoped>
.note {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  margin: auto;
  margin-top: 48px;
}

form {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 24px;
}

label {
  color: white;
  font-weight: bold;
  min-width: 100px;
}

input[type=text] {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  box-sizing: border-box;
  outline: none;
  border-radius: 10px;
  font-weight: bold;
  font-size: 14px;
  color: white;
  background-color: #202124;
  border: 0px;
}

@media only screen and (min-width: 1280px) {
    .note {
      width: 480px;
    }
}
</style>
