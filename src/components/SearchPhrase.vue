<template >
    <div class="searched-phrase">
        <q-field color="primary" outlined stack-label style="cursor: pointer">
            <template v-slot:control>
                <div class="self-center full-width no-outline" tabindex="0" style="color:white"
                    v-html="highlightSearchedTerm(foundName, searchName)" />
            </template>
        </q-field>
    </div>
</template>



<script>
export default {
    name: "SearchedPhrase",
    props: {
        foundName: String,
        searchName: String
    },
    methods: {
        highlightSearchedTerm(foundName, searchName) {
            var searchRegularExpression = new RegExp(`(${searchName})`, 'gi');
            var nameWithHighlightedLetters = foundName.replace(searchRegularExpression, "<strong>$1</strong>")
            return nameWithHighlightedLetters;
        }
    }
}
</script>

<style>
.searched-phrase {
    width: 345px;
    margin-bottom: 3px;
    background-color: #2C3843;
    color: white;
    border-radius: 4px;
    transition: all 1s;
}
</style>