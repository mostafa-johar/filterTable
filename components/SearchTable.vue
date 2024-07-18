<script setup>
const emit = defineEmits(["search"]);
const onSearch = (e) => {
    emit("search", e.target.value);
};
</script>

<template>
    <div class="seatch-table">
        <label for="search">
            <div class="iconSearch"></div>
            <input type="text" id="search" placeholder="Search...(id or title)" @input="onSearch" />
        </label>
    </div>
</template>

<style lang="scss" scoped>
.seatch-table {
    label {
        @apply relative;

        .iconSearch {
            @apply absolute top-0 left-2 w-3 h-3 rounded-full border-4 border-gray-200 p-1;

            &::after {
                content: "";
                width: 5px;
                height: 10px;
                position: absolute;
                top: 10px;
                right: -8px;
                background-color: #ebebeb;
                transform: rotate(-45deg);
            }
        }

        input {
            @apply border border-gray-200 rounded-md outline-blue-300 bg-gray-50 py-2 pl-10;
        }
    }
}
</style>
