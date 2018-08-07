<template>
  <div class="hello">
    <h1>Animal List</h1>
   <table>
        <tr>
            <th>Vrsta</th>
            <th>Ime</th> 
            <th>Datum rodjenja</th>
            <th></th>
            <th></th>
        </tr>
        <tr v-for='(animal,index) in animals' :key='index'>
            <td>{{animal.vrsta}}</td>
            <td>{{animal.ime}}</td> 
            <td v-if="animal.datum_rodjenja != ''">{{animal.datum_rodjenja}}</td> 
            <td v-else>Nepoznato</td> 
            <td><button @click='removeAnimal(animal)'>Remove</button></td>
            <td><button @click='moveToTop(animal)'>Move to top</button></td>
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
                datum_rodjenja: ''
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
                datum_rodjenja: ''
            },
            {
                vrsta:'papkar',
                ime: 'Kamila',
                datum_rodjenja: '3. maj 2000'
            },
        ]
    }
  },

  methods: {
      removeAnimal(animal) {
          let animalIndex = this.animals.indexOf(animal);
          this.animals.splice(animalIndex, 1)
      },
      moveToTop(animal) {
          let animalIndex = this.animals.indexOf(animal);
          this.animals.splice(animalIndex, 1)
          this.animals.splice(0, 0, animal)
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
