<template>
  <div class="hello">
    <h1>Animal List</h1>
    
    <form @submit.prevent>
        <label>Vrsta: </label><br>
        <input type="text" v-model='newAnimal.vrsta'>
        <br>
        <label>Ime: </label><br>
        <input type="text" v-model='newAnimal.ime'>
        <br>
         <label>Datum rodjenja: </label><br>
        <input type="text" v-model='newAnimal.datum_rodjenja'>
        <br>     
        <br>
        <select v-model="newAnimal.sector" v-bind:value=null>
          <option v-for='(sector, index) in sectors' :key='index' v-bind:value='sector'>{{sector.name}}</option>
        </select>
        <br>
        <br>
        <button @click='addAnimal'>Add Animal</button>
    </form>

    <table>
        <tr>
            <th>Vrsta</th>
            <th>Ime</th> 
            <th>Datum rodjenja</th>
            <th>Sector:</th>
            <th></th>
            <th></th>
        </tr>
        <tr v-bind:class="{backgroundColor: isActive(animal)}" v-for='(animal,index) in animals' :key='index'>
            <td>{{animal.vrsta}}</td>
            <td>{{animal.ime}}</td> 
            <td >{{animal.datum_rodjenja ? animal.datum_rodjenja : 'Nepoznato'}}</td> 
            <td>{{animal.sector.name}}</td>

            <td><button @click='removeAnimal(animal)'>Remove</button></td>
            <td><button @click='moveToTop(animal)'>Move to top</button></td>
            <td><button @click='toggle(animal)'>Toggle background</button></td>
        </tr>
    </table>
 
  
        <h1>Sectors </h1>
        <table>
            <tr>
                <th>Sectors</th>
                <th></th>
            </tr>
            <tr v-for='(sector, index) in sectors' :key='index'>
                <td>{{sector.name}}</td>
                <td><button @click='showAnimals(sector)'>Show animals</button></td>
            </tr>
        </table>
  </div>

</template>

<script>
const sectors = [{ name: "kavez" }, { name: "bazen" }, { name: "livada" }];

export default {
  name: "AnimalList",
  data() {
    return {
      sectors: sectors,

      animals: [
        {
          vrsta: "predator",
          ime: "Tigar",
          datum_rodjenja: "",
          sector: sectors[0],
          background: true
        },
        {
          vrsta: "predator",
          ime: "Panter",
          datum_rodjenja: "5. jun 2005",
          sector: sectors[0],
          background: true
        },
        {
          vrsta: "zver",
          ime: "Medved",
          datum_rodjenja: "15. april 1995",
          sector: sectors[0],
          background: false
        },
        {
          vrsta: "vodozemci",
          ime: "Foka",
          datum_rodjenja: "",
          sector: sectors[1],
          background: true
        },
        {
          vrsta: "papkar",
          ime: "Kamila",
          datum_rodjenja: "3. maj 2000",
          sector: sectors[2],
          background: true
        }
      ],
      newAnimal: {
        background: true
      }
    };
  },

  methods: {
    removeAnimal(animal) {
      let animalIndex = this.animals.indexOf(animal);
      this.animals.splice(animalIndex, 1);
    },
    moveToTop(animal) {
      this.removeAnimal(animal);
      this.animals.unshift(animal);
    },
    addAnimal() {
      //if sector is not selected add sector object to newAnimal with value "nepoznato"
      if (!this.newAnimal.sector) {
        this.newAnimal.sector = { name: "Nepoznato" };
      }
      this.animals.push(this.newAnimal);
      this.newAnimal = {
        background: true
      };
    },
    showAnimals(sector) {
      var list = [];
      this.animals.forEach(animal => {
        if (animal.sector === sector) {
          list.push(`${animal.ime} ${animal.vrsta}`);
        }
      });
      alert(list);
    },

    isActive(animal) {
      return animal.background;
    },

    toggle(animal) {
      animal.background = !animal.background;
    }
  }
};
</script>


<style scoped>
table {
  margin: 0 auto;
}
th,
td {
  padding: 15px;
  text-align: left;
}

input {
  width: 60%;
  padding: 12px 10px;
  margin: 8px 0;
  box-sizing: border-box;
}

.backgroundColor {
  background: lightgreen;
}
</style>
