<template>
  <div class="vente-form">
    <h3>Enregistrer une Vente</h3>
    <form @submit.prevent="enregistrerVente">
      <div class="form-group">
        <label for="reference">Référence</label>
        <input type="text" class="form-control" id="reference" v-model="vente.reference" required/>
      </div>
      <div class="form-group">
        <label for="designation">Désignation</label>
        <input type="text" class="form-control" id="designation" v-model="vente.designation" required/>
      </div>
      <div class="form-group">
        <label for="quantite">Quantité Vendue</label>
        <input type="number" class="form-control" id="quantite"
          v-model.number="vente.quantite" required/>
      </div>
      <div class="form-group">
        <label for="prix">Prix de Vente</label>
        <input type="number" class="form-control" id="prix" v-model.number="vente.prix" required/>
      </div>
      <button type="submit" class="btn btn-primary mt-3">Enregistrer</button>
      <div v-if="messageErreur" class="alert alert-danger mt-3">
        {{ messageErreur }}
      </div>
    </form>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  setup(props, { emit }) {
    const vente = ref({
      reference: '',
      designation: '',
      quantite: null,
      prix: null
    });

    const messageErreur = ref('');

    const enregistrerVente = () => {
      if (
        !vente.value.reference ||
        !vente.value.designation ||
        vente.value.quantite <= 0 ||
        vente.value.prix <= 0
      ) {
        messageErreur.value = "Veuillez remplir tous les champs correctement.";
      } else {
        emit('vente-enregistree', { ...vente.value });
        vente.value = {
          reference: '',
          designation: '',
          quantite: null,
          prix: null
        };
        messageErreur.value = '';
      }
    };

    return {
      vente,
      messageErreur,
      enregistrerVente
    };
  }
};
</script>

<style scoped>
.vente-form {
  max-width: 500px;
  margin: auto;
}
</style>
