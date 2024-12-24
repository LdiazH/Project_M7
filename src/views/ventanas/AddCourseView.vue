<template>
    <v-container >
        <v-row class="d-flex justify-center my-5" >
        <h1> Añadir curso</h1>
    </v-row>
        <v-row class="d-flex justify-center" >
            <v-col cols="12" md="8">
            <v-form action=""
            v-model="valid"
            ref="form"
            class="d-flex flex-column my-5 cyan lighten-4 pa-4  " 
            > 
                <v-text-field
                v-model="name"
                label="Nombre"
                :rules="nameRules"
                required
                >
                </v-text-field>
                <v-text-field
                v-model="url"
                label="Url de la imagen"
                :rules="urlRules"
                required
                ></v-text-field>
                <v-text-field
                v-model="vacantes"
                label="Cupos del curso"
                :rules="vacantesRules"
                required
                ></v-text-field>
                <v-text-field
                v-model="suscritos"
                label="Inscritos del curso"
                :rules="suscritosRules"
                required
                ></v-text-field>
                <v-text-field
                v-model="tiempo"
                label="Duracion del Curso"
                :rules="tiempoRules"
                required
                ></v-text-field>
                <v-text-field
                v-model="todayDate"
                label="Fecha de registro"
                required
                ></v-text-field>
                <v-text-field
                v-model="valor"
                label="Costo"
                :rules="valorRules"
                required
                ></v-text-field>
                <v-text-field
                v-model="details"
                label="Descripcion"
                :rules="detailsRules"
                required
                ></v-text-field>
                <div class="my-5">
                <v-btn 
                @click="add" 
                color="success"
                :disabled="!valid"
                >Agregar
                </v-btn>
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
            valid:false,
            name: "",
            nameRules: [
            v => !!v || 'Name is required',
            v => (v && v.length <= 15 ) || 'Name must be less than 15 characters',
            v => /^[A-Za-z]+$/.test(v) || 'Only letters'
            ],
            url: "",
            urlRules:[
            v => !!v || 'Url is required', 
            ], 
            vacantes: "",
            vacantesRules:[
            v => !!v || 'Number is required',
            v => /^[\d]+$/.test(v) || 'Only numbers'
            ],
            suscritos: "",
            suscritosRules:[
            v => !!v || 'Number is required',
            v => /^[\d]+$/.test(v) || 'Only numbers',
            v => (!!v &&  parseInt(this.vacantes)> parseInt(this.suscritos) )|| 'Cupos debe ser mayor a inscritos'
            ],
            tiempo: "",
            tiempoRules:[
            v => !!v || 'Month is required',
            ],
            // fecha: "",
            // fechaRules:[
            // v => !!v || 'Date is required',
            // ],
            valor: "",
            valorRules:[
            v => !!v || 'Value is required',
            v => /^[\d]+$/.test(v) || 'Only numbers'
            ],
            details: "",
            detailsRules:[
            v => !!v || 'Details are required',
            ],
            
            
        }
    },
    computed: {
        todayDate(){
            
            const today = new Date();
    
            const day = today.getDate().toString().padStart(2, '0');
            const month = (today.getMonth() + 1).toString().padStart(2, '0');
            const year = today.getFullYear().toString() 
            return `${day}/${month}/${year}`;
            
        },

    },
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
                fecha_registro: this.todayDate,
                descripcion: this.details, 
                }
                
                console.log(newCurso)
                console.log(this.fecha)

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
            this.details= "",

            this.$refs.form

        },

        cancel(){
            this.$router.push('/administracion')
            
        },
        validator(expression, value){

            if(expression.test(value)){
            return true
            }
            return false
        }
        
    },
    // watch: { },
    components: {
        
    },
    // mixins: [],
    // filters: {},
    // -- Lifecycle Methods
    created(){
        this.fecha = this.fechaActual
    }
    // -- End Lifecycle Methods
}
</script>

<style scoped>

    
</style>