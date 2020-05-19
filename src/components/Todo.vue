<template>
   <div class="w-full h-10 flex justify-between px-2 py-2">
      <span class="mr-2">
         <svg v-if="!todo.completed" v-on:click="$emit('toggleComplete', todo.id)" class="w-5 h-5 stroke-current text-gray-500 cursor-pointer" fill="none" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" stroke="currentColor" viewBox="0 0 24 24">
            <path d="M9 12l2 2 4-4M7.835 4.697a3.42 3.42 0 001.946-.806 3.42 3.42 0 014.438 0 3.42 3.42 0 001.946.806 3.42 3.42 0 013.138 3.138 3.42 3.42 0 00.806 1.946 3.42 3.42 0 010 4.438 3.42 3.42 0 00-.806 1.946 3.42 3.42 0 01-3.138 3.138 3.42 3.42 0 00-1.946.806 3.42 3.42 0 01-4.438 0 3.42 3.42 0 00-1.946-.806 3.42 3.42 0 01-3.138-3.138 3.42 3.42 0 00-.806-1.946 3.42 3.42 0 010-4.438 3.42 3.42 0 00.806-1.946 3.42 3.42 0 013.138-3.138z"></path>
         </svg>
         <svg v-else v-on:click="$emit('toggleComplete', todo.id)" class="w-5 h-5 stroke-current text-gray-500 cursor-pointer" fill="none" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" stroke="currentColor" viewBox="0 0 24 24">
            <path d="M8.228 9c.549-1.165 2.03-2 3.772-2 2.21 0 4 1.343 4 3 0 1.4-1.278 2.575-3.006 2.907-.542.104-.994.54-.994 1.093m0 3h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"></path>
         </svg>
      </span>
      <span class="inline-flex w-4/5">
         <input v-model="text" v-if="isEditing" v-on:keyup.enter="editTodo" class="w-full" value="text" type="text" name="text" id="text">
         <p v-else v-bind:class="{ 'text-gray-400 line-through': todo.completed, 'text-gray-500': !todo.completed }">{{ todo.text }}</p>
      </span>
      <span class="inline-flex ml-1">
         <svg v-if="!isEditing" v-on:click="toggleEdit" class="w-5 h-5 mx-1 stroke-current text-gray-500 cursor-pointer" fill="none" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" stroke="currentColor" viewBox="0 0 24 24">
            <path d="M15.232 5.232l3.536 3.536m-2.036-5.036a2.5 2.5 0 113.536 3.536L6.5 21.036H3v-3.572L16.732 3.732z"></path>
         </svg>
         <svg v-else v-on:click="toggleEdit" class="w-5 h-5 mx-1 stroke-current text-gray-500 cursor-pointer" fill="none" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" stroke="currentColor" viewBox="0 0 24 24">
            <path d="M6 18L18 6M6 6l12 12"></path>
         </svg>
         <svg v-on:click="$emit('deleteTodo', todo.id)" class="w-5 h-5 mx-1 stroke-current text-gray-500 cursor-pointer" fill="none" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" stroke="currentColor" viewBox="0 0 24 24">
            <path d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16"></path>
         </svg>
      </span>
   </div>
</template>

<script>

export default {
   name: "Todo",
   props: ["todo"],
   data: function() {
      return {
         isEditing: false,
         text: this.todo.text
      }
   },
   methods: {
      toggleEdit: function() {
         this.isEditing = !this.isEditing
      },
      editTodo: function() {
         if(this.text == "") {
            alert("invalid input")
            return
         }

         const newTodo = { id: this.todo.id, text: this.text, completed: false}
         this.$emit("editTodo", newTodo)
         // console.log(this.text)
         this.isEditing = !this.isEditing
      }
   }
}

</script>

<style>

</style>