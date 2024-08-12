<template>
  <div class="vente-table mt-5">
    <h3>Ventes Enregistrées</h3>
    <table class="table table-bordered">
      <thead>
        <tr>
          <th>Référence</th>
          <th>Désignation</th>
          <th>Quantité</th>
          <th>Prix</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(vente, index) in ventes" :key="index">
          <td>{{ vente.reference }}</td>
          <td>{{ vente.designation }}</td>
          <td>{{ vente.quantite }}</td>
          <td>{{ vente.prix.toFixed(2) }} MRU</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
  props: {
    ventes: {
      type: Array,
      required: true
    }
  }
});
</script>
