<template>
    <q-field color="primary" outlined stack-label>
        <template v-slot:control>
            <div class="self-center full-width no-outline" tabindex="0" style="color:white"
                v-html="highlightSearchedTerm(characterName, searchName)" />
        </template>
    </q-field>
</template>




<script>
export default {
    name: "FoundCharacters",
    props: {
        characterName: String,
        searchName: String
    },
    methods: {
        highlightSearchedTerm(searchResult, searchName) {
            return searchResult.replace(searchName, '<strong>' + searchName + '</strong>');
        }
    }
}
</script>