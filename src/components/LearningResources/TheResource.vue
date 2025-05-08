<template>
  <base-card>
    <base-button
      @click="setSelectedTab('stored-resource')"
      :mode="storedResButtonMode"
    >
      Stored Resources
    </base-button>
    <base-button
      @click="setSelectedTab('add-resource')"
      :mode="addResButtonMode"
      >Add Resource</base-button
    >
  </base-card>
  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
</template>

<script>
import StoredResource from './StoredResource.vue';
import AddResource from './AddResource.vue';
export default {
  components: {
    StoredResource,
    AddResource,
  },
  data() {
    return {
      selectedTab: 'stored-resource',
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
  provide() {
    return {
      resources: this.storedResoucevalues,
      addResource: this.AddResource,
      removeResource: this.removeResource,
    };
  },
  computed: {
    storedResButtonMode() {
      return this.selectedTab === 'stored-resource' ? null : 'flat';
    },
    addResButtonMode() {
      return this.selectedTab === 'add-resorce' ? null : 'flat';
    },
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    AddResource(title, description, url) {
      const newResource = {
        id: new Date().toISOString(),
        title: title,
        description: description,
        link: url,
      };
      this.storedResoucevalues.unshift(newResource);
      this.selectedTab = 'stored-resource';
    },
    removeResource(resId) {
      const resindex = this.storedResoucevalues.findIndex(
        (res) => res.id === resId
      );
      this.storedResoucevalues.splice(resindex, 1);
    },
  },
};
</script>
