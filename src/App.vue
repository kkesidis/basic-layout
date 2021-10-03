<template>
  <div id="app">
    <Layout>
      <HelloWorld />
    </Layout>
  </div>
</template>

<script>
import Layout from './components/Layout.vue';
import HelloWorld from './components/HelloWorld.vue';

export default {
  name: 'App',
  components: {
    Layout,
    HelloWorld,
  },
}
</script>
