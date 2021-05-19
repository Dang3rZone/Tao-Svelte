<script>
  import { Router, Link, Route } from "svelte-routing";
  import Search from "./Search.svelte";
  import Users from "./Users.svelte";
  import Navbar from "./Navbar.svelte";
  import View from "./View.svelte";
</script>

<Navbar />
<main>
  <h1>Tao's users</h1>
  <Search />
  <h2>- All Users -</h2>
  <div class="grid-3">
    <Users />
  </div>
</main>

<style>
  main {
    align-items: center;
    display: flex;
    flex-direction: column;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 2em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
