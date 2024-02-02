<template>
    
    <div>
        
      <b-form @submit="onSubmit" @reset="onReset" v-if="show">
        
        <b-container>
      <b-breadcrumb :items="items"></b-breadcrumb>
    </b-container>  
        <b-form-group
          id="input-group-1"
          label="Marca:"
          label-for="input-1">
          <b-form-input
            id="input-1"
            v-model="form.brand"
            placeholder="Ingresa la marca del automovil"
            required
          ></b-form-input>
        </b-form-group>
  
        <b-form-group id="input-group-2" label="Modelo:" label-for="input-2">
          <b-form-input
            id="input-2"
            v-model="form.model"
            placeholder="Ingresa el Modelo del automovil"
            required
          ></b-form-input>
        </b-form-group>

        <b-form-group id="input-group-4" label="Numero de Serie:" label-for="input-4">
          <b-form-input
            id="input-4"
            v-model="form.serie"
            placeholder="Ingresa el Numero de Serie del automovil"
            required
          ></b-form-input>
        </b-form-group>


        <b-form-group id="input-group-3" label="Año de Fabricacion:" label-for="input-3">
          <b-form-input
            id="input-3"
            v-model="form.year"
            placeholder="Ingresa el año de farbricacion del automovil"
            required
          ></b-form-input>
        </b-form-group>


       
        <b-button type="submit" variant="primary">Submit</b-button>
        <b-button type="reset" variant="danger">Reset</b-button>
      </b-form>
    
    </div>
  </template>
  
  <script>

  import axios from "axios"
    export default {
      data() {
        return {
          form: {
            brand: '',
            model: '',
            serie:'',
            year:''
          },
          
          show: true,
          items: [
        {
          text: "Inicio",
          to: { name: "inicio" },
        },
        {
          text: "Formulario",
          active: true,
        },
      ],
        }
      },
      
      methods: {

        onSubmit(event) {
 
          event.preventDefault()
          alert(JSON.stringify(this.form))
          axios.post('http://localhost:8080/api/vehiculos', {
        brand: this.form.brand,
        model: this.form.model,
        serie:this.form.serie,
        year:this.form.year
  })
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
        },

        



        validateMarca() {
      const regex = /^[A-Za-z0-9]+$/;
      return regex.test(this.vehicle.brand);
      if(!regex.test(brand)){
        this.addError("marca", "La marca no es válida");
      }

    },
    validateModelo() {
      const regex = /^[A-Za-z0-9]+$/;
      return regex.test(this.vehicle.modelo);
    },
    validateYear() {
      const currentYear = new Date().getFullYear();
      return this.vehicle.anio <= currentYear;
    },
    validateNumeroSerie() {
      const serialRegex = /^[A-Z]{4}000-00[A-Z]{2}$/;
      return serialRegex.test(this.vehicle.numeroSerie);
    },
   

        onReset(event) {
          event.preventDefault()
          // Reset our form values
          this.form.email = ''
          this.form.name = ''
          this.form.food = null
          this.form.checked = []
          // Trick to reset/clear native browser form validation state
          this.show = false
          this.$nextTick(() => {
            this.show = true
          })
        }
      }
    }
  </script>
  