<template>
  <div class="container flex column">
    <Top/>
    <Main/>
    <Rrss/>
    <Bottom/>
  </div>
</template>

<script>
import Top from './components/top.vue'
import Main from './components/main.vue'
import Rrss from './components/rrss.vue'
import Bottom from './components/bottom.vue'

export default {
  name: 'App',
  components: {
    Top, Main, Rrss, Bottom
  }
}
</script>

<style>
/* ESTILOS GENERALES */
@font-face{
    font-family: 'IngeText';
    src: url('./assets/fonts/WEB_QuestrialFont/Questrial-Regular.ttf') format('truetype');
}
@font-face {
    font-family: 'IngeTextBold';
    src: url('./assets/fonts/WEB_CentraleSans-Bold/CentraleSans-Bold.woff') format('woff');
}
@font-face {
    font-family: 'IngeTextFut';
    src: url('./assets/fonts/Futura/FutuLt__.ttf') format('truetype');
}
*{
  margin:0;
  padding:0;
  box-sizing: border-box;
  font-family: 'IngeText';
}
.title{
  font-family: 'IngeTextBold', sans-serif;
}
.futura{
  font-family: 'IngeTextFut';
}
:root{
  --light-lilac:#D2DDEB;
  --lilac: #9FB3E3;
  --dark-lilac: #7A9AC7; 
  --bluish-green: #0C7F7E;
  --dark-bluish-green: #1E6595;
  --blue: #112576;
  --dark-blue: #0A1F42;
  --eshop-color: #092146;
  --gray: #677A8B;
  --dark-gray:#4f4f4f;
  --light-gray: #e1e1e1;
  --shadow: hsl(0 0% 50% / 0.4);
  --shadow-lilac: hsl(215 42% 50% / 0.7);
  --shadow-blue: hsl(228 73% 5% / 0.6);
  --primary-color: #0071fe;
  --error-color: #f23648;
  --error-bg-color: #fddfe2;
  --success-color: #21a67a;
  --success-bg-color: #e0eee4;
}
.flex{
  display: flex;
}
.column{
  flex-direction: column;
}
.wrap{
  flex-wrap: wrap;
}

/* ESTILOS DE ESTE ARCHIVO */
.container{
  width: 100%;
}


/* MEDIA QUERIES */
  /* Para tablets   */
  @media screen and (min-width: 768px) {
  }

  /* Para pantallas mas grandes */
  @media screen and (min-width: 1024px) {
  }
  @media screen and (min-width: 1200px) {
  }
</style>
