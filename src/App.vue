<script lang="ts">
import { defineComponent } from 'vue';
import comidaJaponesa from '@/assets/imagens/comida-japonesa.jpg'
import BolinhaDeQueijo from '@/assets/imagens/bolinha-de-queijo.jpg'
import hamburguer from '@/assets/imagens/hamburguer.jpg'
import pizza from '@/assets/imagens/pizza.jpg'
import saladaDeFrutas from '@/assets/imagens/Salada-de-frutas.jpg'
import vinho from '@/assets/imagens/vinho.jpg'
import GaleriaItem from './components/GaleriaItem.vue'
import type { CardInfo } from './components/types';

export default defineComponent({
  name: "app",
  data() {
    return{
      descricaoGaleria: [
        {nome: "Comida Japonesa", 
         descricao: "A comida japonesa é conhecida mundialmente por sua variedade, frescor e apresentação cuidadosa. Muitos dos pratos que conhecemos hoje, como sushi e tempurá, têm origens que remontam a séculos atrás. O sushi, por exemplo, surgiu no Japão entre os séculos VIII e XIX como uma forma de conservar peixe em arroz fermentado. Já o tempurá foi introduzido no Japão por missionários portugueses no século XVI. Ao longo do tempo, a culinária japonesa evoluiu, incorporando técnicas e ingredientes próprios, e se espalhou pelo mundo, conquistando paladares com seus sabores únicos e delicados.",
         imagem: comidaJaponesa
        },
         {nome: "Bolinha De Queijo",
          descricao:  "A bolinha de queijo é um salgadinho muito popular no Brasil, especialmente em festas e lanches rápidos. Sua origem exata não é totalmente documentada, mas acredita-se que tenha surgido no país entre as décadas de 1960 e 1970, inspirada em receitas de petiscos fritos europeus e americanos. Geralmente é feita com queijo, farinha e ovos, moldada em pequenas bolinhas e frita até ficar dourada e crocante. Com o tempo, conquistou espaço em lanchonetes, festas e bares, tornando-se um verdadeiro clássico brasileiro.",
          imagem: BolinhaDeQueijo
         },
         {nome: "Hambúrguer",
          descricao: "O hambúrguer, como conhecemos hoje, surgiu no início do século XX nos Estados Unidos, mas sua inspiração veio da Alemanha, onde existia o “Hamburg steak”, um prato feito com carne moída temperada. Diversos imigrantes alemães trouxeram essa tradição para os EUA, e a ideia de colocar a carne entre dois pães começou a se popularizar. Entre os primeiros a vender o hambúrguer como sanduíche estão Louis Lassen, em Nova Iorque por volta de 1900, e os irmãos Menches, em Ohio, em 1885. Desde então, o hambúrguer conquistou o mundo e se tornou um dos alimentos mais icônicos da culinária americana.",
          imagem: hamburguer
         },
         {nome: "Pizza",
          descricao: "A pizza, como conhecemos hoje, teve sua origem em Nápoles, na Itália, no final do século XVIII. Ela surgiu como uma comida simples e popular entre os habitantes da cidade, feita com massa de pão, molho de tomate e queijo. A pizza moderna foi popularizada no início do século XX quando imigrantes italianos levaram a receita para os Estados Unidos, especialmente em cidades como Nova Iorque. Com o tempo, a pizza conquistou o mundo, ganhando diversas versões e sabores, tornando-se um dos alimentos mais queridos globalmente.",
          imagem: pizza
         },
         {nome: "Salada De Frutas",
          descricao: "A salada de frutas é um prato simples e refrescante, feito a partir da combinação de diferentes frutas frescas, cortadas em pedaços e, às vezes, temperadas com sucos ou caldas. Sua origem exata é difícil de precisar, mas registros indicam que o conceito de misturar frutas remonta à Grécia e Roma antigas, onde eram servidas como sobremesas ou acompanhamentos. No Brasil, a salada de frutas se popularizou no século XX, ganhando espaço em cafés da manhã, festas e sobremesas, tornando-se um símbolo de leveza, sabor e saúde.",
          imagem: saladaDeFrutas
         },
         {nome: "Vinho",
          descricao: "O vinho é uma das bebidas alcoólicas mais antigas do mundo, produzido a partir da fermentação da uva. Sua história remonta a cerca de 6.000 a.C., na região do atual Irã e Geórgia, onde as primeiras civilizações descobriram o processo de fermentação. Ao longo dos séculos, o vinho se espalhou pelo Egito, Grécia e Roma, tornando-se parte importante da cultura, religião e gastronomia dessas civilizações. Hoje, ele é produzido em diversas regiões do mundo, cada uma com suas variedades e tradições, sendo apreciado tanto em refeições quanto em celebrações.",
          imagem: vinho
         }  
      ] as CardInfo[],
      cardSelecionadoInfo: null as CardInfo | null
    }
  },
  components: {GaleriaItem},

  methods: {
    cardSelecionado(info: CardInfo) {
      this.cardSelecionadoInfo = info;

    }
  }
})
</script>

<template>
<div class="corpo__Card">
  <GaleriaItem v-for="(item, index) in descricaoGaleria"
  :key="index"
  :recebendo-informacoes="item"
  @card-selecionado="cardSelecionado"/>
</div>

<div v-if="cardSelecionadoInfo">
  <h2 class="detalhe__titulo">Você clicou em:</h2>
  <p class="detalhe__nome">{{ cardSelecionadoInfo.nome }}</p>
  <p class="detalhe__descricao">{{ cardSelecionadoInfo.descricao }}</p>
 
</div>
</template>


<style scoped>
.corpo__Card {
  display: flex;
  flex-wrap: wrap;
  gap: 25px;
  margin: 30px;
  justify-content: center;
}

.detalhe__Card {
  margin-top: 40px;
  padding: 25px;
  border-radius: 15px;
  background: linear-gradient(145deg, #fef9f3, #f0f4f8);
  box-shadow: 0 10px 25px rgba(0,0,0,0.1);
  max-width: 600px;
  text-align: center;
}

.detalhe__titulo {
  font-size: 1.6rem;
  color: #1f2937;
  margin-bottom: 15px;
  font-weight: 600;
}

.detalhe__nome {
  font-size: 1.3rem;
  color: #2563eb;
  font-weight: 500;
  margin-bottom: 10px;
}

.detalhe__descricao {
  font-size: 1rem;
  color: #4b5563;
  line-height: 1.6;
}

.detalhe__imagem {
  width: 100%;
  max-width: 400px;
  margin-top: 20px;
  border-radius: 12px;
  box-shadow: 0 6px 18px rgba(0,0,0,0.12);
}
</style>