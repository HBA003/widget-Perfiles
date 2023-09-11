<template>
  <div>
    <header-component />
  </div>
  <!-- Button trigger modal -->
</template>

<script>
import { mapState, mapActions } from 'vuex';
import { usePostsStore } from '@/stores/posts';
import liquidParser from './liquid/liquidParser';
import HeaderComponent from './components/header/HeaderComponent.vue';
export default {
  name: 'App',
  components: {
    HeaderComponent
  },
  data() {
    return {
      year: new Date().getFullYear(),
      siteName: liquidParser.parse('{{site.name | replace: "my", "your" | upcase }}'),
      basePath: liquidParser.parse('{{vars.base_path}}'),
      imagen: liquidParser.parse("{{ 'c94b0179-dba8-43de-ad57-8ce995b53a9e' | asset_image}}"),
    };
  },
  computed: {
    ...mapState(usePostsStore, ['posts']),
  },
  async created() {
    this.getPosts();
  },
  methods: {
    ...mapActions(usePostsStore, ['getPosts']),
  },
};
</script>
<style lang="scss">
  @import "scss/variables";
  @import "~bootstrap";
</style>

<style lang="scss" scoped>
@use "sass:color";

#app {
  ::v-deep {
    .jorge {
      position: block;
      width: 100;
      padding: 0;
      color: red;
    }
  }
}
</style>