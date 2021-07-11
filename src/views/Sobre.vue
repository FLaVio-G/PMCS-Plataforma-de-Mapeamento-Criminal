<template>
  <v-card
    class="mt-12 mx-auto my-auto"
    width="800"
  > <v-card-title>SOBRE PMCS</v-card-title>
    <v-card-text>
     
      
      <div class="text--primary text-justify">
        
O sistema utiliza as ocorrências criminais fornecidas pelo Núcleo Integrado de Operações – NIOP na qual fornece dados gerais da cidade incluindo:  Poluição sonora, Roubo, Desordem, Lesão Corporal, Furto, Arrombamento, Drogas Ilícitas, Violação a domicílio, Homicídio, Estupro. Além desse conjunto de dados, temos o apoio da Superintendência Regional do baixo Amazonas, fornecendo informações por localidade, sendo elas: Jardim Santarém, Santarenzinho, Centro, Aldeia, Laguinho, Distrito de Alter do Chão. Incluindo também os pontos turísticos da Praia do Carapanari, Pajuçara e Ponta de Pedras.<br/>
Os dados Fornecidos pelos Órgãos citados acima são referentes aos 3 meses iniciais de 2018 e 2019.

O Mapeamento Criminal Santareno - MCS foi desenvolvido pelo acadêmico Flávio Gabriel de Andrade Viana, pertencente ao seu Trabalho de Conclusão de Curso, do curso de Bacharel de Sistemas de Informação<br/><br/>
Menção Honrosa:<br/>
Orientadora Dr. Marla Geller<br/>
Acadêmico de direito Hugo Fernandez <br/>
Desenvolvedor de Software Pleno Luan Ferreira<br/>
Acadêmico de Sistemas de Informação  Diego Fernandez<br/>
Acadêmico de Ciência da Computação Paulo Beckman<br/>
      </div>
    </v-card-text>
    <v-expand-transition>
      <v-card
        v-if="reveal"
        class="transition-fast-in-fast-out v-card--reveal"
        style="height: 100%;"
      >
        <v-card-text class="pb-0">
          <p class="text-h4 text--primary">
            Origin
          </p>
          <p>late 16th century (as a noun denoting a place where alms were distributed): from medieval Latin eleemosynarius, from late Latin eleemosyna ‘alms’, from Greek eleēmosunē ‘compassion’ </p>
        </v-card-text>
        <v-card-actions class="pt-0">
          <v-btn
            text
            color="teal accent-4"
            @click="reveal = false"
          >
            Close
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-expand-transition>
  </v-card>
</template>
