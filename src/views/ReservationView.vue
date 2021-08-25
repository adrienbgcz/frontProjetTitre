<template>
  <div>
    <BannerWithButtonTemplate />
    <ReservationFormTemplate
      v-if="isValidated == false"
      :housingProps="housing"
      @send-data-event="displayAndPostReservation"
    />
    <ValidatedReservationTemplate v-if="isValidated == true" :reservationProps="this.reservation" :housingProps="this.housing"/>

  </div>
</template>

<script>
import BannerWithButtonTemplate from "../components/BannerWithButtonTemplate.vue";
import ReservationFormTemplate from "../components/ReservationFormTemplate.vue";
import ValidatedReservationTemplate from "../components/ValidatedReservationTemplate.vue"

export default {
  name: "ReservationView",
  components: {
    BannerWithButtonTemplate,
    ReservationFormTemplate,
    ValidatedReservationTemplate
  },
  methods: {
    getData: async function () {
      try {
        const response = await fetch(
          `http://localhost:9003/logements/${this.$route.params.housingId}`
        );
        const data = await response.json();
        console.log(data[0]);
        this.housing = data[0];
      } catch (error) {
        console.log(error);
      }
    },
    displayAndPostReservation: function (reservation) {
      console.log(reservation);
      this.reservation = reservation;
      this.isValidated = true
    },
  },
  created: function () {
    this.getData();
  },
  data: function () {
    return {
      housing: {},
      isValidated : false,
      reservation : {}
    };
  },

  
};
</script>


<style scoped>
</style>