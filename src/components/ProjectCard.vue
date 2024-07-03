<script>
export default {
  props: {
    project: {
      type: Object,
      required: true
    }
  }
}
</script>

<template>
  <div class="col-lg-4 col-md-6 mb-4">
    <div class="card h-100 shadow-sm">
      <div class="card-body d-flex flex-column">
        <!-- Visualizzo il titolo del progetto -->
        <h5 class="card-title">{{ project.title }}</h5>

        <!-- Visualizzo la descrizione del progetto -->
        <p class="card-text">{{ project.description }}</p>

        <!-- Visualizzo il nome del linguaggio del progetto -->
        <p><strong>Language:</strong> {{ project.type.name }}</p>

        <!-- Visualizzo il campo del progetto -->
        <p><strong>Field:</strong> {{ project.type.field }}</p>

        <!-- Sezione per visualizzare le tecnologie utilizzate nel progetto -->
        <div class="mt-auto">
          <strong>Technologies:</strong>
          <ul class="list-inline">

            <!-- Uso un ciclo v-for per iterare su ogni tecnologia associata al progetto -->
            <li class="list-inline-item badge badge-primary" v-for="tech in project.technologies" :key="tech.id">
              {{ tech.name }}
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
/* Stile per aggiungere spazio tra le card e renderle esteticamente migliori */
.card {
  margin-bottom: 20px;
  border-radius: 10px;
  overflow: hidden;
}

.card-title {
  font-size: 1.25rem;
  font-weight: bold;
}

.card-text {
  flex-grow: 1;
  font-size: 1rem;
}

.list-inline-item {
  margin-right: 10px;
}

.badge-primary {
  background-color: #007bff;
  color: white;
  padding: 5px 10px;
  border-radius: 20px;
}
</style>
