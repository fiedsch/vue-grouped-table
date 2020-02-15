<template>
    <div role="rowgroup">
        <div class="tr" role="row" v-for="(row, i)  in rows" v-bind:key="row.id">
            <template v-if="i == 0 && data.ids.length>1">
                <span class="td" role="cell" v-if="isCollapsed" @click="toggleCollapsed">+</span>
                <span class="td" role="cell" v-else @click="toggleCollapsed">−</span>
            </template>
            <template v-else>
                <span v-if="!isCollapsed" role="cell" class="td" >&nbsp;</span>
            </template>
            <template v-if="i == 0 || (i > 0 && !isCollapsed)">
                <span class="td" role="cell">{{ row.name }}</span>
                <span class="td" role="cell">{{ row.id }}</span>
            </template>
        </div>
    </div>
</template>

<script>
export default {
    name: 'RowsGroup',
    props: {
        data: Array
    },
    data() {
        return {
            isCollapsed: false
        }
    },
    computed: {
        rows() {
            let result = [];
            this.data.ids.forEach((id) => { result.push({ name: this.data.name, id: id })})
            return result
        }
    },
    methods: {
        toggleCollapsed() {
            this.isCollapsed = !this.isCollapsed
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    div.tr {
        display: table-row;
    }
    span.td:first-child {
        width: 1rem;
    }
    span.td {
        display: table-cell;
        border: 1px solid #999;
        padding: .5rem;
        width: 4rem;
    }
</style>
