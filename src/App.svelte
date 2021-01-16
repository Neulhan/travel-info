<script>
  import Main from "./components/Main.svelte";
  import Map from "./components/map/Main.svelte";
  import List from "./components/list/Main.svelte";
  import { Router, Route } from "svelte-routing";

</script>

<Router>
  <Route path="/list" component={Main}></Route>
  <Route path="/map" component={Map}></Route>
  <Route path="" component={List}></Route>
</Router>
