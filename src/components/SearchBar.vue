<template>
    <q-input color="primary" outlined @input="emitSearchNameChange" :value="searchName" label="Name" class="search-bar">
        <template v-slot:append>
            <span class="material-icons" style="color:#2FD17D; font-size: 1.5rem;">
                search
            </span>
        </template>
    </q-input>
</template>




<script>
export default {
    name: 'SearchBar',
    props: {
        searchName: String
    },
    methods: {
        emitSearchNameChange(value) {
            this.$emit("searchName", value)
        }
    },
}
</script>




<style>
.search-bar {
    width: 345px;
    margin-bottom: 5px;
}
</style>