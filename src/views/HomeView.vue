<template>
    <v-row cols="15" md="3" class="my-6">
      <v-col v-for="curso in cursos" :key="curso.id" class="d-flex flex-wrap my-6"  >
        <Card
        :cursoImagen="curso.img"
        :courseName="curso.nombre"
        :cost="curso.costo"
        :time="curso.duracion"
        :disponible="curso.cupos"
        :finalizado="curso.completado"
        :date="curso.fecha_registro"
        :detalles="curso.descripcion"
        >
      </Card>
      </v-col>
    </v-row>
</template>

<script>
import {mapState} from 'vuex'
import Card from '@/components/Card.vue';



  export default {
    name: 'Home-view',

    components: {
      Card
     
    },
    computed:{
    ...mapState(['cursos'])
  },
  }
</script>
