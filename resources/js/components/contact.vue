<template>
  <div>
    <h1 class="text-center">Agenda de contacto</h1>
    <hr />
    <table class="table table-striped table-hover">
      <thead class="table-dark">
        <tr>
          <th scope="col">Id</th>
          <th scope="col">Nombre</th>
          <th scope="col">Apellido</th>
          <th scope="col">Correo electronico</th>
          <th scope="col">Telefono</th>
          <th scope="col">Domicilio</th>
          <th scope="col" colspan="2" class="text-center">Acción</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="contact in contacts" :key="contact.id">
          <th scope="row">{{ contact.id }}</th>
          <th>contact.first_name</th>
          <th>contact.last_name</th>
          <th>contact.email</th>
          <th>contact.phone</th>
          <th>contact.address</th>
          <td>
            <button class="btn btn-warning">Editar</button>
          </td>
          <td>
            <button @click="eliminar(contact.id)" class="btn btn-danger">Eliminar</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data (){
        return {
            contacts:[],
        }
    },
    methods: {
        async list() {
            const res = await axios.get('contacts');
            this.contacts = res.data;
        },
        async eliminar(id){
            const res = await axios.delete('/contacts/' +id);
            this.list();
        }

    },
    created(){
        this.list();
    },
  
}
</script>

<style scoped>
</style>