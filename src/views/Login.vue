<template>
    <header class="header">
        <div id="container">
            <div>
                logo
            </div>

            <div>
                <span>Voce ja tem uma conta na LinkTec?</span> 
                <span><strong> Faca login {{me}}</strong></span>
            </div>            
        </div>
    </header>

    <div id="register" v-if="tipoCadastro == null">
        <div class="a_register">
            <h1 style="text-align:center;">Criar uma conta{{tipoCadastro}}</h1>

            <br>

            <span>Seja bem-vindo ao LinkTec Diga-nos o que você está procurando.</span>        

            <div id="tipos">
                <div class="tipo">
                <!-- Ofertante -->
                    <input class="inputOption" type="radio" name="ofertante">
                    <span class="title_type text-center">Eu quero trabalhar</span>
                    <!-- Description -->
                    <div class="description_type">
                        <span>Encontre projetos, seja contratado e ganhe dinheiro.</span>                      
                    </div>
                </div>  

                <!-- Contratante -->
                <div class="tipo">
                    <input class="inputOption" type="radio" name="ofertante">
                    <span class="title_type">Eu quero Contratar</span>
                    <!-- Description -->
                    <div class="description_type">
                        <span>Publique a sua vaga e encontre freelancers incríveis.</span>                         
                    </div>
                </div>                  
            </div>
            
            <button class="buttonGreen" @click="tipoCadastro = 2">Continuar</button>
        </div>
        
    </div>

    <div id="register" v-if="tipoCadastro == 1">
        <div class="b_register">
            <h1 style="text-align:center;">Cadastro</h1>

            <br>

            <h4 v-on:click="tipoCadastro = 2" style="text-align:center;">Esta buscando trabalho? Cadastre-se como Freelancer.</h4>        

            <form>
                <input type="text" name="" id="" class="inputRegister" placeholder="Nome completo">

                <input type="text" name="" id="" class="inputRegister" placeholder="Documento" v-model="documento">

                <select class="inputRegister" style="width: 100%" name="" id="">
                    <option v-for="tPago in tipoPagamento" v-bind:key="tPago.id">{{tPago}}</option>
                </select>
            </form>
            
            <button class="buttonGreen" v-on:click="cadastrar()">Cadastrar</button>
        </div>
        
    </div>

        <div id="register" v-if="tipoCadastro == 2">
        <div class="b_register">
            <h1 style="text-align:center;">Cadastro</h1>

            <br>

            <h4 v-on:click="tipoCadastro = 1" style="text-align:center;">Esta precisando contratar? Cadastre-se como Cliente.</h4>        

            <form>
                <input type="text" name="" id="" class="inputRegister" placeholder="Nome completo">

                <input type="text" name="" id="" class="inputRegister" placeholder="Documento" v-model="documento">

                <select class="inputRegister" style="width: 100%" name="" id="">
                    <option v-for="tPago in tipoPagamento" v-bind:key="tPago.id">{{tPago}}</option>
                </select>

                <input type="file" name="" id="" class="inputRegister" placeholder="Arquivos de comprovacao de atividade">

                <hr style="margin: 8px 0px;">


                <div style="margin-bottom: 21px;">
                    <div style="margin-bottom: 13px">
                        <input type="checkbox" style="margin-right: 8px">
                        <span>Font-End</span>
                    </div>

                    <div style="margin-bottom: 13px">
                        <input type="checkbox" style="margin-right: 8px">
                        <span>Back-End</span>
                    </div>

                    <div style="margin-bottom: 13px">
                        <input type="checkbox" style="margin-right: 8px">
                        <span>DevOps</span>
                    </div>

                    <div style="margin-bottom: 13px">
                        <input type="checkbox" style="margin-right: 8px">
                        <span>Database Administrator</span>
                    </div>                   
                </div>

                <hr style="margin: 8px 0px;">

            </form>
            
            <button class="buttonGreen" v-on:click="cadastrar()">Cadastrar</button>
        </div>
        
    </div>

  <FooterComponent/>
