<template>
  <section>
    <div class="reservation">
      <p>Réservation effectuée par : {{reservationProps.utilisateur.prenom}} {{reservationProps.utilisateur.nom}}</p>
      <p>Vous avez réservé le logement "{{housingProps.titre}}" du {{reservationProps.date_arrivee}} au {{reservationProps.date_depart}}</p>
      <p>Votre numero de reservation est le {{reservationProps.numero_reservation}}</p>
    </div>
  </section>
</template>

<script>
export default {
    name: "ReservationValidatedTemplate",
    props: ["reservationProps", "housingProps"]
    

}
</script>

<style scoped>
.reservation {
    margin-top : 100px;
    width: 500px;
    border: solid;
    box-shadow: 10px 10px 23px -7px rgba(0,0,0,0.66);
    padding: 20px;
    border-width : 1px;
    border-color: #0B295D;
}

section {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 1000px;
    margin: auto;
    font-family: lato;
    color: #0B295D;
}

@media screen and (max-width: 650px) {
  .reservation {
      width: 95%
  }
}

</style>