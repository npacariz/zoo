<template>
  <div class="hello">
    <h1>Animal List</h1>
   <table>
        <tr>
            <th>Vrsta</th>
            <th>Ime</th> 
            <th>Datum rodjenja</th>
        </tr>
        <tr v-for='(animal,index) in animals' :key='index'>
            <td>{{animal.vrsta}}</td>
            <td>{{animal.ime}}</td> 
            <td>{{animal. datum_rodjenja}}</td> 
        </tr>
</table>
  </div>
</template>

<script>
export default {
  name: 'AnimalList',
  
  data() {
    return {
        animals: [
            {
                vrsta:'predator',
                ime: 'Tigar',
                datum_rodjenja: '5. jun 2015'
            },
            {
                vrsta:'Predator',
                ime: 'Panter',
                datum_rodjenja: '5. jun 2005'
            },
            {
                vrsta:'zver',
                ime: 'Medved',
                datum_rodjenja: '15. april 1995'
            },
            {
                vrsta:'vodeni sisar',
                ime: 'Foka',
                datum_rodjenja: '5. jun 2010'
            },
            {
                vrsta:'papkar',
                ime: 'Kamila',
                datum_rodjenja: '3. maj 2000'
            },
        ]
    }
  }
}
</script>


<style scoped>
table {
    margin: 0 auto;
}
th, td {
    padding: 15px;
    text-align: left;
}
</style>
