# svelte speedrun base%
*Goal: using svelte, hello world to a webpage*

### Leaderboards 


### Steps:
1. Create Project
2. Write in +page.svelte
3. Create +layout.svelte

### Create Project

Decide: do on webserver or local computer

Open visual studio

Open command terminal 

cd into your dev folder. 
```cd c:/dev```

```
npm create svelte@latest [name of project]
[Skeleton]
[Add typescript checking? NO]
```
The project builds.

```
cd [project name]
npm install
npm run dev -- --open
```

Open the page in the localhost address provided.

### Write in +page.svelte

Open the project in visual studio

Naviage to ```src/routes/+page.svelte```

Write ```<h1>Hello World<h1>```

See the update in the browser

Add some style to this page, such as:

```
<style>
    * {
        color:deeppink;
    }
</style>
```

### Create +layout.svelte

In ```src/routes``` create a file called ```+layout.svelte```

Refresh the webpage. It's broken!

In this new file, write ```<slot/>```

Now the content of ```+page.svelte``` renders.



