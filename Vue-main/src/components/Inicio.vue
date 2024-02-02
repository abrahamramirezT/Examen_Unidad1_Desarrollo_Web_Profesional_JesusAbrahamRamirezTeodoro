<template>
  <div>
    <b-container>
      <b-breadcrumb :items="items"></b-breadcrumb>
    </b-container>

    <h1>Vehiculos</h1>
    
    <b-link :to="{ name: 'form' }">
      <b-button variant="success"  class="btn-inicio">Formulario</b-button>
    </b-link>
    <b-link :to="{ name: 'pagination' }">
      <b-button variant="success" class="btn-inicio"> Paginacion </b-button>
    </b-link>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          text: "Inicio",
          active: true,
        },
      ],
    };
  },
};
</script>
<style>
.btn-inicio {
  padding: 20px;
  margin: 10px;
}

.btn-inicio a {
  text-decoration: none;
  color: white;
}
</style>
