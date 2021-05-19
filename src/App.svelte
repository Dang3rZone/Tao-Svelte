<script>
  //   import Error from './Error.svelte';
  //   import Spinner from './Spinner.svelte';
  // const response = getData('https://hr.oat.taocloud.org/v1/users?limit=20');
  import { getData } from "./stores.js";
  import Search from "./Search.svelte";
  import Users from "./Users.svelte";
  import Navbar from "./Navbar.svelte";
</script>

<Navbar />
<main>
  <h1>Tao's users</h1>
  <Search />
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
