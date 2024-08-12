<template>
    <div class="container mt-5">
      <h2>Enregistrement des Ventes</h2>
      <form @submit.prevent="enregistrerVente">
        <div class="form-group">
          <label for="reference">Référence</label>
          <input type="text" id="reference" v-model="vente.reference" class="form-control" required>
        </div>
  
        <div class="form-group">
          <label for="designation">Désignation</label>
          <input type="text" id="designation" v-model="vente.designation" class="form-control" required>
        </div>
  
        <div class="form-group">
          <label for="quantite">Quantité</label>
          <input type="number" id="quantite" v-model="vente.quantite" class="form-control" required>
        </div>
  
        <div class="form-group">
          <label for="prix">Prix de Vente</label>
          <input type="number" id="prix" v-model="vente.prix" class="form-control" required>
        </div>
  
        <button class="btn btn-primary mt-3" type="submit">Enregistrer Vente</button>
      </form>
  
      <TableauVentes :ventes="ventes"/>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  import TableauVentes from './components/TableauVentes.vue';
  
 

      const vente = ref({
        reference: '',
        designation: '',
        quantite: 0,
        prix: 0
      });
  
      const ventes = ref([]);
  
      const enregistrerVente = () => {
        ventes.value.push({ ...vente.value });
        vente.value.reference = '';
        vente.value.designation = '';
        vente.value.quantite = 0;
        vente.value.prix = 0;
      };

  </script>
  