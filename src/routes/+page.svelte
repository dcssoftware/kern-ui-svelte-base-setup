<script>
  import { AppWrapper } from "$lib/components/appwrapper/index.js";
  import { Button } from "$lib/components/button/index.js";
</script>

<h1>Welcome to your library project</h1>
<p>
  Create your package using @sveltejs/package and preview/showcase your work
  with SvelteKit
</p>
<p>
  Visit <a href="https://svelte.dev/docs/kit">svelte.dev/docs/kit</a> to read the
  documentation
</p>

<AppWrapper>
  <Button
    variant="primary"
    kernIconLeft="check"
    click={() => alert("Button clicked!")}
  >
    Click Me
  </Button>
</AppWrapper>
