<script setup lang="ts">
const buttonList = ref(['b1', 'b2', 'b3', 'b4', 'b5'])
const itemRefs = ref([])


onMounted(() => {
      if (itemRefs.value) {
        itemRefs.value[0].focus()
      }
    });


</script>

<template>
  <div class="container mt-5 mx-5">
    <button ref="itemRefs" v-for="(bb, index) in buttonList" type="button" 
    class="focus:bg-blue-700 text-white bg-blue-200 font-medium rounded-lg text-sm px-5 py-2.5 mr-2 mb-2 dark:bg-blue-600 dark:hover:bg-blue-700 focus:outline-none dark:focus:ring-blue-800">
    {{ bb }}
  </button>
  </div> 

</template>