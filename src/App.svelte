<script>
	import Main from "./components/Main.svelte";
	import Map from "./components/map/Main.svelte";
	import List from "./components/list/Main.svelte";
	import { Router, Route } from "svelte-routing";
</script>

<Router>
	<Route path="/list/:city" component={List} let:city />
	<Route path="/map" component={Map} />
	<Route path="" component={Main} />
</Router>
