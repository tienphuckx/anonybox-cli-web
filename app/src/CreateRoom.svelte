<script>
    let roomName = '';

    const createRoomHandler = () => {
        if (roomName) {
            alert(`Room "${roomName}" has been created.`);
        } else {
            alert('Please enter a room name.');
        }
    }
</script>

<div>
    <h2>Create a Chat Room</h2>
    <input type="text" bind:value={roomName} placeholder="Enter room name" />
    <button on:click={createRoomHandler}>Create Room</button>
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
