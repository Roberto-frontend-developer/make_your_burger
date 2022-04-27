<template>
<dvi> 
  <Message :msg ="msg" v-show="msg" />
</dvi>
 <div>
  <form id="burger-form" method="POST" @submit="createBurger">
    <div class="input-container">
      <label for="nome">Nome do cliente: </label>
      <input type="text" id="nome" name="nome" v-model="nome"
        placeholder="Digite seu Nome" />
    </div>

    <div class="input-container">
      <label for="pao">Escolha o pão: </label>
      <select name="pao" id="pao" v-model="pao">
        <option value="">Selecione seu pão</option>
        <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">
         {{ pao.tipo }}
        </option>
      </select>
    </div>

    <div class="input-container">
      <label for="carne">Escolha sua carne: </label>
      <select name="carne" id="carne" v-model="carne">
        <option value="">Selecione o tipo de carne</option>
        <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">
         {{ carne.tipo}}
         </option>
      </select>
    </div>

    <div id="opcionais-container" class="input-container">
      <label id="opcionais-title" for="opcionais">
       Selecione os opcionais:
      </label>
      <div class="checkbox-container" v-for="opcional in opcionaisdata"
      :key="opcional.id" >
        <input
          type="checkbox"
          name="opcionais"
          v-model="opcionais"
          :value="opcional.tipo"
        />
        <span>{{ opcional.tipo }}</span>
      </div>     
      <div class="input-container">
       <input type="submit" class="submit-btn" value="Criar meu Burger" />
      </div>
    </div>
  </form>
 </div>
</template>

<script>
import Message from './Message.vue'
export default {
  name: "BurgerFom",

  data() {
   return {
    paes: null,
    carnes: null,
    opcionaisdata: null,
    nome: null,
    pao: null,
    carne: null,
    opcionais:[],
    msg: null
   }
  },
  methods: {
   async getIngredientes () {

    const req = await fetch("http://localhost:3000/ingredientes");
    const data= await  req.json();

    this.paes = data.paes;
    this.carnes = data.carnes;
    this.opcionaisdata = data.opcionais
   },
   async createBurger(e) {
    e.preventDefault()
    
    const data = {
     nome: this.nome,
     carne: this.carne,
     pao: this.pao,
     opcionais: Array.from(this.opcionais),
     status: "Solicitado"
    }

    const dataJson = JSON.stringify(data);
    const req = await  fetch(" http://localhost:3000/burgers", { 
     method: "POST",
     headers: {"Content-type": "application/json"},
     body: dataJson
    });

    const res = await req.json();
    //colocar mnesagem de sistema
    this.msg = `Pedido de N° ${res.id} realizando com sucesso`

    //limpar msg
    setTimeout(()=> this.msg ="", 3000);

    //limpar os campos 
    this.nome = "";
    this.carne = "";
    this.pao = "";
    this.opcionais = "";
   }
  },
  mounted() {
   this.getIngredientes()
  },
  components: {
    Message
  }
};
</script>

<style scoped>
#burger-form {
  width: 400px;
  margin: 0 auto;
}
.input-container {
  display: flex;
  flex-direction: column;
  margin-bottom: 20px;
}

label {
  font-weight: bold;
  margin-bottom: 15px;
  color: #222;
  padding: 5px 10px;
  border-left: 4px solid #fcba03;
}

input,
select {
  padding: 5px 10px;
  widows: 300px;
}

#opcionais-container {
  flex-direction: row;
  flex-wrap: wrap;
  
}

#opcionais-title {
  width: 100%;
}

.checkbox-container {
  display: flex;
  align-items: center;
  width: 50%;
  margin: 15px auto;
}

 .checkbox-container span,
 .checkbox-container input {
    width: auto;
  }

  .checkbox-container span {
    margin-left: 6px;
    font-weight: bold;
  }
  
  .submit-btn {
    background-color: #222;
    color:#fcba03;   
    border: 1px solid #222;
    border-radius: 18px;

    margin: 50px 90px auto ;

    padding: 15px;
    font-size: 16px;
    font-weight: bold;
    
    cursor: pointer;
    transition: .5s;
  }

  .submit-btn:hover {
    background-color: transparent;
    color: #222;
  }
</style>
