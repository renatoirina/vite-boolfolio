<script>
// Importa il modulo axios per effettuare le richieste HTTP
import axios from "axios";

export default {
  data() {
    return {
      // Inizializza l'array projects vuoto
      projects: [],
    };
  },

  // Metodo eseguito al momento della creazione del componente
  created() {
    // Effettua una richiesta GET all'API per ottenere i progetti
    axios.get("http://127.0.0.1:8000/api/projects").then((resp) => {
      // Assegna i dati ricevuti alla variabile projects
      this.projects = resp.data.results;
    });
  }
};
</script>

<template>
  <div class="container">
    <div class="row">
      <!-- Ciclo v-for per iterare su ogni progetto -->
      <div class="col-3" v-for="project in projects" :key="project.id">
        <div class="card">
          <div class="card-body">
            <!-- Visualizzo il titolo del progetto -->
            <h1>{{ project.title }}</h1>
            <!-- Visualizzo la descrizione del progetto -->
            <p>{{ project.description }}</p>
            <!-- Visualizzo il nome del linguaggio del progetto -->
            <p><strong>Language:</strong> {{ project.type.name }}</p>
            <!-- Visualizzo il campo del progetto -->
            <p><strong>Field:</strong> {{ project.type.field }}</p>
            <!-- Sezione per visualizzare le tecnologie utilizzate nel progetto -->
            <div>
              <strong>Technologies:</strong>
              <ul>
                <!-- Ciclo v-for per iterare su ogni tecnologia associata al progetto -->
                <li v-for="tech in project.technologies" :key="tech.id">
                  {{ tech.name }}
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
/* Stile per aggiungere spazio tra le card */
.card {
  margin-bottom: 20px;
}
</style>
