<template>
    <v-container>
        <h1> Añadir curso</h1>
        <v-row class="d-flex justify-center" >
            <v-col cols="12" md="8">
            <v-form action="" class="d-flex  flex-column my-5" >
                
                <v-text-field
                v-model="name"
                label="Nombre"
                required
                ></v-text-field>
                <v-text-field
                v-model=" url"
                label="Url de la imagen"
                required
                ></v-text-field>
                <v-text-field
                v-model="vacantes"
                label="cupos del curso"
                required
                ></v-text-field>
                <v-text-field
                v-model="suscritos"
                label="inscritos del curso"
                required
                ></v-text-field>
                <v-text-field
                v-model="tiempo"
                label="Duracion del Curso"
                required
                ></v-text-field>
                <v-text-field
                v-model="fecha"
                label="Fecha de registro"
                required
                ></v-text-field>
                <v-text-field
                v-model="valor"
                label="Costo"
                required
                ></v-text-field>
                <v-text-field
                v-model="details"
                label="Descripcion"
                required
                ></v-text-field>
                <div class="my-5">
                <v-btn @click.prevent="add" color="success">Agregar</v-btn>
                <v-btn @click.prevent="clean" color="warning">Limpiar formulario</v-btn>
                <v-btn @click.prevent="cancel" color="error">Cancel</v-btn>
            </div>     
        </v-form>
    </v-col>
    </v-row>
    </v-container>
   
</template>

<script>

import { mapActions } from 'vuex';

export default {
    name: 'addcourse-view',
    // props: {},
    data: function(){
        return {
            name: "",
            url: "",
            vacantes: "",
            suscritos: "",
            tiempo: "",
            fecha: "",
            valor: "",
            details: "",
            
        }
    },
    // computed: {},
    methods: {
        ...mapActions(['addCourse']),

        add(){
            let valid = true;
            
            if(valid){

                let newCurso = {
                img: this.url,
                nombre: this.name,
                costo: parseInt(this.valor),
                duracion: this.tiempo,
                cupos: parseInt(this.vacantes),
                inscritos: parseInt(this.suscritos),
                fecha_registro: this.fecha,
                descripcion: this.details, 
                }
                console.log(newCurso)

                this.addCourse(newCurso)
                this.$router.push('/administracion')
            }
        },
        clean(){
            this.name= "",
            this.url="",
            this.vacantes= "",
            this.suscritos= "",
            this.tiempo= "",
            this.fecha= "",
            this.valor= "",
            this.details= ""

        },

        cancel(){
            this.$router.push('/administracion')
            
        },
        
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

    
</style>