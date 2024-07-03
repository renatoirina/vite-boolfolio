<script>
// Importo il modulo axios per effettuare richieste HTTP
import axios from "axios";
// Importo il nuovo componente ProjectCard
import ProjectCard from "./components/ProjectCard.vue";

export default {
  components: {
    ProjectCard
  },
  data() {
    return {
      // Inizializzo l'array projects vuoto
      projects: [],
    };
  },

  // Questo metodo viene eseguito al momento della creazione del componente
  created() {

    // Effettuo una richiesta GET all'API per ottenere i progetti
    axios.get("http://127.0.0.1:8000/api/projects").then((resp) => {
      
      // Assegno i dati ricevuti alla variabile projects
      this.projects = resp.data.results;
    });
  }
};
</script>

<template>
  <div class="container my-5">
    <div class="row">
      <!-- Uso il componente ProjectCard per iterare su ogni progetto -->
      <ProjectCard v-for="project in projects" :key="project.id" :project="project" />
    </div>
  </div>
</template>

<style>
/* Puoi aggiungere ulteriori stili globali qui */
</style>
