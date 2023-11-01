# svelte refresh on a timer%
*Goal: using svelte, refresh the page using a timer*

### Leaderboards 🏆


### Steps:
1. Create Project
2. Create Refresh.svelte
3. Add component to App.svelte

### Create Project

see first speed run

### Create Refresh.svelte


```javascript
<script>
    import { onMount } from 'svelte';

    let refreshTimer = 1000; //milliseconds 

    let pets = [
        {name: 'lulu'},
        {name: 'grey kitty'},
        {name: 'lulu'},
        {name: 'lulu'}
    ]

    let pet 
 
    async function getRandomPet (){
        pet = pets[Math.floor(Math.random() * (5))].name
    }  

    onMount(() => {   
        getRandomPet();
        const interval = setInterval(getRandomPet, refreshTimer);
        getRandomPet();
        return () => clearInterval(interval);
    });
</script>

Pet of the Month is <b>{pet}</b>
```