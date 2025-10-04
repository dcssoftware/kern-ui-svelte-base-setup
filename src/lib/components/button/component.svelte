<script lang="ts">
  // This is a placeholder Svelte component file.
  // The actual implementation of the KERN Button component is in TypeScript using LitElement.
  // Please refer to the TypeScript code below for the complete implementation.

  interface Props {
    variant?: "primary" | "secondary" | "tertiary" | "outline";
    disabled?: boolean;
    type?: "button" | "submit" | "reset";
    kernIconLeft?: string;
    kernIconRight?: string;
    block?: boolean;
    href?: string;

    click?: (event: MouseEvent) => void;

    children?: import("svelte").Snippet;
  }

  let {
    variant = "primary",
    disabled = false,
    type = "button",
    kernIconLeft = "",
    kernIconRight = "",
    block = false,
    href = "",

    click = (event: MouseEvent) => {},

    children,
  }: Props = $props();

  function handleClick(event: MouseEvent) {
    if (disabled) {
      event.preventDefault();
      event.stopPropagation();
      return;
    }

    // Navigate to URL if href is specified
    if (href && href.trim() !== "") {
      window.location.href = href;
      return;
    }

    click(event);
  }
</script>

<button
  part="button"
  class={`kern-btn kern-btn--${variant} ${block ? "kern-btn--block" : ""}`}
  {type}
  {disabled}
  onclick={handleClick}
>
  {#if kernIconLeft !== ""}
    <div class="kern-icon kern-icon--{kernIconLeft}"></div>
  {/if}

  <span class="kern-label">
    {@render children?.()}
  </span>

  {#if kernIconRight !== ""}
    <div class="kern-icon kern-icon--{kernIconRight}"></div>
  {/if}
</button>

<style lang="sass">
  .kern-btn
    display: inline-block

  .kern-btn--outline 
    background: transparent !important
    border: 1px solid transparent !important
    border-radius: var(
      --kern-metric-dimension-border-radius-sm,
      4px
    ) !important
    margin: 0
    top: -16px
    box-shadow: none !important
    min-height: auto !important
    transform: translateY(-2px)
    transform: translateX(-6px)
    color: var(--kern-color-layout-text-default, #212529)
  
  .kern-btn--outline .kern-label 
    color: var(--kern-color-layout-text-default, #212529)

  .kern-btn--outline .kern-icon 
    color: var(--kern-color-layout-text-default, #212529)
  

  .kern-btn--outline:hover 
    background: transparent !important
    box-shadow: none !important
    border: 1px solid var(--kern-color-action-border-default, #007bff) !important
    border-radius: var(
      --kern-metric-dimension-border-radius-sm,
      4px
    ) !important
  

  .kern-btn--outline:active 
    background: transparent !important
    box-shadow: none !important
    border: 1px solid var(--kern-color-action-border-default, #007bff) !important
    border-radius: var(
      --kern-metric-dimension-border-radius-sm,
      4px
    ) !important


  .kern-btn--outline:focus 
    background: transparent !important
    box-shadow: none !important
    border: 1px solid var(--kern-color-action-border-default, #007bff) !important
    border-radius: var(
      --kern-metric-dimension-border-radius-sm,
      4px
    ) !important
    outline: 2px solid var(--kern-color-action-focus-border-outside, rgba(0, 123, 255, 0.25)) !important
    outline-offset: 2px !important
  

  .kern-btn--outline:disabled 
    background: transparent !important
    opacity: 0.6;

</style>
