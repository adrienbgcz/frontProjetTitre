<template>
    <section>

        <h1>Formulaire de réservation pour <span>{{housingProps.titre}}</span></h1>

        <form @submit.prevent="sendDataEvent" action="">
                <div class="inputAndLabel">
                    <label for="input-nom">Nom</label>
                    <input v-model="reservation.utilisateur.nom" type="text" name="nom" id="input-nom" required>
                </div>

                <div class="inputAndLabel">
                    <label for = "input-prenom">Prénom</label>
                    <input v-model="reservation.utilisateur.prenom" type="text" name="prenom" id="input-prenom" >
                </div>

                <div class="inputAndLabel">
                    <label for = "input-pseudo">Pseudo</label>
                    <input v-model="reservation.utilisateur.pseudo" type="text" name="pseudo" id="input-pseudo" >
                </div>

                <div class="inputAndLabel">
                    <label for = "input-numero">Numéro de salarié</label>
                    <input v-model="reservation.utilisateur.numero_salarie" type="text" name="numero" id="input-numero" >
                </div>

                <div class="inputAndLabel">
                    <label for = "input-date-arrivee">Date d'arrivée</label>
                    <input v-model="reservation.date_arrivee" class="inputDate" type="date" name="numero" id="input-date-arrivee"  >
                </div>

                <div class="inputAndLabel">
                    <label for = "input-date-depart">Date de départ</label>
                    <input v-model="reservation.date_depart" class="inputDate" type="date" name="numero" id="input-date-depart" >
                </div>
                
                <input class="reservationButton" type="submit" value="Réserver maintenant">

    
            </form>
    </section>
</template>

<script>
export default {
    name: "ReservationFormTemplate",
    props: ["housingProps"],
    data: function(){
        return {
            reservation : {
                numero_reservation: 9999,
                date_arrivee: "",
                date_depart: "",
                utilisateur: {
                    id: 3,
                    nom: "",
                    prenom: "",
                    pseudo: "",
                    numero_salarie: ""
                } 
            }
        }
    },
    methods: {
        sendDataEvent: function() {
            this.$emit("send-data-event", this.reservation)
        }
    }
}
</script>

<style scoped>
.inputAndLabel {
    display: flex;
    flex-direction: column;
    margin-bottom: 20px;
}


form {
    margin-top: 50px;
    width: 500px;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 50px;
    background-color:#c4fffc;
    border-radius: 10px;
    
}

input {
    width : 300px;
    height: 20px;
    margin-top: 10px;
}

.inputDate {
    font-family: lato;
    height: 25px;
}

.reservationButton {
    font-size: 16px;
    background-color: #D41418;
    color: white;
    height: 40px;
    width: 200px;
    margin-top: 30px;
    border-radius: 10px;
    border: none;
    display:flex;
    justify-content: center;
}

.reservationButton:hover {
    color: #D41418;
    background-color: white;
    border:solid;
    
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


h1 {
    font-family: lato;
    font-weight: normal;
    color: #0B295D;
    width: 600px;
    text-align: center;
    margin-top: 150px;
}

span {
    font-weight: 700;
}

.reservation {
    margin-top : 100px;
    width: 500px;
    border: solid;
    box-shadow: 10px 10px 23px -7px rgba(0,0,0,0.66);
    padding: 20px;
    border-width : 1px;
    border-color: #0B295D;
}

@media screen and (max-width: 1200px) {

h1 {
    width: 90%
}

section {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 100%;
    margin: auto;
    font-family: lato;
    color: #0B295D;
}



}
</style>