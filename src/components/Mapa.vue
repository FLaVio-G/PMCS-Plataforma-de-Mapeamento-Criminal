<template>
  <v-main>
    <v-container>
      <v-row align="center">
        <v-col class="mx-auto">
          <v-sheet height="90vh" rounded="lg" id="base">
            <div>
              <GmapMap
                :center="center"
                :zoom="13"
                map-type-id="roadmap"
                style="
                  color: black;
                  width: 100%;
                  height: 90vh;
                  position: relative;
                "
              >
                <gmap-info-window
                  :options="infoOptions"
                  :position="infoWindowPos"
                  :opened="infoWinOpen"
                  @closeclick="infoWinOpen = false"
                >
                  align
                </gmap-info-window>
                <GmapMarker
                  :key="index"
                  v-for="(m, index) in markers"
                  :position="m.position"
                  :clickable="true"
                  :draggable="false"
                  @click="toggleInfoWindow(m, index)"
                />
              </GmapMap>
            </div>
          </v-sheet>
        </v-col>
      </v-row>
    </v-container>
  </v-main>
</template>

<script>
export default {
  data: () => ({
    infoWindowPos: null,
    infoWinOpen: false,
    currentMidx: null,

    infoOptions: {
      content: "",
      //optional: offset infowindow so it visually sits nicely on top of our marker
      pixelOffset: {
        width: 0,
        height: -35,
      },
    },
    center: { lat: -2.4530985799530893, lng: -54.727193366776206 },
    markers: [
      {
        position: {
          lat: -2.4437823101318985,
          lng: -54.71465330504791,
        },
        type: {
          icon: "https://developers.google.com/maps/documentation/javascript/examples/full/images/parking_lot_maps.png",
        },
        infoText: `<h2 class="title"> Ocorrências criminais </h2>
<section class="grid">
    <div class="item item-1">2020</div>
    <div class="item item-2">2021</div>
  
    <div class="item item-3">Natureza</div>
    <div class="item ">Janeiro</div>
    <div class="item ">Fevereiro</div>
    <div class="item ">Março</div>
    <div class="item ">Janeiro</div>
    <div class="item ">Fevereiro</div>
    <div class="item ">Março</div>
  
  <div class="item">Ameaça</div>
    <div class="item ">144</div>
    <div class="item ">143</div>
    <div class="item ">139</div>
    <div class="item ">133</div>
    <div class="item ">107</div>
    <div class="item ">138</div>

    <div class="item">Arrombamento</div>
    <div class="item ">60</div>
    <div class="item ">37</div>
    <div class="item ">35</div>
    <div class="item ">29</div>
    <div class="item ">37</div>
    <div class="item ">34</div>
    
    <div class="item">Desordem</div>
    <div class="item ">119</div>
    <div class="item ">101</div>
    <div class="item ">152</div>
    <div class="item ">96</div>
    <div class="item ">90</div>
    <div class="item ">97</div>

    <div class="item">Disparo de arma</div>
    <div class="item ">7</div>
    <div class="item ">8</div>
    <div class="item ">6</div>
    <div class="item ">10</div>
    <div class="item ">6</div>
    <div class="item ">3</div>

    <div class="item">Drogas ilicitas</div>
    <div class="item ">11</div>
    <div class="item ">12</div>
    <div class="item ">10</div>
    <div class="item ">21</div>
    <div class="item ">25</div>
    <div class="item ">29</div>

    <div class="item">Estelionato/fraude</div>
    <div class="item ">4</div>
    <div class="item ">2</div>
    <div class="item ">2</div>
    <div class="item ">1</div>
    <div class="item ">1</div>
    <div class="item ">3</div>

 <div class="item">Estupro</div>
    <div class="item ">1</div>
    <div class="item ">1</div>
    <div class="item ">3</div>
    <div class="item ">6</div>
    <div class="item ">1</div>
    <div class="item ">0</div>

 <div class="item">Furto</div>
    <div class="item ">12</div>
    <div class="item ">12</div>
    <div class="item ">5</div>
    <div class="item ">55</div>
    <div class="item ">43</div>
    <div class="item ">54</div>

 <div class="item">Lesão corporal</div>
    <div class="item ">112</div>
    <div class="item ">93</div>
    <div class="item ">101</div>
    <div class="item ">117</div>
    <div class="item ">101</div>
    <div class="item ">0</div>

 <div class="item">Poluição sonora / perturbação de sossego</div>
    <div class="item ">177</div>
    <div class="item ">158</div>
    <div class="item ">224</div>
    <div class="item ">350</div>
    <div class="item ">298</div>
    <div class="item ">308</div>

 <div class="item">Roubo</div>
    <div class="item ">106</div>
    <div class="item ">111</div>
    <div class="item ">106</div>
    <div class="item ">52</div>
    <div class="item ">43</div>
    <div class="item ">39</div>

 <div class="item">Violação a domicílio</div>
    <div class="item ">1</div>
    <div class="item ">3</div>
    <div class="item ">0</div>
    <div class="item ">2</div>
    <div class="item ">1</div>
    <div class="item ">0</div>

 `,
      },

      {
        position: {
          lat: -2.4374168594869525,
          lng: -54.720604110619796,
        },
        type: {
          icon: "https://developers.google.com/maps/documentation/javascript/examples/full/images/parking_lot_maps.png",
        },
        infoText: `<h2 class="title">Bairro Jardim Santarém</h2>
<section class="grid">
    <div class="item item-1">2018</div>
    <div class="item item-2">2019</div>
  
    <div class="item item-3">Natureza</div>
    <div class="item ">Janeiro</div>
    <div class="item ">Fevereiro</div>
    <div class="item ">Março</div>
    <div class="item ">Janeiro</div>
    <div class="item ">Fevereiro</div>
    <div class="item ">Março</div>
  
  <div class="item">Roubo</div>
    <div class="item ">1</div>
    <div class="item ">1</div>
    <div class="item ">1</div>
    <div class="item ">3</div>
    <div class="item ">3</div>
    <div class="item ">1</div>

    <div class="item">Homicídio</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    
    <div class="item">Estupro de Vulnerável</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>

    <div class="item">Estupro</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>

    <div class="item">Tráfico</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>

    <div class="item">Extorsão mediante a sequestro</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
</section>`,
      },
      {
        position: {
          lat: -2.4385945526804207,
          lng: -54.91645764325301,
        },
        type: {
          icon: "https://developers.google.com/maps/documentation/javascript/examples/full/images/parking_lot_maps.png",
        },
        infoText: `<h2 class="title">Praia do Ponta de pedras</h2>
<section class="grid">
    <div class="item item-1">2018</div>
    <div class="item item-2">2019</div>
  
    <div class="item item-3">Natureza</div>
    <div class="item ">Janeiro</div>
    <div class="item ">Fevereiro</div>
    <div class="item ">Março</div>
    <div class="item ">Janeiro</div>
    <div class="item ">Fevereiro</div>
    <div class="item ">Março</div>
  
  <div class="item">assalto</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div

    <div class="item">Homicídio</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div
    
    <div class="item">Estupro de Vulnerável</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div

    <div class="item">Estupro</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div

    <div class="item">Tráfico</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div

    <div class="item">Extorsão mediante a sequestro</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div`,
      },
      {
        position: {
          lat: -2.4172548674062506,
          lng: -54.84071159678977,
        },
        type: {
          icon: "https://developers.google.com/maps/documentation/javascript/examples/full/images/parking_lot_maps.png",
        },
        infoText: `<h2 class="title">Praia do Pajuçara</h2>
<table>
  <section class="grid">
    <div class="item item-1">2018</div>
    <div class="item item-2">2019</div>
  
    <div class="item item-3">Natureza</div>
    <div class="item ">Janeiro</div>
    <div class="item ">Fevereiro</div>
    <div class="item ">Março</div>
    <div class="item ">Janeiro</div>
    <div class="item ">Fevereiro</div>
    <div class="item ">Março</div>
  
  <div class="item">assalto</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div

    <div class="item">Homicídio</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div
    
    <div class="item">Estupro de Vulnerável</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div

    <div class="item">Estupro</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div

    <div class="item">Tráfico</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>

    <div class="item">Extorsão mediante a sequestro</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div`,
      },
      {
        position: {
          lat: -2.4195983709138726,
          lng: -54.8349306358766,
        },
        type: {
          icon: "https://developers.google.com/maps/documentation/javascript/examples/full/images/parking_lot_maps.png",
        },
        infoText: `<h2 class="title">Praia do Carapanari</h2>
<section class="grid">
    <div class="item item-1">2018</div>
    <div class="item item-2">2019</div>
  
    <div class="item item-3">Natureza</div>
     <div class="item ">Janeiro</div>
    <div class="item ">Fevereiro</div>
    <div class="item ">Março</div>
    <div class="item ">Janeiro</div>
    <div class="item ">Fevereiro</div>
    <div class="item ">Março</div>
  
  <div class="item">Roubo</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div

    <div class="item">Homicídio</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div
    
    <div class="item">Estupro de Vulnerável</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div

    <div class="item">Estupro</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div

    <div class="item">Tráfico</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div

    <div class="item">Extorsão mediante a sequestro</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div`,
      },
      {
        position: {
          lat: -2.5033948719234638,
          lng: -54.95469133719674,
        },
        type: {
          icon: "https://developers.google.com/maps/documentation/javascript/examples/full/images/parking_lot_maps.png",
        },
        infoText: `<h2 class="title">Distrito Alter do Chão</h2>
<section class="grid">
    <div class="item item-1">2018</div>
    <div class="item item-2">2019</div>
  
    <div class="item item-3">Natureza</div>
     <div class="item ">Janeiro</div>
    <div class="item ">Fevereiro</div>
    <div class="item ">Março</div>
    <div class="item ">Janeiro</div>
    <div class="item ">Fevereiro</div>
    <div class="item ">Março</div>
  
  <div class="item">Roubo</div>
    <div class="item ">4</div>
    <div class="item ">4</div>
    <div class="item ">0</div>
    <div class="item ">7</div>
    <div class="item ">1</div>
    <div class="item ">0</div>

    <div class="item">Homicídio</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">2</div>
    <div class="item ">1</div>
    <div class="item ">1</div>
    
    <div class="item">Estupro de Vulnerável</div>
    <div class="item ">2</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">1</div>
    <div class="item ">0</div>

    <div class="item">Estupro</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">1</div>
    <div class="item ">1</div>
    <div class="item ">0</div>

    <div class="item">Tráfico</div>
    <div class="item ">0</div>
    <div class="item ">1</div>
    <div class="item ">0</div>
    <div class="item ">1</div>
    <div class="item ">2</div>
    <div class="item ">0</div>

    <div class="item">Extorsão mediante a sequestro</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>`,
      },
      {
        position: {
          lat: -2.4214353297884728,
          lng: -54.722671335920175,
        },
        type: {
          icon: "https://developers.google.com/maps/documentation/javascript/examples/full/images/parking_lot_maps.png",
        },
        infoText: `<h2 class="title">Bairro Aldeia</h2>
<section class="grid">
    <div class="item item-1">2018</div>
    <div class="item item-2">2019</div>
  
    <div class="item item-3">Natureza</div>
    <div class="item ">Janeiro</div>
    <div class="item ">Fevereiro</div>
    <div class="item ">Março</div>
    <div class="item ">Janeiro</div>
    <div class="item ">Fevereiro</div>
    <div class="item ">Março</div>
  
  <div class="item">Roubo</div>
    <div class="item ">1</div>
    <div class="item ">1</div>
    <div class="item ">0</div>
    <div class="item ">3</div>
    <div class="item ">7</div>
    <div class="item ">2</div>

    <div class="item">Homicídio</div>
    <div class="item ">2</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">1</div>
    
    <div class="item">Estupro de Vulnerável</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">1</div>
    <div class="item ">1</div>
    <div class="item ">0</div>

    <div class="item">Estupro</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">1</div>
    <div class="item ">0</div>
    <div class="item ">0</div>

    <div class="item">Tráfico</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>

    <div class="item">Extorsão mediante a sequestro</div>
   <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>`,
      },
      {
        position: {
          lat: -2.4235551842646217,
          lng: -54.73305500868176,
        },
        type: {
          icon: "https://developers.google.com/maps/documentation/javascript/examples/full/images/parking_lot_maps.png",
        },
        infoText: `<h2 class="title">Bairro Laguinho</h2>
<section class="grid">
    <div class="item item-1">2018</div>
    <div class="item item-2">2019</div>
  
    <div class="item item-3">Natureza</div>
    <div class="item ">Janeiro</div>
    <div class="item ">Fevereiro</div>
    <div class="item ">Março</div>
    <div class="item ">Janeiro</div>
    <div class="item ">Fevereiro</div>
    <div class="item ">Março</div>
  
  <div class="item">Roubo</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">1</div>

    <div class="item">Homicídio</div>
   <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    
    <div class="item">Estupro de Vulnerável</div>
   <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    

    <div class="item">Estupro</div>
   <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>

    <div class="item">Tráfico</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>

    <div class="item">Extorsão mediante a sequestro</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>`,
      },
      {
        position: {
          lat: -2.4163868722954533,
          lng: -54.710979488736115,
        },
        type: {
          icon: "https://developers.google.com/maps/documentation/javascript/examples/full/images/parking_lot_maps.png",
        },
        infoText: `<h2 class="title">Orla da Cidade</h2>
<section class="grid">
    <div class="item item-1">2018</div>
    <div class="item item-2">2019</div>
  
    <div class="item item-3">Natureza</div>
     <div class="item ">Janeiro</div>
    <div class="item ">Fevereiro</div>
    <div class="item ">Março</div>
    <div class="item ">Janeiro</div>
    <div class="item ">Fevereiro</div>
    <div class="item ">Março</div>
  
  <div class="item">assalto</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>

    <div class="item">Homicídio</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div
    
    <div class="item">Estupro de Vulnerável</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div

    <div class="item">Estupro</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div

    <div class="item">Tráfico</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div

    <div class="item">Extorsão mediante a sequestro</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div`,
      },
      {
        position: {
          lat: -2.4187375295661666,
          lng: -54.71395836925293,
        },
        infoText: `<h2 class="title">Bairro Centro</h2>
<section class="grid">
    <div class="item item-1">2018</div>
    <div class="item item-2">2019</div>
  
    <div class="item item-3">Natureza</div>
     <div class="item ">Janeiro</div>
    <div class="item ">Fevereiro</div>
    <div class="item ">Março</div>
    <div class="item ">Janeiro</div>
    <div class="item ">Fevereiro</div>
    <div class="item ">Março</div>
  
  <div class="item">Roubo</div>
    <div class="item ">8</div>
    <div class="item ">6</div>
    <div class="item ">0</div>
    <div class="item ">9</div>
    <div class="item ">7</div>
    <div class="item ">2</div>

    <div class="item">Homicídio</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">1</div>
    <div class="item ">0</div>
    
    <div class="item">Estupro de Vulnerável</div>
    <div class="item ">0</div>
    <div class="item ">2</div>
    <div class="item ">0</div>
    <div class="item ">2</div>
    <div class="item ">2</div>
    <div class="item ">2</div>

    <div class="item">Estupro</div>
    <div class="item ">0</div>
    <div class="item ">2</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>

    <div class="item">Tráfico</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>

    <div class="item">Extorsão mediante a sequestro</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>`,
      },
      {
        position: {
          lat: -2.447948895660524,
          lng: -54.73987943234595,
        },
        infoText: `<h2 class="title">Bairro Santarenzinho</h2>
<section class="grid">
    <div class="item item-1">2018</div>
    <div class="item item-2">2019</div>
  
    <div class="item item-3">Natureza</div>
     <div class="item ">Janeiro</div>
    <div class="item ">Fevereiro</div>
    <div class="item ">Março</div>
    <div class="item ">Janeiro</div>
    <div class="item ">Fevereiro</div>
    <div class="item ">Março</div>
  
  <div class="item">Roubo</div>
    <div class="item ">10</div>
    <div class="item ">8</div>
    <div class="item ">0</div>
    <div class="item ">26</div>
    <div class="item ">25</div>
    <div class="item ">20</div>

    <div class="item">Homicídio</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">1</div>
    <div class="item ">1</div>
    <div class="item ">0</div>
    
    <div class="item">Estupro de Vulnerável</div>
    <div class="item ">0</div>
    <div class="item ">2</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">2</div>
    <div class="item ">0</div>

    <div class="item">Estupro</div>
    <div class="item ">1</div>
    <div class="item ">1</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">0</div>
    <div class="item ">1</div>

    <div class="item">Tráfico</div>
    <div class="item ">4</div>
    <div class="item ">2</div>
    <div class="item ">1</div>
    <div class="item ">4</div>
    <div class="item ">0</div>
    <div class="item ">3</div>

    <div class="item">Extorsão mediante a sequestro</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>
    <div class="item ">-</div>`,
      },
    ],

    model: 1,
  }),
  methods: {
    toggleInfoWindow: function (marker, idx) {
      this.infoWindowPos = marker.position;
      console.log(marker.infoText);
      this.infoOptions.content = marker.infoText;

      //check if its the same marker that was selected if yes toggle
      if (this.currentMidx == idx) {
        this.infoWinOpen = !this.infoWinOpen;
      }
      //if different marker set infowindow to open and reset current marker index
      else {
        this.infoWinOpen = true;
        this.currentMidx = idx;
      }
    },
  },
};
</script>
<style >
strong {
  color: black !important;
}
.title {
  text-align: center;
}
b {
  font-weight: bold;
}
tr:nth-child(even) {
  background-color: #dddddd;
}
.grid {
  display: grid;
  grid-template-columns: repeat(7, 1fr);
  gap: 5px;
}
.item-1 {
  grid-column: 2/5;
}
.item-2 {
  grid-column: -1/5;
}
.item {
  text-align: center;
  font-size: 20px;
  padding: 8px;
  border: 1px solid #dddddd;
}
</style>