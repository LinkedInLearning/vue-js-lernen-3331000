<script >
export default {
    data() {
        return {
            newItem: '',
            items: [
                { id: 1, title: 'Brot' },
                { id: 2, title: 'Tomaten' },
                { id: 3, title: 'Öl' },
            ]
        }
    },
    /* Methode zum Hinzufügen von Punkten definieren */
    methods: {
        addItem() {
            this.items.push({ id: this.items.length + 1, title: this.newItem })
            this.newItem = ''
        }
    }
}
</script>

<template>
    <h2>Option API</h2>
    <!-- Beim Absenden des Formulars soll newItem
        der Liste hinzugefügt werden.
        Das Absenden des Formular soll unterbunden werden -->
    <form @submit.prevent="addItem">
        <label for="newItem">weiteren Artikel</label>
        <input id="newItem" v-model="newItem">
        <input type="submit">
    </form>
    <!-- Alle Inhalte der Einkaufliste in einer Schleife 
        ausgeben lassen-->
    <ol>
        <li v-for="item in items" :key="item.id">{{ item.title }}</li>
    </ol>
</template>
<style>
label {
    display: block;
}
</style>