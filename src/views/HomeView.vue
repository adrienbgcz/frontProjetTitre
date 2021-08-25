<template>
  <div>
    <BannerWithoutButtonTemplate />
    <h1>Liste des logements</h1>
    <div class="allCards">
      <HousingCardTemplate v-for="housing in housingList" :key="housing.id" :housingProps="housing"/>
    </div>
  </div>
  
</template>

<script>
import BannerWithoutButtonTemplate from "../components/BannerWithoutButtonTemplate.vue"
import HousingCardTemplate from "../components/HousingCardTemplate.vue"

export default {
  name: "HomeView",
  components : {
    BannerWithoutButtonTemplate,
    HousingCardTemplate
  },
  methods: {
    getData: async function() {
      try {
        const response = await fetch("http://localhost:9003/logements")
        const data = await response.json()
        console.log(data)
        this.housingList = data
      } catch(error) {
        console.log(error)
      }
    }
  },
  created: function() {
    this.getData()
  },
  data: function() {
    return {
      housingList: []
    }

  }
}
</script>

<style scoped>
h1 {
    text-align: center;
    font-family: lato;
    color: #0B295D;
    margin-top: 100px;
    margin-bottom: 50px;
    font-size: 30px;
}

.allCards {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
}



</style>
