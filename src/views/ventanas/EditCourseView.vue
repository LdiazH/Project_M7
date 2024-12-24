<template>
    <v-container>
        <v-row class="d-flex justify-center my-5" >
            <h1 > Editar curso {{ this.id }}</h1>
        </v-row>
        <v-row class="d-flex justify-center" >
            <v-col cols="12" md="8">
            <v-form action="" class="d-flex  flex-column cyan lighten-4 pa-4" > 
                <v-text-field
                v-model="courseToEdit.nombre"
                label="Nombre"
                required
                ></v-text-field>
                <v-text-field
                v-model="courseToEdit.img"
                label="Url de la imagen"
                required
                ></v-text-field>
                <v-text-field
                v-model="courseToEdit.cupos"
                label="cupos del curso"
                required
                ></v-text-field>
                <v-text-field
                v-model="courseToEdit.inscritos"
                label="inscritos del curso"
                required
                ></v-text-field>
                <v-text-field
                v-model="courseToEdit.duracion"
                label="Duracion del Curso"
                required
                ></v-text-field>
                <v-text-field
                v-model="courseToEdit.fecha_registro"
                label="Fecha de registro"
                required
                ></v-text-field>
                <!-- <v-text-field
                v-model="courseToEdit.completado"
                label="Terminado"
                required
                ></v-text-field> -->
                <v-select
                :items="[true,false]"
                label="Completado"
                v-model="courseToEdit.completado"
                >
                </v-select>
                <v-text-field
                v-model="courseToEdit.costo"
                label="Costo"
                required
                ></v-text-field>
                <v-text-field
                v-model="courseToEdit.descripcion"
                label="Descripcion"
                required
                ></v-text-field>
                <v-col>
                <v-btn @click.prevent="agregar(courseToEdit.id)" color="success">Agregar</v-btn>
                <v-btn @click.prevent="cancel" color="error">Cancel</v-btn>
                </v-col>    
        </v-form>
    </v-col>
    </v-row>
    </v-container>
</template>


<script>
import { mapState } from 'vuex';
import { mapActions } from 'vuex';

export default {

    name: 'edit-view',
    // props: {},
    data: function(){
        return {
            courseToEdit:""

        }
    },
    computed: {
        ...mapState(['cursos']),
        id(){
            return this.$route.params.id
        },
    // boolean(){
    //     if(this.courseToEdit.finish === true){
    //         return true
    //     }
    //     return false
    // }
    },
    methods: {
        ...mapActions(['guardarCambios']),
        getCourse(id){
            let index = this.cursos.find((curso)=> curso.id==id)
            return this.courseToEdit = index
        },
        agregar(index){
            console.log( !!this.courseToEdit.completado)
            console.log(typeof !!this.courseToEdit.completado)
            let newEditCourse = {
                
                img: this.courseToEdit.img,
                nombre: this.courseToEdit.nombre,
                costo: parseInt(this.courseToEdit.costo),
                completado: !!this.courseToEdit.completado,
                duracion: this.courseToEdit.duracion,
                cupos: parseInt(this.courseToEdit.cupos),
                inscritos: parseInt(this.courseToEdit.inscritos),
                fecha_registro: this.courseToEdit.fecha_registro,
                descripcion: this.courseToEdit.descripcion, 
                }
            console.log(newEditCourse)
            this.guardarCambios(index,newEditCourse)
            this.$router.push('/administracion/')
        },
        cancel(){
            this.$router.push('/administracion/')
        }
        

        
    },
    // watch: {},
    // components: {},
    // mixins: [],
    // filters: {},
    // -- Lifecycle Methods
    created(){
        this.getCourse(this.id)
            
        
    },
    // -- End Lifecycle Methods
}
</script>

<style scoped>
    
</style>    