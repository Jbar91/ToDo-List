<template>
  <h1>Your To Do List</h1>
  <div>
    <input
      @keydown.enter="CreateTask"
      type="text"
      placeholder="What's to do?"
      autocomplete="no"
      v-model="task"
    />
    <button @click="CreateTask" class="create">Create</button>
  </div>
  <div class="task-container">
    <h3 v-if="!chores.length">You have no pending tasks!</h3>
    <ul v-if="chores.length">
      <li v-for="(chore, index) in chores" :key="chore">
        <p>{{ chore }}</p>
        <button @click="RemoveTask(index)" class="remove">Remove</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "List",
  data() {
    return {
      chores: [],
      task: "",
    };
  },
  //JSON.parse(localStorage.getItem("SavedTasks"))
  methods: {
    CreateTask() {
      this.chores = [...this.chores, this.task];
      localStorage.setItem("SavedTasks", JSON.stringify(this.chores));
      this.task = "";
    },
    RemoveTask(choreIndex) {
      localStorage.removeItem(this.chores[choreIndex]);
      this.chores.splice(choreIndex, 1);
      localStorage.setItem("SavedTasks", JSON.stringify(this.chores));
    },
  },
  mounted() {
    if (JSON.parse(localStorage.getItem("SavedTasks"))) {
      this.chores = JSON.parse(localStorage.getItem("SavedTasks"));
    }
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
input {
  padding: 5px;
  border-radius: 10px;
  text-align: center;
  margin-right: 15px;
}
button {
  padding: 5px;
  border-radius: 8px;
}
li {
  list-style: none;
  display: flex;
  flex-wrap: wrap;
  flex-flow: row;
  justify-content: center;
  align-items: center;
}
p {
  background-color: whitesmoke;
  border: 0.2px solid black;
  border-radius: 12px;
  padding: 8px 12px;
  margin-right: 10px;
  font-weight: bold;
  min-width: 40px;
}
.task-container {
  border: 1px solid black;
  overflow-y: auto;
  height: 65%;
  width: 85%;
  margin-top: 60px;
}
.create {
  background-color: yellowgreen;
  color: black;
}
.remove {
  background-color: red;
  color: whitesmoke;
}
</style>
