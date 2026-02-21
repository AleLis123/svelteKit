<script lang="ts">
  import Header from '$lib/components/Header.svelte';
  import '../app.css'; // globalne style (jeśli masz)
</script>

<Header />

<main>
  <slot />
</main>

<style>
  main {
    margin-top: 80px; /* żeby header fixed nie zasłaniał treści */
  }
</style>