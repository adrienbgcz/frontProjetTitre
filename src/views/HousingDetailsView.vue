<template>

<div>
    <BannerWithButtonTemplate />
    <HousingDetailsTemplate :housingProps="housing" />
</div>

  
</template>

<script>
import BannerWithButtonTemplate from "../components/BannerWithButtonTemplate.vue"
import HousingDetailsTemplate from '../components/HousingDetailsTemplate.vue'

export default {
    name: "HousingDetailsView",
    components : {
        BannerWithButtonTemplate,
        HousingDetailsTemplate
    },
    methods: {
    getData: async function() {
      try {
        const response = await fetch(`http://localhost:9003/logements/${this.$route.params.housingId}`)
        const data = await response.json()
        console.log(data[0])
        this.housing = data[0]
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
      housing: {}
    }

  }
}


</script>

<style>

</style>