<script lang="ts" setup>
import { ref } from "vue";

const emit = defineEmits(['categoryArr'])

const showFilter = ref(false);
const ByCategory = ref([]);
const arrCategory = ref(['Furniture', 'Soap', 'Cheese', 'Fish', 'Salad', 'Shoes', 'Computer', 'Pizza']);



const onHundleChange = () => {
  emit('categoryArr', ByCategory.value)
}


</script>
<template>
  <div class="filter-table">

    <div class="boxFilter">
      <button @click="showFilter = !showFilter">
        <div class="flex flex-col gap-[3px] justify-center items-center">
          <span class="w-6 h-[1px] bg-slate-800 p-[1px]" </span>
            <span class="w-4 h-[1px] bg-slate-800 p-[1px]"></span>
            <span class="w-2 h-[1px] bg-slate-800 p-[1px]"></span>
        </div>
        Filter
      </button>
    </div>

    <!-- absolute -->
    <form class="filterForm" v-show="showFilter">
      <h3>Filter By Category :</h3>

      <div class="form-controll" v-for="(item, index) in arrCategory" :key="`${item}_${index}`">
        <input type="checkbox" :value="item" :id="item" v-model="ByCategory" @change="onHundleChange" />
        <label :for="item">{{ item }}</label>
      </div>
    </form>
  </div>
</template>

<style lang="scss" scoped>
.filter-table {
  @apply relative;

  .boxFilter {
    @apply flex justify-end;

    button {
      @apply flex gap-2 items-center border-4 rounded-lg border-gray-50 font-medium text-gray-900 px-5 py-2;
    }
  }

  .filterForm {
    @apply bg-white shadow-md p-3 absolute top-20 right-0 w-[200px] z-[100];

    h3 {
      @apply text-[12px] text-gray-950 font-semibold my-2;
    }

    .form-controll {
      @apply flex gap-2;

      label {
        @apply text-sm;
      }
    }
  }
}
</style>
