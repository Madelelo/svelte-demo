# Kom i gang med svelte

I dette kurset skal vi se på følgende konsepter i Svelte

- Basic svelte setup
- Komponenter og syntaks
- state og props
- IF-blokker
- EACH-blokker
- Bind:
- Routing
- Ekstra snacks: AWAIT-blokker, styling, ..

## Svelte setup og syntaks

Åpne iTerm og naviger til mappen hvor du lagrer repositoriene dine. Inne i denne mappen, opprett en mappe for Svelte-prosjektet ditt. For eksamepl `svelte-demo`

```bash
# lager et nytt svelte-prosjekt
npx sv create

# installerer alle svelte-pakker
npm install

# kjører svelte-appen din
npm run dev

```

Svelte bruker en kombinasjon av HTML, CSS og JavaScript i samme fil. Her er et eksempel:

```svelte
<script>
    let navn = "Madeleine";
</script>

<h1>Hei, {navn}!</h1>

<style>
    h1 {
        color: blue;
    }
</style>
```

- `{navn}` brukes for å flette JavaScript-variabler inn i HTML.
- `<style>`-blokken definerer CSS som kun gjelder for denne komponenten.

Sjekk ut flere syntaks-ting i [documentasjonen](https://svelte.dev/docs/svelte/basic-markup)

## Komponenter og $props()

En komponent i Svelte er en gjenbrukbar del av brukergrensesnittet. Hver komponent har sin egen `.svelte`-fil og kan inneholde HTML, CSS og JavaScript.

TODO: forklaring av fil og komponentstrukturen i game-librar

### Props

Med [Props](https://svelte.dev/docs/svelte/$props) kan du sende variabler til komponentene dine. For eksempel sender dette eksempelet adjektivet `kul` fra hovedsiden `+page.svelte` til `MinKomponent`:

```svelte
<!-- +page.svelte -->
<script>
    import MinKomponent from './MinKomponent.svelte';
</script>

<MinKomponent adjektiv="kul" />
```

```svelte
<!-- MinKomponent.svelte -->
<script>
    export let adjektiv;
</script>

<p>Denne komponenten er såååå {adjektiv}!</p>
```

**Resultat i nettleseren:**

```
Denne komponenten er såååå kul!
```

## Reaktivitet med $state()

Svelte håndterer reaktivitet automatisk med [state](https://svelte.dev/docs/svelte/$state). Hvis du vil at en variabel skal oppdatere brukergrensesnittet når den endres, bruker du en vanlig variabel med `$state()`, og Svelte vil oppdatere verdien.

Her vil `count` oppdatere automatisk når knappen trykkes.

```svelte
<script>
    let count = 0;

    function increment() {
        count += 1;
    }
</script>

<button on:click={increment}>Klikk meg</button>
<p>Antall klikk: {count}</p>
```

For eksempel hvis du har en liker-knapp og skal oppdatere antall likes. [Sjekk eksempel fra Gamelibrary her.](https://github.com/Madelelo/svelte-demo/blob/main/src/routes/gamelist/GameLikesComponent.svelte)

### IF-blokker

IF-blokker lar deg vise innhold basert på if/else. For eksempel hvis du kun vil vise tekst så lenge variablene eksisterer:

```svelte
<script>
    let visTekst = true;
</script>

{#if visTekst}
    <p>Hei, verden!</p>
{/if}
```

Hvis `visTekst` er `true`, vises teksten. Du kan også bruke `else`:

```svelte
{#if visTekst}
    <p>Hei, verden!</p>
{:else}
    <p>Teksten er skjult.</p>
{/if}
```

### EACH-blokker

EACH-blokker brukes for å gjenta innhold basert på en liste og er en slags for-løkke.

```svelte
<script>
    let frukter = ['Eple', 'Banan', 'Appelsin'];
</script>

<ul>
    {#each frukter as frukt}
        <li>{frukt}</li>
    {/each}
</ul>
```

## Input og bind:

Med Bind: kan du koble sammen input-felter og visning av data. Dette betyr at en variabel automatisk oppdateres når brukeren skriver i et input-felt.

```svelte
<script>
    let navn = "";
</script>

<input bind:value={navn} placeholder="Skriv navnet ditt" />
<p>Hei, {navn}!</p>
```

Når brukeren skriver i input-feltet, vil `navn`-variabelen oppdateres automagisk.

## Sider og navigasjon (routing)

SvelteKit har innebygd routing basert på filsystemet.

For eksempel:

```
/src/routes/
  +page.svelte       # Hovedsiden
  about/+page.svelte # /about
```

Navigasjon mellom sider:

```svelte
<a href="/about">Gå til About</a>
```

Eller med `<Link>`-komponenten fra SvelteKit:

```svelte
<script>
    import { goto } from '$app/navigation';
</script>

<button on:click={() => goto('/about')}>Gå til About</button>
```

## Ekstra snacks

### AWAIT-blokker

Await brukes for asynkrone operasjoner, for eksempel API-kall.

```svelte
<script>
    let dataPromise = fetch('https://jsonplaceholder.typicode.com/posts/1')
        .then(response => response.json());
</script>

{#await dataPromise}
    <p>Laster...</p>
{:then data}
    <h1>{data.title}</h1>
    <p>{data.body}</p>
{/await}
```

### Styling

Hver `.svelte`-fil har en `<style>`-blokk som kun gjelder for den komponenten.

```svelte
<style>
    p {
        color: red;
    }
</style>
```

Svelte gir også mulighet for globale CSS-regler og CSS-moduler.

---

Dette gir deg en god start på Svelte! 🚀
