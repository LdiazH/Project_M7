<template>
 
     <v-col >
        <v-card width="400">
          <v-img
            height="300px"
            :src="cursoImagen">  
          </v-img>
          <v-card-text>
            <div class="font-weight-bold ml-8 mb-2">
                {{this.courseName}}
            </div>
            <div class="font-weight-bold ml-8 mb-2">
              Información
            </div>
            <v-timeline
            align-top
            dense>
          <v-timeline-item>
                <div>
                  <div class="font-weight-normal">
                    <strong>Costo:</strong>
                  </div>
                  <div>{{this.cost}}</div>
                </div>
                <div>
                  <div class="font-weight-normal">
                    <strong>Duracion</strong>
                  </div>
                  <div>{{this.time}}</div>
                </div>
              </v-timeline-item>
              <v-timeline-item>
                <div>
                  <div class="font-weight-normal">
                    <strong>Cupos</strong>
                  </div>
                  <div>{{this.disponible}}</div>
                </div>
                <div>
                  <div class="font-weight-normal">
                    <strong>Completado</strong>
                  </div>
                  <div>{{this.finalizado}}</div>
                </div>
              </v-timeline-item>
            <v-timeline-item>
                <div>
                  <div class="font-weight-normal">
                    <strong>Fecha de Registro</strong>
                  </div>
                  <div>{{this.date}}</div>
                </div>
                <div>
                  <div class="font-weight-normal">
                    <strong>Descripcion</strong>
                  </div>
                  <div>{{this.detalles}}</div>
                </div>
              </v-timeline-item>
            </v-timeline> 
          </v-card-text>
        </v-card>
      </v-col> 
  </template>
<script>
export default {
    name: 'component-card',
    props: {
       cursoImagen:{
            type:String,
            required:true
        },
        courseName:{
            type:String,
             required:true
         },
         cost:{
             type:Number,
             required:true
        },
         time:{
             type:String,
             required:true
         },
         disponible:{
             type:Number,
             required:true
         },
         date:{
            type:String,
             required:true
         },
         detalles:{
             type:String,
           required:true
         },
         finalizado:{
             type:Boolean,
             required:true
         },
     },
    data: () => ({
      
    }),
    // computed: {},
    //methods: {}
    // watch: {},
    // components: {},
    // mixins: [],
    // filters: {},
    // -- Lifecycle Methods
    // -- End Lifecycle Methods
}
</script>

<style scoped>
    
</style>