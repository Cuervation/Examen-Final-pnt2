<template >

  <section class="src-componentes-formulario">
    <h4>Conversor a dólares</h4>

      <label for="importe">Ingrese el monto $  </label>
      <input 
        type="number" 
        id="monto" 
        class="form-control" 
        autocomplete="off"
        v-model.number="formData.monto" 
        name="monto"
        @change=  actualizar()        
        required
      >

      <br>
      <br>

      <label for="dolar">Valor del dolar en $  </label>
      <input 
        type="number" 
        id="monto" 
        class="form-control" 
        autocomplete="off"
        v-model.number="formData.dolar"         
        name="monto"
        @change=  actualizar()        
        required
      >  --
      <label for="actualizacion">Actualización</label>
      <input id="actualizacion" type="checkbox">
      <br>
      <br>    
    <div>Valor convertido en USD {{ this.resultado }}</div>         



    <p>Respuestas 1)C,2)B,3)C,4)A,5)B</p>         
  </section>

</template>

<script >

  export default  {
    name: 'src-componentes-formulario',
    props: [],
    mounted () {
      
    },
    data () {
      return {
        dolares :[],
        url : 'https://www.dolarsi.com/api/api.php?type=valoresprincipales',
        formData: this.getInitialData(),
        resultado : 0
      }
    },
    methods: {
        async getUsuariosFetchAsync() {                
          try {
            let response = await fetch(this.url)        
            let respuesta = await response.json();       
            this.dolares = respuesta;
          }
          catch(error) {
            console.log(error);
          }          

            
        },        
      actualizar(){
          let datos = { ...this.formData }
          this.resultado = datos.monto * datos.dolar          
      },
    getInitialData() {
      return {
        monto: 0,
        dolar: 310, 
               
      }
    }, 
    },
    computed: {

    }

}


</script>

<style scoped lang="css">
  .src-componentes-formulario {

  }
</style>
