<template>
    <div>
        <h1 class="my-5">Administrando la Lista de Opiniones</h1>
    <div class="container" v-if="existenOpiniones">
        <div class="alert alert-danger">
        No existen opiniones para editar.
        </div>
    </div>
        <table v-else class="table w-75 m-auto">
        <thead>
            <tr>
            <th>#</th>
            <th>Persona</th>
            <th>Juego</th>
            <th>Opinion</th>
            <th></th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(opinion, i) in getJuegosAndOpiniones" :key="i">
            <td>{{ opinion.id }}</td>
            <td>{{ opinion.usuario.nombre }}</td>
            <td>{{ opinion.juego.name }}</td>
            <td>{{ opinion.descripcion }}</td>
            <td>
                <button @click="eliminar_Opinion(opinion.id)" class="btn btn-danger me-5">Eliminar</button>
                <button @click="irAEditarOpinion(opinion.id)" class="btn btn-info">Editar</button>
            </td>
            </tr>
        </tbody>
        </table>
    </div>
</template>

<script>
import { mapGetters, mapActions } from "vuex";
export default {
    computed: {
        ...mapGetters(["getJuegosAndOpiniones"]),
        existenOpiniones(){
        return !this.getJuegosAndOpiniones.length
        }
    },
    methods: {
        ...mapActions(["eliminar_Opinion"]),
        irAEditarOpinion(id) {
        this.$router.push(`/editar/${id}`);
        },
    },
};
</script>

<style>
</style>