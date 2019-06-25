<template>
    <div>
        <ul>
            <li v-for="(animal, index) in listOfAnimals" :key=index>
                Species: {{ animal.species }}   Name: {{ animal.name }}   Date of Birth: {{ checkIfEmpty(animal.birthDate) }}
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    data () {
        return {
            listOfAnimals: [
                {species: 'mammal', name: 'horse', birthDate: ''},
                {species: 'insect', name: 'bettle', birthDate: '09.12.2004.'},
                {species: 'fish', name: 'salmon', birthDate: '04.01.2001.'},
                {species: 'mammal', name: 'monkey', birthDate: '10.03.2013.'},
                {species: 'rodent', name: 'mouse', birthDate: '01.01.2010.'}
            ]
        }
    },

    methods: {
        checkIfEmpty (date) {
            if (!date) {
                return 'Nepoznat';
            } else {
                return date;
            }
        }
    }
}
</script>