</template>

<script>
import FooterComponent from '../components/FooterComponent.vue';

export default {
  name: 'Login',
  components: { FooterComponent },
  data(){
      return{
          tipoCadastro: null,
          documento: null,
          tipoPagamento:['Cartao de Credito', 'Boleto', 'Pix', 'Dinheiro'],
          tipoServico:['FontEnd', 'BackEnd', 'DevOps','DatabaseAdministrator']
      }
  },
  
  methods: {
      verificaDocumento(){
          console.log(this.documento);
      },
      cadastrar: () => {
          window.alert("Cadastrado.")
      }
  },

  mounted: ()=>{
      let xhr = new XMLHttpRequest;
        
      xhr.open("POST", true);

      xhr.onreadystatechange = () => {
          if(xhr.status == 200){
              console.log(xhr.responseText);
              return this.documento = xhr.responseText;
          }else{
              console.error(xhr.status);
          }
      }

      xhr.send("www.demonhao.net");
  }
}

</script>

<style>
    *{
        color: #7d7d7d;
    }

    #container{
        height: 100%;
        width: 1200px;
        margin: 0 auto;
    }

    .header{
        width: 100%;
        height: 80px;
        color: #fefefe;
        background-color: #5a8b94;
    }

    .header{
        color: #fefefe;
        font-size: 12px;
    }

    .header *{
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    #register{
        width: 100%;
        box-sizing: border-box;
        height: calc(100vh - 160px);
    }

        #register{
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .a_register{
            width: 500px; 
            padding: 40px;
            height: 380px; 
            font-size: 13px;
            border-radius: 3px;
            box-sizing: border-box;
            background-color: #fefefe; 
            border: 1px solid #1818182e;
            text-align: left;
        }

        .b_register{
            width: 500px; 
            padding: 40px;
            height: 380px; 
            font-size: 13px;
            border-radius: 3px;
            box-sizing: border-box;
            background-color: #fefefe; 
            border: 1px solid #1818182e;
            text-align: left;
            display: table;
        }

        #tipos{
            width: 100%;
            margin: 13px 0px;
            font-size: 13px;
        }

        .tipo{
            margin-bottom: 21px;
        }

        .title_type{
            font-size: 15px;
            font-weight: 600;            
        }

        .description_type{
            margin-top: 5px;
            margin-left: 25px;
        }

        .inputOption{
            font-weight: 600;
            margin-right: 13px;
        }

        input[type=radio] {
            width: 18px;
            height: 18px;
            border-radius: 12px;
            -moz-appearance: none;
            -webkit-appearance: none;
            border: 3px solid #bdc3c7;
        }

        input[type=radio]:checked{
            background-color: #5a8b94;
            }


        .inputRegister{
            width: 100%;
            height: 25px;
            height: 50px;
            padding: 0 10px;
            border: 1px solid #ccc;
            -webkit-box-shadow: inset 0 1px 2px rgb(0 0 0 / 10%);
            box-shadow: inset 0 1px 2px rgb(0 0 0 / 10%);
            -webkit-border-radius: 5px;
            -moz-border-radius: 5px;
            -ms-border-radius: 5px;
            -o-border-radius: 5px;
            border-radius: 5px;
            transition: box-shadow .45s,border-color .45s ease-in-out;
            font-size: 15px;
            color: rgba(0,0,0,.75);
            -moz-box-sizing: border-box;
            -webkit-box-sizing: border-box;
            box-sizing: border-box;
            margin: 12px 0px;
            }


    /* Buttons */
    .buttonGreen{
        color: #fefefe;
        border: 0;
        padding: 12px;
        width: 100%;
        height: 55px;
        border-radius: 3px;
        background-color:  #16ac2fcd;
        transition: 250ms ease-in-out;
        margin-top: auto;
    }

    .buttonGreen:hover{
        cursor: pointer;
        background-color:  #16ac2fe7;
    }

    .text-center{
        text-align: center!important;
    }
</style>