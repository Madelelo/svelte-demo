<script>
import Navbar from "./Navbar.svelte";
import QueueCard from "./QueueCard.svelte";

let name = "Madeleine";
let color = "blue";

let queue = ["Madeleine", "Magnus", "Fredrik"]

let count = 0;

function countClicks(){
        count += 1;
}

</script> 
<!-- HTML--> 

<Navbar/>

<h1 style="color:{color}"> Hello {name} </h1>

<button on:click={countClicks}> Click me</button>
<p> Button clicked {count} times! </p>

{#if count > 10}
    <p id="nice"> Nice Work {name}</p>
{/if}

{#each queue as name}
        <QueueCard  name={name}/>
{/each}

<style> 
#nice{
        color: green;
}
</style>
