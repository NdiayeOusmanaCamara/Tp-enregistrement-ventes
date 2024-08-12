<template>
  <div id="app" class="container mt-5">
    <VenteForm @vente-enregistree="ajouterVente" />
    <VenteTable :ventes="ventes" />
  </div>
</template>

<script>
import { ref } from 'vue';
import VenteForm from './components/VenteForm.vue';
import VenteTable from './components/VenteTable.vue';

export default {
  components: {
    VenteForm,
    VenteTable
  },
  setup() {
    const ventes = ref([]);

    const ajouterVente = (vente) => {
      ventes.value.push(vente);
    };

    return {
      ventes,
      ajouterVente
    };
  }
};
</script>
