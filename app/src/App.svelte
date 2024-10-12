<script>
    import CreateRoom from './CreateRoom.svelte';
    import JoinRoom from './JoinRoom.svelte';
    import HomeRoom from "./HomeRoom.svelte";

    let currentPage = 'home';
</script>

<main>
	{#if currentPage === 'home'}
	<HomeRoom />
    {/if}

    {#if currentPage === 'create'}
    <CreateRoom />
    {/if}

    {#if currentPage === 'join'}
    <JoinRoom />
    {/if}
</main>

<style>
    :global(html, body) {
        margin: 0;
        padding: 0;
        height: 100%;
        width: 100%;
    }

    main {
    background-color: black;
    height: 100vh; 
    width: 100vw; 
    margin: 0;
    padding: 0;
    display: flex;
    justify-content: center;
    align-items: center;

    
    /* Radial gradient background */
    background: rgb(238,174,234);
    background: -moz-radial-gradient(circle, rgba(238,174,234,1) 0%, rgba(148,187,233,1) 100%);
    background: -webkit-radial-gradient(circle, rgba(238,174,234,1) 0%, rgba(148,187,233,1) 100%);
    background: radial-gradient(circle, rgba(238,174,234,1) 0%, rgba(148,187,233,1) 100%);
	}
</style>
