<template>
    <div class="container">
        <h2>Produits du catalogue</h2>
        <div class="catalogue">
            <span v-for="produits in catalogue" :key="produits.produit">
                {{ produits.produit }}
            </span>
        </div>
        <h2>Inventaire des placards</h2>
        <div class="placards" v-for="(produitsPlacards, index) in produitsPlacards" :key="produitsPlacards.produit">
            <label>
                {{ produitsPlacards.produit }}
                <input type="checkbox" v-model="produitsPlacards.selected"  :value="produitsPlacards.produit" @click="(this.produitsPlacards[index].selected) = !(this.produitsPlacards[index].selected)">
            </label>  
        </div>
        <h2>Liste des courses</h2>
        <div class="courses">
            <span class="produit-courses" v-for="produitsAcheter in listeCourses" :key="produitsAcheter.produit">
                {{ !produitsAcheter.selected ? produitsAcheter.produit : "" }}
            </span>
        </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      catalogue: [
        {produit: "Lait", selected: false},
        {produit: "Beurre", selected: false},
        {produit: "Confiture", selected: false},
        {produit: "Légumes", selected: false},
        {produit: "Café", selected: false},
        {produit: "Viande", selected: false},
        {produit: "Desserts", selected: false},
        {produit: "Surgelés", selected: false},
        {produit: "Produits d'entretien", selected: false},
      ],
      listeCourses: [],
      produitsPlacards: [],
    }
  },
  created: function () {
    this.produitsPlacards = Object.assign(this.produitsPlacards, this.catalogue);
    this.listeCourses = Object.assign(this.listeCourses, this.produitsPlacards);
  }
}
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
    font-size: 14px;
    /* border: 1px solid red; */
}
.container {
    display: flex;
    flex-direction: column;
    align-items: center;
}
h2 {
    padding: 1rem;
    margin: 1rem auto;
    border: 2px solid #000
}
.catalogue, .courses {
    display: flex;
    flex-direction: column;
}
.catalogue span {
    padding: .4rem;
    margin: .2rem;
    border: 1px solid #b8b7b7;
}
.placards {
    display: flex;
}
.courses span {
    font-weight: bolder;
}
label {
    display: flex;
    justify-content: space-between;
    width: 160px;
}
</style>
