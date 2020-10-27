<template>
  <div class="container">
    <div class="form">
      <form @submit.prevent>
        <label for="nome"><strong>Nome</strong></label>
        <input
          v-model="nome"
          type="text"
          id="nome"
          name="nome"
          placeholder="Digite seu nome..."
        />

        <label for="sobrenome"><strong>Sobrenome</strong></label>
        <input
          v-model="sobrenome"
          type="text"
          id="sobrenome"
          name="sobrenome"
          placeholder="Digite seu sobrenome..."
        />

        <label for="email"><strong>Email</strong></label>
        <input
          v-model="email"
          type="email"
          id="email"
          name="email"
          placeholder="Digite seu email..."
        />

        <label for="telefone"><strong>Telefone</strong></label>
        <input
          v-model="telefone"
          type="text"
          id="telefone"
          name="telefone"
          placeholder="Digite seu telefone..."
        />

        <div class="checkbox">
          <label class="checkbox">
            <input v-model="checado" id="cnpj" type="checkbox" name="cnpj" />
            CNPJ
          </label>
        </div>

        <div v-if="checado">
          <label :for="checado"></label>
          <input
            v-model="cnpj"
            type="text"
            id="cnpj"
            name="cnpj"
            placeholder="Coloque seu cnpj"
          />
        </div>

        <div v-else>
          <label for="cpf">cpf</label>
          <input
            v-model="cpf"
            type="text"
            id="checado"
            name="checado"
            placeholder="Coloque seu cpf"
          />
        </div>

  
          <input v-on:click="estado" type="submit" value="Submit" />
     
      
       <!-- <div else class="buttons">
       <button v-on:click="emitiralterar" class="button is-info"  type="button">Atualizar</button>

</div> -->
      





      </form>
    </div>
    <div class="container-dados">
      <div class="dado" v-for="cliente in clientes" :key="cliente.id">
        
        <Cliente :cliente="cliente" @alterar="atualizarusuario($event)"  @delete="deletarusuario($event)" />
      </div>
    </div>
  </div>
</template>

<script>
import Cliente from "./components/Cliente.vue";
export default {
  name: "App",
  data() {
    return {
      nome: "",
      sobrenome: "",
      email: "",
      telefone: "",
      razaoSocial: "",
      checado: false,
      cpf: "",
      cnpj: "",
      id: "",
      clientes: [],
      estadoform: "cadastrar"
    };
  },
  components: {
    Cliente,
  },
  //     watch:{
  //    checadow:function(){

  //      if(this.checado){

  //       this.razaoSocial = this.cnpj;
  //      // this.cpf = ''
  //  console.log(this.razaoSocial);

  //      }else{
  //             this.razaoSocial = this.cpf;
  //             //this.checado = false;
  //             // this.cnpj = ''
  //              console.log( this.razaoSocial);
  //        }
  //    }
  //     },
  methods: {
    estado:function(){
     if(this.estadoform == "cadastrar"){
      this.adicionar()
     }


    },
    limparcampos:function(){
    this.nome = "",
      this.sobrenome = "",
        this.email = "",
        this.telefone = ""
       
    },
    adicionar: function () {
      this.clientes.push({
        nome: this.nome,
        sobrenome: this.sobrenome,
        email: this.email,
        telefone: this.telefone,
        id: Date.now(),
      });
      this.limparcampos();
   
    },
    updateusuario:function(){
      
    },
    atualizarusuario: function($event){
     this.estadoform = "atualizar";
         var id = $event.idcliente;
         console.log("id" + id );
         this.nome =  $event.nome
         this.sobrenome =  $event.sobrenome
         this.email =  $event.email
         this.telefone =  $event.telefone
            console.log($event);
        console.log("estado" + this.estadoform)
        console.log(this.clientes);
    },

    deletarusuario: function ($event) {
      var id = $event.idcliente;
      var listanova = this.clientes.filter((cliente) => cliente.id != id);
      this.clientes = listanova;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.container {
  display: flex;
  justify-content: center;
}

/* .form
  {
    border: 1px solid blue;
    min-width: 30vw;
    margin-right: 5px;
  } */
.formulario {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
}
.container-dados {
  width: auto;

  /* min-width: 30vw; */

  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 5px;
}

.dado {
  margin-bottom: 20px;

  width: 100%;
}
input[type="text"],
select {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}
input[type="email"],
select {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}
input[type="submit"] {
  width: 100%;
  background-color: #4caf50;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

input[type="submit"]:hover {
  background-color: #45a049;
}

.conteinerdados {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.dados {
  margin: 10px;
  display: flex;
  flex-direction: column;
  width: 100%;
  border: 1px solid green;
}

.container {
  display: flex;
}
</style>
