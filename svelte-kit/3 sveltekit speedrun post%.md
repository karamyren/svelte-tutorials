# svelte speedrun base%
*Goal: using svelte, perform a post http request to an api*

### Leaderboards 🏆


### Steps:
1. Create Project
2. Create api-componenst folder
2. Create Post.svelte
3. Add component to App.svelte

### Create Project

see first speedrun

### Create api-components folder

see second speedrun


### Create Post.svelte

Open the project in VS Code

In the ```api-components``` folder, create file ```Post.svelte```

Write 

```javascript
<script>

let result = null
let message

async function doPost() {
    const res = await fetch('http://71.225.98.52:44000/v1/demo/audio', {
        method: 'POST',
        headers: {
        'Content-Type': 'application/json'
        },
        body: JSON.stringify({
            message: message
        })
    })
    const json = await res.json()
    result = JSON.stringify(json)
}

</script>

<h1>Post</h1>
Message: <input bind:value={message} />

<button type="button" on:click={doPost}>
    Post
</button>

<p>Result: {result}</p>

```

### Add Component to App.svelte

In ```src/routes/+page.svelte```, delete all the code in the file. 

Write

```javascript
<script>
import Post from './api-components/Post.svelte';
</script>
<Post />
```



