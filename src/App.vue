<template>
  <the-header title="Remember Me"></the-header>
  <stored-resource :resources="storedResoucevalues"></stored-resource>
</template>

<script>
import TheHeader from './components/layouts/TheHeader.vue';
import StoredResource from './components/LearningResources/StoredResource.vue';
export default {
  components: {
    TheHeader,
    StoredResource,
  },
  data() {
    return {
      storedResoucevalues: [
        {
          id: 'official guide',
          title: 'official guide',
          description: 'The official vue.js documentation',
          link: 'https://vuejs.org/',
        },
        {
          id: 'Google',
          title: 'Google',
          description: 'The official google documentation',
          link: 'https://google.com/',
        },
      ],
    };
  },
};
</script>
<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}
</style>
