<template>
    <q-input color="primary" outlined @input="emitSearchNameChange" :value="searchName" label="Name" class="search-bar"
        :class="{error: isError}">
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
        searchName: String,
        arrayOfCharactersLength: Number
    },
    methods: {
        emitSearchNameChange(value) {
            this.$emit("searchName", value)
        }
    },
    computed: {
        isError() {
            if (this.arrayOfCharactersLength === 0 && this.searchName.length > 0) {
                return true
            } return false
        },
    }
}
</script>




<style>
.search-bar {
    width: 345px;
    margin-bottom: 5px;
}

.error input::selection {
    background-color: rgba(255, 0, 0, 0.144);
}
</style>