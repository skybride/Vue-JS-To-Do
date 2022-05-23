<template>
  <div>
    <h1>To Do List</h1>
    <hr>
    <div v-if="!isEditing">
      <input type="text" v-model="toDoItem">
      <input type="submit" value="Add" @click="addItem">
    </div>
    <div v-else>
      <input type="text" v-model="toDoItem">
      <input type="submit" value="Update" @click="updateItem">
    </div>
    <ul>
      <li v-for="(toDo, index) in toDoItems">
        {{ toDo }}
        <button @click="editItem(index, toDoItem)">edit</button>
        <button @click="deleteItem(index, toDoItem)">delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "ToDoListView",
  data(){
    return {
      toDoItem: "",
      toDoItems: [],
      selectedIndex: null,
      isEditing: false
    }
  },
  methods: {
    addItem(){
      this.toDoItems.push(this.toDoItem);
      this.toDoItem = "";
    },
    editItem(index, toDoItem){
      this.toDoItem = toDoItem;
      this.selectedIndex = index;
      this.isEditing = true;
    },
    updateItem(){
      this.toDoItems.splice(this.selectedIndex, 1, this.toDoItem)
      this.isEditing = false;
    },
    deleteItem(index){
      this.toDoItems.splice(index, 1);
    }
  }

}
</script>

<style scoped>

</style>