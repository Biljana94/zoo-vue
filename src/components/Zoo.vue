<template>

    <div class="container">
        <h2>Animals</h2>
        <table class="table">
            <thead>
                <tr>
                    <th scope="col">Species</th>
                    <th scope="col">Name</th>
                    <th scope="col">Date of Birth</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(animal, index) in animals" :key="index"> <!--pomocu for petlje prolazimo kroz niz i ispisujemo u tabeli zivotinje-->
                    <td>{{animal.species}}</td>
                    <td>{{animal.name}}</td>
                    <!--Ako zivotinja nema datum rodjenja napisati da je datum nepoznat-->
                    <td>{{animal.dateOfBirth == '' ? 'Unknown' : animal.dateOfBirth}}</td>
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
    
}
</script>
