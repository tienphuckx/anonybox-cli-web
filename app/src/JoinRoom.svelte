<script>
    import SharedCanvas from './SharedCanvas.svelte'; 
    export let navigate;
    let roomCode = '';
    const joinRoomHandler = () => {
        if (roomCode) {
            alert(`Joining room with code: ${roomCode}`);
        } else {
            alert('Please enter a room code.');
        }
    }
</script>

<div>
    <SharedCanvas />
    <h2>Join a Room</h2>
    <input type="text" bind:value={roomCode} placeholder="Enter room code" />
    <button on:click={joinRoomHandler}>Join Room</button>
    <button on:click={() => navigate('home')}>Back to Home</button>
</div>

<style>
    input {
        padding: 0.5rem;
        margin: 1rem 0;
        font-size: 1rem;
    }
    button {
        padding: 0.5rem 1.5rem;
        font-size: 1rem;
    }
</style>
