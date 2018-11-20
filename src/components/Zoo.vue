<template>

    <div class="container">
        <h2>Animals</h2>
        <table class="table">
            <thead>
                <tr>
                    <th scope="col">Species</th>
                    <th scope="col">Name</th>
                    <th scope="col">Date of Birth</th>
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

                    <td>
                        <!--na klik dugmeta se pokrece akcija removeAnimal(animal), koja brise zivotinju, ta metoda se nalazi u export default-->
                        <button @click="removeAnimal(animal)">Remove</button>
                    </td>

                    <td>
                        <!--Datu zivotinju da mozemo na klik dugmeta da pomerimo na vrh liste-->
                        <button @click="moveToTop(animal)">Move to top</button>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
    
</template>


<script>

export default {
    //data fnc vraca neki objekat
    data() {
        return {
            //niz animals koji sadrzi objekte
            animals: [
                {species: 'pas', name: 'Maza', dateOfBirth: '22.10.2017'},
                {species: 'macka', name: 'Mitar', dateOfBirth: '15.9.2018'},
                {species: 'slon', name: 'Dambo', dateOfBirth: '5.3.2017'},
                {species: 'riba', name: 'Nemo', dateOfBirth: '11.11.2011'},
                {species: 'zaba', name: 'Sima', dateOfBirth: '1.2.2001'},
                {species: 'zmija', name: 'Sladja', dateOfBirth: ''}
            ]
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
        }
    }
    
}
</script>
