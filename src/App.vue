<template>
  <div>
    <section class="section">
      <div class="container">
        <div class="columns">
          <!-- esquerda -->
          <div class="column is-3 lista-de-conversas">
            <div class="barra-superior" />
            <div class="item" v-for="(conversa, index) in conversas" :key="index" @click="indiceAtivo = index">
              <div class="title is-6">
                {{ conversa.usuario }}
              </div>
              <div class="subtitle is-6">
                Última Mensagem...
              </div>
            </div>
          </div>
          <!-- direita -->
          <div class="column conversa-ativa">
            <div class="barra-superior">
              <span>{{ conversas[indiceAtivo].usuario }}</span>
            </div>
            <div class="lista-mensagens">
              <Mensagem v-for="(mensagem, indice) in conversas[indiceAtivo].mensagens" :key="indice" 
              :conteudo="mensagem.conteudo" :verde="mensagem.verde" :horario="mensagem.horario" />
            </div>
            <div class="barra-inferior">
                <input type="text" class="input" placeholder="Insira sua mensagem">
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import conversasIniciais from './dados'
import Mensagem from './components/Mensagem'
export default {
  data(){
    return {
      conversas: conversasIniciais,
      indiceAtivo: 0,
      conteudoNovaMensagem
    }
  },
  components: {
    Mensagem
  }
}
</script>

<style>

.barra-inferior {
    bottom:0;
    width: 76.4%;
    padding: 10px;
    position: absolute;
    background: #f0f0f0;
}

.barra-inferior input {
    border:none;
    padding: 10px;
    margin: 0 50px;
    width: 93%;
    border-radius: 15px;
    font-size: 16px;
}

.lista-mensagens{
    height: 85%;
    display: flex;
    justify-content: flex-end;
    flex-direction: column;
}

.column {
  padding: 0 !important;
}
  .columns {
    min-height: 750px;
    box-shadow: 0 3rem -1rem rgba(10,10,10,.2);
  }

  .lista-de-conversas {
    background: white;
  }

  .conversa-ativa {
    background: #E5DDD5;
  }

  .barra-superior {
    margin: 0;
    height: 50px;
    background: #EDEDED;
    border-right: 1px solid #E1E1E1;
    border-bottom: 1px solid rgb(200, 200, 200);
  }

  .barra-superior span {
    line-height: 50px;
    margin-left: 25px;
    font-weight: 500;
  }

  .item {
    border-bottom: 1px solid #F2F2F2;
    padding: 15px 30px;
    margin-bottom: 0 !important;
  }

  .subtitle {
    color: gray;
  }

  .item:hover {
    background: #F5F5F5;
    cursor: pointer;
  }
</style>
