<script context="module">
  export async function load({ page, fetch, session, context }) {
    const url = `https://jsonplaceholder.typicode.com/users`;
    const res = await fetch(url);

    if (res.ok) {
      return {
        props: {
          users: await res.json(),
        },
      };
    }

    return {
      status: res.status,
      error: new Error(`Could not load ${url}`),
    };
  }
</script>

<script>
  // import Counter from '$lib/Counter.svelte';

  export let users;
</script>

<main>
  <h1>Hello world!</h1>

  <!-- <Counter /> -->

  <div class="flex p-8 flex-wrap">
    {#each users as user}
      <div class="p-8">{user.name} - {user.email}</div>
    {/each}
  </div>

  <p>
    Visit <a class="text-blue-600 underline" href="https://svelte.dev"
      >svelte.dev</a
    > to learn how to build Svelte apps.
  </p>
</main>

<style style lang="postcss">
  :root {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }

  main {
    @apply text-center;
    @apply p-4;
    @apply mx-auto;
  }

  h1 {
    @apply text-red-600;
    @apply uppercase;
    @apply text-6xl;
    @apply font-thin;
    @apply leading-tight;
    @apply my-16 mx-auto;
    @apply max-w-xs;
  }

  p {
    @apply max-w-xs;
    @apply my-8 mx-auto;
    @apply leading-snug;
  }

  @screen sm {
    h1 {
      @apply max-w-none;
    }

    p {
      @apply max-w-none;
    }
  }
</style>
