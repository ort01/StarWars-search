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

<!-- .search-phrase {
    width: 345px;
    margin-bottom: 3px;
    background-color: #2C3843;
    color: white;
    border-radius: 4px;
    transition: all 1s;
    position: relative;
    overflow: hidden;
}

.search-phrase:hover {
    color: #2C3843;
}

.search-phrase:before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: #2FD17D;
    z-index: -1;
    border-radius: 0 0 50% 50%;
    height: 0%;
    transition: all 1s;
}

.search-phrase:hover:before {
    height: 200%;
} -->