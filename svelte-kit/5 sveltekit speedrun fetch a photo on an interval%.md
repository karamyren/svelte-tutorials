# svelte speedrun fetch a photo on an interval%
*Goal: using svelte, perform an http fetch request of a photo on a timer and display the result*

### Leaderboards 🏆


### Steps:
1. Create Project
2. Create api-components folder
3. Create FetchDogs.svelte
4. Add component to App.svelte

### Create Project

see first speed run

### Create api-components folder

see second speed run

### Create FetchDogs.svelte

In the ```api-components``` folder, create file ```FetchDogs.svelte```

Write 

```javascript
<script>
    import { onMount } from "svelte";
    let promise = doGet()
    let fetchResult

    let refreshTimer = 1000; //milliseconds 

    async function doGet(){
        const response = await fetch(`https://dog.ceo/api/breed/malamute/images/random`)
        fetchResult = await response.json()
    }

    onMount(() => {   
        doGet();
        const interval = setInterval(doGet, refreshTimer);
        doGet();
        return () => clearInterval(interval);
    });

</script>

<h1>Fetch</h1>

{#await promise}
    <p>...waiting</p>
{:then value}
    <img src={fetchResult.message}/>
{:catch error}
    <p style="color: red">{error.message}</p>
{/await}

```

### Add Component to App.svelte

In ```src/routes/+page.svelte```

Write

```javascript
<script>
import FetchDogs from './api-components/FetFetchDogsch.svelte';
</script>
<FetchDogs />
```

