<script>
    import SharedCanvas from './SharedCanvas.svelte'; 
    export let navigate; // Receive the navigate function as a prop from the parent

    let roomName = '';

    const createRoomHandler = () => {
        if (roomName) {
            alert(`Room "${roomName}" has been created.`);
        } else {
            alert('Please enter a room name.');
        }
    }

</script>

<main>
    <SharedCanvas/>
    <h2>Create a Chat Room</h2>
    <input type="text" bind:value={roomName} placeholder="Enter room name" />
    <button class="create-btn" on:click={createRoomHandler}>Create Room</button>
    <button class="back-btn" on:click={() => navigate('home')}>Back to Home</button>
</main>


<style>
    /* main {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    padding: 20px;
    background-color: #f5f5f5;
} */
h2 {
    font-size: 2rem;
    color: #333;
    margin-bottom: 20px;
}

/* Styling the input field */
input[type="text"] {
    width: 300px;
    padding: 10px;
    font-size: 1rem;
    border: 2px solid #ccc;
    border-radius: 5px;
    margin-bottom: 20px;
    transition: border-color 0.3s ease;
}

input[type="text"]:focus {
    border-color: #007bff;
    outline: none;
}

/* Styling the Create Room button */
.create-btn {
    background-color: #28a745;
    color: white;
    border: none;
    padding: 10px 20px;
    font-size: 1rem;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s ease, transform 0.2s ease;
    margin-bottom: 10px;
}

.create-btn:hover {
    background-color: #218838;
    transform: scale(1.05);
}

/* Styling the Back to Home button */
.back-btn {
    background-color: #dc3545;
    color: white;
    border: none;
    padding: 10px 20px;
    font-size: 1rem;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s ease, transform 0.2s ease;
}

.back-btn:hover {
    background-color: #c82333;
    transform: scale(1.05);
}

/* Add some margin between buttons */
button {
    margin-top: 10px;
}


</style>
