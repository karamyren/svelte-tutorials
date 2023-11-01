# svelte speedrun each from API%
*Goal: display a list of all dog breeds iterating through a JSON in an each loop in a webapp in svelte*

### Leaderboards 🏆


### Steps:
1. Create Project
2. Create api-components folder
3. Create FetchDogBreeds.svelte
4. Add component to App.svelte

### Create Project

see first speed run

### Create api-components folder

see second speed run

### Create FetchDogBreeds.svelte

In the ```api-components``` folder, create file ```FetchDogBreeds.svelte```

Write 

```javascript
<script>

    let promise = doGet()
    let fetchResult = []
    
    async function doGet(){
        const response = await fetch(`https://dog.ceo/api/breeds/list`)
        fetchResult = await response.json()
    }
    
    doGet()
    
</script>
    
    <h1>Fetch Dog Breeds</h1>
    
    {#await promise}
        <p>...waiting</p>
    {:then value}
         {#each fetchResult.message as breed, i}
            <ul>
                {i+1}. {breed}           
            </ul>
            <hr>
        {/each}
    {:catch error}
        <p style="color: red">{error.message}</p>
    {/await}
```

### Add Component to App.svelte

In ```src/routes/+page.svelte```, in the ```<script>``` block, write

```javascript
import FetchDogBreeds from './api-components/FetchDogBreeds.svelte';
```

Then add the component to the markup

```
<FetchDogBreeds />
```

### note:
this had a nested json too. 