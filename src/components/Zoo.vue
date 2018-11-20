<template>

    <div class="container">
        <h2>Animals</h2>

        <!--FORMA ZA UNOS ZIVOTINJA-->
        <div class="row justify-content-md-center">
            <!--@submit.prevent="addAnimal" - metoda koja nam dodaje zivotinju-->
            <form @submit.prevent="addAnimal">
                <p class="text-muted">Animal Form</p>

                <div class="form-group row">
                    <label>Specie</label>
                    <input v-model="newAnimal.species" class="form-control" type="text" placeholder="Enter specie">
                </div>

                <div class="form-group row">
                    <label>Animal Name</label>
                    <input v-model="newAnimal.name" class="form-control" type="text" placeholder="Enter name">
                </div>

                <div class="form-group row">
                    <label>Date of Birth</label>
                    <input v-model="newAnimal.dateOfBirth" class="form-control" type="text" placeholder="Enter date of birth">
                </div>

                <div class="form-group row">
                    <label>Sectors</label>
                    <select v-model="newAnimal.sector" class="form-control">
                        <option v-for="(sector, index) in sectors" :key="index" v-bind:value="sector">
                            {{ sector.name }}
                        </option>
                    </select>
                </div>

                <button type="submit" class="btn btn-primary">Add new animal</button>
            </form>
        </div>





        <!--TABELA SA ZIVOTINJAMA-->
        <table class="table">
            <thead>
                <tr>
                    <th scope="col">Species</th>
                    <th scope="col">Name</th>
                    <th scope="col">Date of Birth</th>
                    <th scope="col">Sector</th>
                    <th scope="col">Remove Animal</th>
                    <th scope="col">Move to top</th>
                    
                </tr>
            </thead>
            <tbody>
                <tr v-for="(animal, index) in animals" :key="index"> <!--pomocu for petlje prolazimo kroz niz i ispisujemo u tabeli zivotinje-->
                    <td>{{animal.species}}</td>
                    <td>{{animal.name}}</td>

                    <!--Ako zivotinja nema datum rodjenja napisati da je datum nepoznat-->
                    <td>{{animal.dateOfBirth ? animal.dateOfBirth : 'Unknown'}}</td>

                    <td>{{animal.sector.name}}</td>

                    <td>
                        <!--na klik dugmeta se pokrece akcija removeAnimal(animal), koja brise zivotinju, ta metoda se nalazi u export default-->
                        <button @click="removeAnimal(animal)">Remove</button>
                    </td>

                    <td>
                        <!--Datu zivotinju da mozemo na klik dugmeta da pomerimo na vrh liste-->
                        <button type="submit" @click="moveToTop(animal)">Move to top</button>
                    </td>
                </tr>
            </tbody>
        </table>



    </div>
    
</template>


<script>

//sektori za zivotinje
const sectors = [
    {name:'Water-animals', surface:'Water'},
    {name:'Fawl', surface:'Kages'},
    {name:'Predators', surface:'Kages'}
];

export default {
    //data fnc vraca neki objekat
    data() {
        return {
            //nova zivotinja
            newAnimal: {
                species: '',
                name: '',
                dateOfBirth: ''
            },

            //niz animals koji sadrzi objekte
            animals: [
                {species: 'pas', name: 'Maza', dateOfBirth: '22.10.2017', sector:sectors[2]},
                {species: 'macka', name: 'Mitar', dateOfBirth: '15.9.2018', sector:sectors[2]},
                {species: 'slon', name: 'Dambo', dateOfBirth: '5.3.2017', sector:sectors[1]},
                {species: 'riba', name: 'Nemo', dateOfBirth: '11.11.2011', sector:sectors[0]},
                {species: 'zaba', name: 'Sima', dateOfBirth: '1.2.2001', sector:sectors[0]},
                {species: 'zmija', name: 'Sladja', dateOfBirth: '', sector:sectors[2]}
            ],

            //sektori zivotinja
            sectors:sectors, //moramo ispisati da je sektor:sektor jer nam je sektor iznad export data
        }
    },

    //funkcije
    methods: {
        //obrisi zivotinju, fnc
        removeAnimal(animal) {
            let index = this.animals.indexOf(animal); //u let index stavljamo index svake zivotinje
            this.animals.splice(index, 1); //splice - brisemo sa index pozicije 1 element;
        },

        //
        moveToTop(animal) {
            this.removeAnimal(animal); //iskoristili smo metodu removeAnimal() koja nam sklanja neku zivotinju, a posto nam je ne brise bez fnc splice() onda smo je pomerili u sledecoj liniji na pocetak niza
            this.animals.unshift(animal);//i nad nizom zivotinja smo pozvali fnc unshift() koja nam pomera zivotinju na prvo mesto u listi
        },

        //dodavanje zivotinje
        addAnimal() {
            this.animals.push(this.newAnimal);
            this.newAnimal = {};
        }
    }
    
}
</script>
