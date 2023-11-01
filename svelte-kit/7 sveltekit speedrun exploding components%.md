# svelte speedrun use variabe from a store%
*Goal: write to a variable in one svelte script, use the variable in another svelte script*

### Leaderboards 🏆


### Steps:
1. Create Project
2. Create folders
3. Create datamodel.js
4. Create breed variable
5. Create FetchRandomBreed.svelte
6. Create dogImage variable
6. Create DisplayBreedImage.svelte
7. Add files to App.svelte
8. Create Button to do a new one
9. Make the variables reactive here?
10. Add component to App.svelte


### Create Project

see first speed run

### Create folders

Open the project in VS Code

Within ```src```, create a folder called ```api-components```

Within ```src```, create a folder called ```api-scripts```

Within ```src```, create a folder called ```cards```


### Create datamodel.js

In the ```api-scripts``` folder, create file ```datamodel.js```


### Create breed variable

In ```datamodel.js```, write

```javascript
import { writable } from 'svelte/store'

export const breed = writable([]);
```

### Create FetchRandomBreed.svelte

In the ```api-components``` folder, create file ```FetchRandomBreed.svelte```

Write 

```javascript
<script>
import { breed } from '../lib/datamodel.js';

async function doGet(){
    const response = await fetch(`https://dog.ceo/api/breeds/list/random`)
    $breed = await response.json()
}

doGet()

</script>
```

### Create dogImage variable

In ```datamodel.js```, write

```javascript
import { writable } from 'svelte/store'

export const dogImage = writable([]);
```


### FetchBreedImage.svelte

In the ```api-components``` folder, create file ```FetchRandomBreed.svelte```

Write 

```javascript
<script>
    import { breed } from '../lib/datamodel.js';
    import { dogImage } from '../lib/datamodel.js';

    async function doGet(dog){
        const response = await fetch(`https://dog.ceo/api/breed/${dog}/images/random`)
        $dogImage = await response.json()
    }
    
    $: doGet($breed.message)

</script>
```

(it's important that $breed.message is in the reactivity line, when that changes the line will know to rerun. If it's not passed in as a variable there, but is instead just in the fetch, the line wont re run.)


### Create DisplayBreedImage.svelte


In the ```cards``` folder, create file ```DisplayBreedImage.svelte```

Write 

```javascript
<script>
    import { dogImage } from '../lib/datamodel.js'; 
    let thisDog;
    $: thisDog = $dogImage;
</script>

{#if $dogImage}
    <img src={$dogImage.message}/>
{/if}
```

### Add Component to App.svelte

In ```App.svelte```, in the ```<script>``` block, write

```javascript
<script>
  import FetchRandomBreed from './api-components/FetchRandomBreed.svelte';
  import FetchBreedImage from "./api-components/FetchBreedImage.svelte";
  import DisplayBreedImage from './cards/DisplayBreedImage.svelte';
</script>

<FetchRandomBreed />
<FetchBreedImage />
<DisplayBreedImage />
```



