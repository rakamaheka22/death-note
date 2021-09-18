<template>
  <div class="list">
    <h2>List of Target</h2>
    <hr>
    <ul v-if="listOfTarget.length > 0">
      <li v-for="(list, index) in listOfTarget" :key="index">
        <div>
          <input
            v-model="list.status"
            type="checkbox"
            id="completed" 
            :value="true"
          />
          <span :class="list.status ? 'strike' : ''">
            {{ list.name }}
          </span>
        </div>
        <button v-if="!list.status" @click="onRemove(listOfTarget, list.id)">
          Coret
        </button>
      </li>
    </ul>
    <div class="empty-list" v-else>
      Belum ada target
    </div>
  </div>
</template>

<script>
export default {
  name: 'List',
  props: {
    listOfTarget: {
      type: Array,
      default: () => {
        return []
      },
    },
    name: {
      type: String,
      default: ''
    },
    status: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    onRemove(listOfTarget, id) {
      const selectionRemove = listOfTarget.filter((item) => item.id !== id)
      this.$emit('targetlist', selectionRemove)
    }
  }
}
</script>

<style scoped>
.list {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  margin: auto;
}

h2 {
  font-size: 16px;
  color: white;
  align-self: flex-end;
}

hr {
  border: 1px solid #202124;
  width: 100%;
}

ul {
  list-style: none;
  width: 100%;
}

li {
  display: flex;
  align-items: center;
  justify-content: space-between;
  color: white;
  margin-bottom: 16px;
}

input[type=checkbox] {
  margin-right: 16px;
}

.empty-list {
  color: white;
  margin-top: 16px;
}

.strike {
  text-decoration: line-through;
}

button {
  border: none;
  background-color: #ef4c29;
  color: white;
  padding: 5px 10px;
  border-radius: 5px;
}

@media only screen and (min-width: 1280px) {
    .list {
      width: 480px;
    }
}
</style>
