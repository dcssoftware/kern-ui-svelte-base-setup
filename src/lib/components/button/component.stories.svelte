<script module>
  import { defineMeta } from "@storybook/addon-svelte-csf";

  import "$lib/styles/styles.css";
  import "$lib/styles/kern.css";
  import Button from "./component.svelte";

  export const ComponentData = {};

  const { Story } = defineMeta({
    component: Button,
    title: "Button",
    tags: ["autodocs"],
    excludeStories: /.*Data$/,
    args: {
      type: "button",
      disabled: false,
      variant: "primary",
      kernIconLeft: "check",
    },
  });
</script>

{#snippet ExampleText()}
  <p>Hello World</p>
{/snippet}

<Story name="Default" args={{ task: ComponentData, children: ExampleText }} />
