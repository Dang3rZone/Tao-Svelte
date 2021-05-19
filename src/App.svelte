<script>
  import { Router, Link, Route } from "svelte-routing";

  import Home from "./Home.svelte";
  import Users from "./Users.svelte";
  import View from "./View.svelte";

  export let url = "";
</script>

<Router {url}>
  <!-- <nav>
    <Link to="user">Users</Link>
  </nav> -->
  <div>
    <Route path="user" component={Users} />
    <Route path="user/:id" component={View} let:params />
    <Route path="/"><Home /></Route>
  </div>
</Router>
