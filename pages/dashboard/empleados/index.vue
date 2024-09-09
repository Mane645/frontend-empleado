<template>
  <div>
    <v-row align="center" justify="center">
      <h1>CRUD Empleados</h1>
    </v-row>
    <v-row align="center" justify="center">
      <v-data-table
        style="width: 100%;"
        :headers="headers"
        :items="empleados"
      />
    </v-row>
  </div>
</template>

<script>
export default {
  data () {
    return {
      empleados: [],
      headers: [
        {
          text: 'Nombre',
          align: 'center',
          sortable: true,
          value: 'nombre'
        },
        {
          text: 'A. Paterno',
          align: 'center',
          sortable: true,
          value: 'apaterno'
        },
        {
          text: 'A. Materno',
          align: 'center',
          sortable: true,
          value: 'amaterno'
        },
        {
          text: 'Ciudad',
          align: 'center',
          sortable: true,
          value: 'ciudad'
        },
        {
          text: 'Estado',
          align: 'center',
          sortable: true,
          value: 'estado'
        },
        {
          text: 'Direccion',
          align: 'center',
          sortable: true,
          value: 'direccion'
        },
        {
          text: 'Telefono',
          align: 'center',
          sortable: true,
          value: 'telefono'
        },
        {
          text: 'Perfil',
          align: 'center',
          sortable: true,
          value: 'perfil'
        }
      ]
    }
  },
  mounted () {
    this.loadEmpleados()
  },
  methods: {
    async loadEmpleados () {
      const response = await this.$axios.get('/get-all')
      if (response.data.success === true) {
        // this.empleados = response.data.message
        response.data.message.forEach((item) => {
          this.empleados.push(item)
        })
      }
      console.log('@@@ Response', this.empleados)
    }
  }
}
</script>

<style scoped>
</style>
