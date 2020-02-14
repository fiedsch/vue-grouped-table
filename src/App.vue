<template>
    <div>
        <rows-group v-for="row in rows" :data="row" v-bind:key="row.group_id"/>
    </div>
</template>

<script>
    import RowsGroup from "./components/RowsGroup";

    export default {
        name: 'App',
        components: {
            RowsGroup,
        },
        data() {
            return {
                rows: [
                    {'name': 'Tom', ids: [1, 2], group_id: 1 },
                    {'name': 'Sue', ids: [3], group_id: 2 },
                    {'name': 'Mae', ids: [4, 5], group_id: 3 }
                ]
            }
        },
    }
</script>

<style>
</style>
