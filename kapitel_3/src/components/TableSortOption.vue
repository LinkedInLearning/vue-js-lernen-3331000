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
<script>
export default {
    data() {
        return {
            sortBy: 'name',
            persons: []
        }
    },
    computed: {
        sortedPersons() {
            return this.persons.sort((a, b) =>
                a[this.sortBy].localeCompare(b[this.sortBy])
            )
        }
    },
    async mounted() {
        const response = await fetch('https://jsonplaceholder.typicode.com/users');
        const data = await response.json()
        this.persons = data
    }
}
</script>