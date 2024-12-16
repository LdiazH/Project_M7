<template>
  <div id="body">
  <v-row class="d-flex justify-center my-5"> 
    <v-btn depressed color="primary" @click="reRouteAdd">Agregar Curso</v-btn>
  </v-row>
    <div>
    <v-simple-table>
  <thead>
    <tr>
      <th scope="col">Curso</th>
      <th scope="col">Cupos</th>
      <th scope="col">Inscritos</th>
      <th scope="col">Duracion</th>
      <th scope="col">Costo</th>
      <th scope="col">Terminado</th>
      <th scope="col">Fechas</th>
      <th scope="col">acciones</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="curso in cursos"
    :key="curso.id">
      <td>{{curso.nombre}}</td>
      <td>{{curso.cupos}}</td>
      <td>{{curso.inscritos}}</td>
      <td>{{curso.duracion}}</td>
      <td><v-chip
      class="ma-2"
      color="green"
      text-color="white">
      {{curso.costo}}
    </v-chip></td>
      <td ><v-chip
      class="ma-2"
      :color="getColor(curso.completado)">
      {{terminado( curso.completado)}}
      </v-chip></td>
      <td>
      <v-chip
      class=""
      color="green"
      text-color="white">
      {{curso.fecha_registro}}
      </v-chip>
      </td>
      <td class="d-flex align-baseline">
        <v-btn @click="editar(curso.id)" color="warning">Editar</v-btn >
          <v-btn @click="eliminar(curso.id)" color="error">Eliminar</v-btn>
       </td>
      
    </tr>
  </tbody>
</v-simple-table>
</div>
    <v-row class="d-flex flex-column align-center my-5">
      <p class="border w-75" id="cupos">Cantidad total de alumnos permitidos: {{ totalCupos }}</p>
      <p class="border w-75" id="inscritos">Cantidad total de alumnos inscritos: {{ totalInscritos }}</p>
      <p class="border w-75" id="restantes">Cantidad total de cupos restantes: {{ totalCuposRestantes }}</p>
      <p class="border w-75" id="restantes">Cantidad total de cursos terminados: {{ totalCursosTerminados }}</p>
      <p class="border w-75" id="activos">Cantidad total de cursos activos: {{ totalCursosActivos }}</p>
      <p class="border w-75" id="totalCursos">Cantidad total de cursos: {{ totalCursos }}</p>
    </v-row>
    
<v-dialog
      v-model="dialog"
      persistent
      max-width="290">
      
      <v-card>
        <v-card-title class="text-h5">
          Eliminar curso
        </v-card-title>
        <v-card-text>¿Realmente desea eliminar el curso?</v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="green darken-1"
            text
            @click="dialog = false"
          >
            Cancelar
          </v-btn>
          <v-btn
            color="error"
            text

            @click="borrar(selectedId)"
          >
            Eliminar
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>  
  </div>
</template>

<script>
import {mapState, mapGetters, mapActions} from 'vuex'
export default {
  name: 'administracion-view',
  // props: {},
  data: function(){
    return {
      selectedId:"",
      dialog: false,
      
    }
  },
  computed: {
    ...mapState(['cursos']),
    
    ...mapGetters(['totalInscritos','totalCupos','totalCuposRestantes','totalCursos','totalCursosActivos','totalCursosTerminados']),
  },
  methods: {
    ...mapActions(['eliminarCurso']),

    reRouteAdd(){
      this.$router.push('/addCourse')
    },

    editar(id){
      this.$router.push(`/administracion/edit/${id}`)
    },

    eliminar(index){
      alert('eliminar'+index)
      this.selectedId = index
      this.dialog = true

    },

    borrar(idCourse){
      
      this.eliminarCurso(idCourse);
      this.dialog = false
    },

    terminado(status){
      if(status == true){
        return "si"
      }else{
        return "no"
      }

    },
    getColor(status){
      if(status==true){
        return "info"
      } else{
        return "default"
      }

    }
    
    
    // modal(){
    // const myModal = document.getElementById('myModal')
    // const myInput = document.getElementById('myInput')

    // myModal.addEventListener('shown.bs.modal', () => {
    // myInput.focus()
    // })
    // },
    // openModal(id) {
    //         this.selectedId = id;
    //         this.showModal = true;
    //         alert(id)
    //     },
    // closeModal() {
    //         this.showModal = false;
    //         this.selectedId = null;
    // },
        
    
  },
  // watch: {},
  components: {
    
  },
  // mixins: [],
  // filters: {},
  // -- Lifecycle Methods
  // -- End Lifecycle Methods
}
</script>

<style scoped>

#cupos{
  color: blueviolet;
}

#inscritos{
  color: blue;

}

#restantes{
  color: orangered;

}

#activos{
  color: olivedrab;

}

#totalCursos{
  color: rgb(255, 174, 0);

}

  
</style>