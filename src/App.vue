<template>
  <div>
    <section class="section">
      <div class="container">
        <div class="columns">
          <!-- esquerda -->
          <div class="column is-3 lista-de-conversas">
            <div class="barra-superior" />
            <div class="item" v-for="conversa in conversas" :key="conversa">
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
              <span>Usuário</span>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import conversasIniciais from './dados'
export default {
  data(){
    return {
      conversas: conversasIniciais
    }
  }
}
</script>

<style scoped>
  .columns{
    min-height: 800px;
    box-shadow: 0 3rem -1rem rgba(10,10,10,.2);
  }

  .lista-de-conversas{
    background: white;
  }
  .conversa-ativa{
    background: #E5DDD5;
  }
</style>
