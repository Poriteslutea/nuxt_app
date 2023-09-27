<script setup lang="ts">
const buttonList = ref(['b1', 'b2', 'b3', 'b4', 'b5'])
const itemRefs = ref([])

const btnContent = ref(['Default Active Button', 'Default Inactive Button'])
  const selectedBtn = ref('Default Active Button')

  function clickBtn(val) {
    selectedBtn.value = val
  }



onMounted(() => {
      if (itemRefs.value) {
        itemRefs.value[0].focus()
      }
    });


</script>

<template>
  <div class="container mt-5 mx-5">
    <button ref="itemRefs" v-for="(bb, index) in buttonList" type="button" 
      class="focus:bg-blue-700 text-white bg-blue-200 font-medium rounded-lg text-sm px-5 py-2.5 ms-2 dark:bg-blue-600 dark:hover:bg-blue-700 focus:outline-none dark:focus:ring-blue-800">
      {{ bb }}
    </button>

    <button type="button" v-for="(val, idx) in btnContent"  @click="clickBtn(val)" :class="{'bg-blue-800': selectedBtn === val}"  class="mt-5 ms-2 bg-blue-200 text-gray-100 hover:bg-blue-800 hover:text-gray-100  group w-40 h-15 p-3 rounded-md items-center text-xs font-medium">
              {{ val }}
    </button>
  </div> 


</template>