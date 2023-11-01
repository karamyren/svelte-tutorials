# svelte speedrun fetch%
*Goal: using svelte, perform an http fetch request and display the result*

### Leaderboards 🏆


### Steps:
1. Create Project
2. Create api-components folder
3. Create Fetch.svelte
4. Add component to App.svelte

### Create Project

[see 1st speedrun]

### Create api-components folder

Open the project in VS Code

Within ```src```, create a folder called ```api-components```

### Create Fetch.svelte

In the ```api-components``` folder, create file ```Fetch.svelte```

Write 

```javascript
<script>

let promise = doGet()
let fetchResult

async function doGet(){
    const response = await fetch(`https://dog.ceo/api/breeds/list/random`)
    fetchResult = await response.json()
}
doGet()

</script>

<h1>Fetch</h1>

{#await promise}
    <p>...waiting</p>
{:then value}
    {JSON.stringify(fetchResult)} <br/>
    {fetchResult.message}
{:catch error}
    <p style="color: red">{error.message}</p>
{/await}

```

### Add Component to App.svelte

In ```src/routes/+page.svelte```, delete all the code in the file. 

Write

```javascript
<script>
import Fetch from '../api-components/Fetch.svelte';
</script>
<Fetch />
```

### note:
this has my favorite  ```{JSON.stringify(fetchResult)}``` hack
