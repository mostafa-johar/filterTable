<script setup>
useHead({
  title : 'Filter Table'
})
const categoryFilter = ref([]);
const searchFilter = ref("");

const { data } = await useFetch('/api/test')
const { dataitems } = data.value

const handleFilterCategory = (category) => {
  categoryFilter.value = category;
};

const handleFilterSearch = (search) => {
  searchFilter.value = search;
};

const filterData = computed(() => {
  let data = dataitems;
  // filter by searching
  if (searchFilter.value !== "") {
    data = data.filter((item) => {
      return (
        item.id.toString().includes(searchFilter.value) ||
        item.title.includes(searchFilter.value)
      );
    });
  }

  // filter by category
  if (categoryFilter.value.length !== 0) {
    data = data.filter((item) => {
      return categoryFilter.value.includes(item.category.name);
    });
  }

  return data;
});
</script>
<template>
  <div class="app">
    <div class="container">
      <section class="box">
        <div class="flex justify-between items-center md:flex-row flex-col-reverse gap-3 px-3 py-5">
          <!-- search input -->
          <SearchTable @search="handleFilterSearch" />

          <!-- Filter => data -->
          <FilterTable @categoryArr="handleFilterCategory" />
        </div>
        <!-- table => data -->
        <TableData :items="filterData" />
      </section>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.app {
  @apply py-5;

  .box {
    @apply bg-white rounded-md border border-gray-200 overflow-x-auto min-h-screen;
  }
}
</style>
