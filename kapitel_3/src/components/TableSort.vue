<script setup>
import { computed, ref, onMounted } from 'vue'

const sortBy = ref('name')
const persons = ref([])

const sortedPersons = computed(() => {
    return persons.value.sort((a, b) =>
        a[sortBy.value].localeCompare(b[sortBy.value])
    )
})

onMounted(async () => {
    const response = await fetch('https://jsonplaceholder.typicode.com/users');
    const data = await response.json()
    persons.value = data
})

</script>
<template>
    <table>
        <thead>
            <tr>
                <th @click="sortBy = 'name'">Name</th>
                <th @click="sortBy = 'username'">Benutzername</th>
                <th @click="sortBy = 'email'">E-Mail</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="person in sortedPersons" :key="person.id">
                <td>{{ person.name }}</td>
                <td>{{ person.username }}</td>
                <td>{{ person.email }}</td>
            </tr>
        </tbody>
    </table>
</template>
<style>
table {
    border-collapse: collapse;
}

td,
th {
    border: 1px solid blue;
    padding: 1rem;
}

th {
    cursor: pointer;
}
</style>