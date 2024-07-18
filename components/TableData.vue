<script setup>
defineProps({
    items: {
        type: Array,
        required: true
    }
})
</script>
<template>
    <div class="TableData">
        <table>

            <thead>
                <tr>
                    <th>id</th>
                    <th>title</th>
                    <th>price</th>
                    <th>category</th>
                    <th>description</th>
                    <th>date</th>
                </tr>
            </thead>

            <tbody>
                <tr v-for="item in items" :key="item.id">
                    <td>{{ item.id }}</td>
                    <td>{{ item.title }}</td>
                    <td>{{ item.price }}</td>
                    <td>{{ item.category.name }}</td>
                    <td>{{ item.description }}</td>
                    <td>{{ new Date(item.creationAt).toLocaleDateString() }}</td>
                </tr>
            </tbody>

        </table>
    </div>
</template>
<style lang="scss" scoped>
table {
    @apply border-collapse text-center w-full;

    tr {
        @apply border-b border-gray-200;

        th {
            @apply text-slate-900 bg-gray-50 text-base font-semibold;
        }

        td {
            @apply text-[13px] text-gray-600 font-medium;
        }

        th,
        td {
            @apply p-2
        }
    }
}
</style>
