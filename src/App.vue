<template>
  <div>
    <header class="Page_Header"><page-header></page-header></header>
    <main class="Page_Main"><page-main></page-main></main>
    <footer class="Page_Footer"><page-footer></page-footer></footer>
  </div>
</template>

<script>
import PageHeader from './components/PageHeader.vue';
import PageMain from './components/PageMain.vue';
import PageFooter from './components/PageFooter.vue';
import SongDisplay from './components/SongDisplay.vue';

export default {
  name: 'Layout',
  components: {

    PageHeader,
    PageMain,
    PageFooter,
    SongDisplay
  }
}
</script>

<style>

.Page_Header{
display: grid;
grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
min-height: 10vh;
}

.Page_Main{
display: grid;
grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
min-height: 80vh;
}

.Page_Footer{
display: grid;
grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
min-height: 10vh;
}
</style>
