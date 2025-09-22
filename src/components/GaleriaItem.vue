<script lang="ts">
import { defineComponent } from 'vue'
import type { CardInfo } from './types'

export default defineComponent({
 props: {
    recebendoInformacoes: {type: Object as () => CardInfo, required: true}
 },
 methods:{
    cardClicado() { this.$emit('card-selecionado', this.recebendoInformacoes )

    }
 }
})
</script>

<template>
    <section class="card" @click="cardClicado">
        <img :src= "recebendoInformacoes.imagem" class="card__imagem">
 </section>
</template>


<style scoped>
.card {
  width: 250px;
  background: linear-gradient(135deg, #fdfcfb, #e2e8f0);
  border-radius: 15px;
  box-shadow: 0 8px 20px rgba(0,0,0,0.12);
  cursor: pointer;
  overflow: hidden;
  transition: transform 0.25s, box-shadow 0.25s;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 15px;
}
.card:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 25px rgba(0,0,0,0.18);
}
.card__imagem {
  width: 100%;
  border-radius: 10px;
  object-fit: cover;
  margin-bottom: 10px;
}

</style>