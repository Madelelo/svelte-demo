# Kom i gang med svelte

I dette kurset skal vi se på følgende konsepter i Svelte

- [Kom i gang med svelte](#kom-i-gang-med-svelte)
  - [Svelte setup og syntaks](#svelte-setup-og-syntaks)
  - [Komponenter og $props()](#komponenter-og-props)
    - [$props()](#props)
    - [TODO - Props:](#todo---props)
  - [Reaktivitet med $state()](#reaktivitet-med-state)
    - [TODO state](#todo-state)
  - [IF-blokker](#if-blokker)
    - [TODO IF-blokker](#todo-if-blokker)
  - [EACH-blokker](#each-blokker)
    - [TODO EACH-blokker](#todo-each-blokker)
  - [Input og bind](#input-og-bind)
    - [TODO IF-blokker](#todo-if-blokker-1)
  - [Sider og navigasjon (routing)](#sider-og-navigasjon-routing)
  - [Tips og triks](#tips-og-triks)
  - [Ekstra snacks](#ekstra-snacks)

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

```html
<script>
  // JavaScript skrives her
  let navn = "Madeleine";
</script>

<!-- HTML skrives her med {JavaScript inni krøllparanteser} -->
<h1>Hei, {navn}!</h1>

<style>
  /* CSS for styling her */
  h1 {
    color: blue;
  }
</style>
```

Sjekk ut flere syntaks-ting i [Svelte-docs her.](https://svelte.dev/docs/svelte/basic-markup)

## Komponenter og $props()

En komponent i Svelte er en gjenbrukbar del av grensesnittet. Hver komponent har sin egen `.svelte`-fil, `+page`-filen fungerer som en index-fil. Sånn ser dette prosjektet ut:

```
svelte-demo
│   README.md
│   ...diverse andre filer
│
└───src
   │
   └───Components
   │     ...komponenter som brukes overralt
   │
   └───gamelibrary
   │      +page.svelte
   │      ...andre filer
   └───gamelist
         +page.svelte
         ...andre filer
```

### $props()

Med [props](https://svelte.dev/docs/svelte/$props) kan du sende variabler til komponentene dine. For eksempel sender dette eksempelet adjektivet `kul` fra hovedsiden `+page.svelte` til `MinKomponent`:

```html
<!-- +page.svelte -->
<script>
  import MinKomponent from "./MinKomponent.svelte";
</script>

<MinKomponent adjektiv="kul" />
```

```html
<!-- MinKomponent.svelte -->
<script>
  let { adjektiv } = $props();
</script>

<p>Denne komponenten er såååå {adjektiv}!</p>
```

**Resultat i nettleseren:**

```
Denne komponenten er såååå kul!
```

### TODO - Props:

- [ ] [Kom i gang med props](https://svelte.dev/tutorial/svelte/declaring-props)
- [ ] [Default verdier](https://svelte.dev/tutorial/svelte/default-values)
- [ ] [Pakk ut flere verdier](https://svelte.dev/tutorial/svelte/spread-props)

---

## Reaktivitet med $state()

Svelte håndterer reaktivitet automatisk med [state](https://svelte.dev/docs/svelte/$state). Hvis du vil at en variabel skal oppdatere brukergrensesnittet når den endres, bruker du en vanlig variabel med `$state()`, og Svelte vil oppdatere verdien.

Her vil `klikk` oppdatere automatisk når knappen trykkes.

```html
<script>
	let klikk = $state(0);
</script>

<button onclick={() => klikk++}>
	clicks: {klikk}
</button>
```

For eksempel hvis du har en liker-knapp og skal oppdatere antall likes. [Sjekk eksempel fra denne appen her.](https://github.com/Madelelo/svelte-demo/blob/main/src/routes/gamelist/GameLikesComponent.svelte)

### TODO state

- [ ] [Kom i gang med state](https://svelte.dev/tutorial/svelte/state)
- [ ] [Global state](https://svelte.dev/tutorial/svelte/universal-reactivity)

---

## IF-blokker

IF-blokker lar deg vise innhold basert på en if/else. For eksempel hvis du kun vil vise tekst så lenge variablene eksisterer:

```html
<script>
  let visTekst = true;
</script>

{#if visTekst}
<p>Hei, verden!</p>
{/if}
```

Hvis `visTekst` er `true`, vises teksten. Du kan også bruke `else`:

```html
{#if visTekst}
<p>Hei, verden!</p>
{:else}
<p>Teksten er skjult.</p>
{/if}
```

### TODO IF-blokker

- [ ] [IF-blokker](https://svelte.dev/tutorial/svelte/if-blocks)

---

## EACH-blokker

`{#each}`-blokker er Svelte-versjonen av for-løkker eller maps. Hvis du for eksempel skal vise like cards for alle elementer i en liste kan du bruker en `{#each}`-blokk til å lage

```html
<script>
  let spill_liste = ["Zelda", "Yatzy", "Kabal"];
</script>

<div>
  {#each spill_liste as spill}
  <SpillCardComponent spill="{spill}" />
  {/each}
</div>
```

### TODO EACH-blokker

- [ ] [EACH-blokker](https://svelte.dev/tutorial/svelte/each-blocks)

---

## Input og bind

Med bind: kan du koble sammen input-felter og visning av data. Dette betyr at en variabel automatisk oppdateres når brukeren skriver i et input-felt.

```html
<script>
  let navn = "";
</script>

<input bind:value="{navn}" placeholder="Skriv navnet ditt" />
<p>Hei, {navn}!</p>
```

Når brukeren skriver i input-feltet, vil `navn`-variabelen oppdateres automagisk. Du finner også eksempler på dette i SearchBar-funskjonaliteten.

### TODO IF-blokker

- [ ] [Text input](https://svelte.dev/tutorial/svelte/text-inputs)
- [ ] [Tall](https://svelte.dev/tutorial/svelte/numeric-inputs)
- [ ] [Checkbox](https://svelte.dev/tutorial/svelte/checkbox-inputs)
- [ ] [Grupper](https://svelte.dev/tutorial/svelte/group-inputs)

---

## Sider og navigasjon (routing)

Svelte har en innebygd funksjonalitet for routing kalt SvelteKit. I svelte er routing basert på filsystemet. Så lenge du lager en mappe med en +page.sveltefil har du en route på `/mappenavn`

For eksempel:

```
/src/routes/
  +page.svelte       # Hovedsiden
  gamelist/+page.svelte # /gamelist
  gamelibrary/+page.svelte # /gamelibrary

```

## Tips og triks

- Du kan navidere inni komponenter i VS-code med COMMAND+trykk

## Ekstra snacks

- Sjekk ut AWAIT-blokker
- Sjekk ut styling

Dette gir deg en god start på Svelte! 🚀
