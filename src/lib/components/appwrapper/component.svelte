<script lang="ts">
  import "$lib/styles/styles.css";
  import "$lib/styles/kern.css";

  interface Props {
    children?: import("svelte").Snippet;
  }

  let { children }: Props = $props();
</script>

{@render children?.()}
