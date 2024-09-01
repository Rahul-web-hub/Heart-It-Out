<template>
  <div id="app">
    <header>
    </header>
    <main>
      <top-bar/>
      <section-one></section-one>
      <section-two></section-two>
      <section-three></section-three>
      <bottom-bar/>
    </main>
    <footer>
    </footer>
  </div>
</template>

<script>
import SectionOne from './components/SectionOne.vue'
import SectionTwo from './components/SectionTwo.vue'
import SectionThree from './components/SectionThree.vue'
import TopBar from './components/TopBar.vue';
import BottomBar from "./components/BottomBar.vue"

export default {
  name: 'App',
  components: {
    TopBar,
    SectionOne,
    SectionTwo,
    SectionThree,
    BottomBar,
  }
}
</script>

<style>
</style>