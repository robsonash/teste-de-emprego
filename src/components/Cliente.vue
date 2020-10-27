<template>


<div>
  <strong>Id: </strong> {{cliente.id}}
  <strong>Nome: </strong> {{cliente.nome}}
  <strong>Sobrenome:</strong>{{cliente.sobrenome}}
  <strong>Email:</strong>{{cliente.email}}
  <strong> Telefone:</strong>{{cliente.telefone}}
  <div class="buttons">
  <button v-on:click="emitiralterar" class="button is-warning"  type="button">Editar</button>
 <button v-on:click="emitirdelete"  class="button is-danger" type="button">Excluir</button>
</div>
</div>


</template>

<script>
export default {
  name:'Cliente',
 data() {

    return {
 
    }
 },
 props:{
   cliente: Object
 },


    methods:{
      emitiralterar:function(){
   this.$emit("alterar",{idcliente: this.cliente.id,nome: this.cliente.nome,sobrenome: this.cliente.sobrenome,email: this.cliente.email,telefone: this.cliente.telefone,component: this});
      },
     emitirdelete:function(){
     this.$emit("delete",{idcliente: this.cliente.id,component: this});
     }
   



    }, 

    computed:{

    }
}
    </script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
/* .formulario{
  width: 50%;
  border-radius: 5px;
  background-color: #f2f2f2;
  padding: 20px;
}
input[type=text], select {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}
input[type=email], select {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}
input[type=submit] {
  width: 100%;
  background-color: #4CAF50;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

input[type=submit]:hover {
  background-color: #45a049;
}
.container{
  display: flex;
  
} */






</style>
