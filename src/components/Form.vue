<template>
   <div class="form w-full h-10 bg-white border-b-2 border-solid border-indigo-300 flex">
      <span class="inline-block pt-2 pl-1 bg-gray-500 w-1/12">
         <svg class="w-5 h-5 stroke-current text-white" fill="none" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" stroke="currentColor" viewBox="0 0 24 24">
            <path d="M11 5H6a2 2 0 00-2 2v11a2 2 0 002 2h11a2 2 0 002-2v-5m-1.414-9.414a2 2 0 112.828 2.828L11.828 15H9v-2.828l8.586-8.586z"></path>
         </svg>
      </span>
      <input v-on:keyup.enter="addTodo" v-model="text" class="w-8/12 h-full pl-2" value="text" type="text" name="text" id="text" placeholder="enter todo...">
      <button @click="addTodo" class="w-3/12 h-full text-white font-bold bg-gray-500 hover:bg-gray-600">submit</button>
   </div>
</template>

<script>
export default {
   name: "Form",
   data: function() {
      return {
         text: ""
      }
   },
   methods: {
      addTodo: function() {
         if(this.text == "") {
            alert("Invalid input")
            return
         }
         this.$emit("addTodo", this.text)
         this.text = ""
      }
   }
}
</script>

<style lang="scss" scoped>

</style>