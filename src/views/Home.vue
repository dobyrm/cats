<template>
  <div class="home">
    <Cat />
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import Cat from '@/components/Cat.vue'; // @ is an alias to /src

@Options({
  components: {
    Cat,
  },
})
export default class Home extends Vue {}
</script>
