<template>
    <div>
        <form @submit.prevent="addAnimal">
            <div>
                <label for="species">Species</label>
                <input type="text" id="species" v-model="newAnimal.species" required>
            </div>
            <div>
                <label for="name">Name</label>
                <input type="text" id="name" v-model="newAnimal.name" required>
            </div>
            <div>
                <label for="birthDate">Date of Birth</label>
                <input type="date" id="birthDate" v-model="newAnimal.birthDate">
            </div>

            <select name="sector" id="sector" v-model="newAnimal.sector" required>
                <option :value=sector v-for="(sector, index) in sectors" :key=index>{{ sector }}</option>
            </select>

            <div>
                <button type="submit">Add Animal</button>
            </div>
        </form>

        <ul>
            <li v-for="(animal, index) in listOfAnimals" :key=index>
                Species: {{ animal.species }}   Name: {{ animal.name }}   Date of Birth: {{ checkIfEmpty(animal.birthDate) }}   Sector: {{ animal.sector }}
                <button @click="removeAnimal(index)">Remove</button>
                <button @click="moveToTop(index)">Move to Top</button>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    data () {
        return {
            newAnimal: {
                species: '',
                name: '',
                birthDate: '',
                sector: ''
            },

            listOfAnimals: [
                {species: 'Horse', name: 'Konjo', birthDate: '', sector: 'Mammals'},
                {species: 'Fox', name: 'Lijo', birthDate: '09.12.2004.', sector: 'Mammals'},
                {species: 'Lynx', name: 'Riso', birthDate: '04.01.2001.', sector: 'Mammals'},
                {species: 'Bear', name: 'Grizo', birthDate: '10.03.2013.', sector: 'Mammals'},
                {species: 'Monkey', name: 'Majmo', birthDate: '01.01.2010.', sector: 'Mammals'}
            ],

            sectors: [ 'Birds' , 'Mammals', 'Fishes']
        }
    },

    methods: {
        checkIfEmpty (date) {
            if (!date) {
                return 'Nepoznat';
            } else {
                return date;
            }
        },

        removeAnimal (index) {
            this.listOfAnimals.splice(index, 1);
        },

        moveToTop (index) {
            let tempAnimal = this.listOfAnimals.splice(index, 1);
            this.listOfAnimals = [...tempAnimal, ...this.listOfAnimals];
        },

        addAnimal () {
            this.listOfAnimals.push({...this.newAnimal});
            this.newAnimal = {
                species: '',
                name: '',
                birthDate: ''
            }
        }
    }
}
</script>
