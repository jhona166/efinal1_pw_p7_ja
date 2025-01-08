<template>
    <div class="container">
        <table>
            <tr>
                <td>Foto:</td>
                <td><img :src="localFoto" alt="foto" /></td>
              
            </tr>
            <tr>
                <td>Título:</td>
                <td>{{ localTitulo }}</td>
              
            </tr>
            <tr>
                <td>Nombre:</td>
                <td>{{ localNombre }}</td>
               
            </tr>
            <tr>
                <td>Apellido:</td>
                <td>{{ localApellido }}</td>
            
            </tr>
            <tr>
                <td>Ciudad:</td>
                <td>{{ localCiudad }}</td>
              
            </tr>
            <tr>
                <td>País:</td>
                <td>{{ localPais }}</td>
                
            </tr>
        </table>
    </div>
</template>

<script>
export default {
    props: {
        foto: String,
        titulo: String,
        nombre: String,
        apellido: String,
        ciudad: String,
        pais: String
    },
    data() {
        return {
            localFoto: this.foto,
            localTitulo: this.titulo,
            localNombre: this.nombre,
            localApellido: this.apellido,
            localCiudad: this.ciudad,
            localPais: this.pais
        };
    },
    methods: {
        updateFoto() {
            this.$emit('update:foto', this.localFoto);
        },
        updateTitulo() {
            this.$emit('update:titulo', this.localTitulo);
        },
        updateNombre() {
            this.$emit('update:nombre', this.localNombre);
        },
        updateApellido() {
            this.$emit('update:apellido', this.localApellido);
        },
        updateCiudad() {
            this.$emit('update:ciudad', this.localCiudad);
        },
        updatePais() {
            this.$emit('update:pais', this.localPais);
        }
    }
}
</script>

<style>
.container {
    display: flex;
    flex-direction: column;
    width: 50%;
    margin: 0 auto;
}
table {
    width: 100%;
    border-collapse: collapse;
}
td {
    padding: 8px;
    border: 1px solid #ddd;
}
</style>