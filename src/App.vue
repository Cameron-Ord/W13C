<template>
  <div>
    <header class="Page_Header"><page-header></page-header></header>
    <main class="Page_Main"><song-display></song-display></main>
    <footer class="Page_Footer"><page-footer></page-footer></footer>
  </div>
</template>

<script>
import PageHeader from './components/PageHeader.vue';
import PageFooter from './components/PageFooter.vue';
import SongDisplay from './components/SongDisplay.vue';

export default {
  name: 'Layout_Page',
  components: {

    PageHeader,
    PageFooter,
    SongDisplay,

   
  }
}
</script>

<style>

*{

  padding: 0px;
  margin: 0px;
}

.Page_Header{
display: grid;
grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
min-height: 10vh;
justify-items: center;
align-items: center;
background-color: #F79824;
width: 100%;
}

.Page_Main{
display: grid;
grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
min-height: 80vh;
justify-items: center;
align-items: center;
background-color: #31393C;
width: 100%;
}

.Page_Footer{
display: grid;
grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
min-height: 10vh;
justify-items: center;
align-items: center;
background-color: #F79824;
width: 100%;
}
</style>
