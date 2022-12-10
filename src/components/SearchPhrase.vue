<template>
    <q-field color="primary" outlined stack-label>
        <template v-slot:control>
            <div class="self-center full-width no-outline" tabindex="0" style="color:white"
                v-html="highlightSearchedTerm(foundName, searchName)" />
        </template>
    </q-field>
</template>



<script>
export default {
    name: "SearchPhrase",
    props: {
        foundName: String,
        searchName: String
    },
    methods: {
        highlightSearchedTerm(foundName, searchName) {
            var searchRegularExpression = new RegExp(`(${searchName})`, 'gi');
            // var nameWithHighlightedLetters = foundName.replace(new RegExp(`(${searchName})`, 'gi'), "<strong>$1</strong>")
            var nameWithHighlightedLetters = foundName.replace(searchRegularExpression, "<strong>$1</strong>")
            return nameWithHighlightedLetters;
        }
    }
}
</script>