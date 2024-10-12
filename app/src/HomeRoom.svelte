<script>
    import SharedCanvas from './SharedCanvas.svelte'; 
    export let navigate; // Receive navigate function as a prop
    let welcomeTxt = "Welcome to the Anonymous chat box";
</script>

<main>
    <SharedCanvas />
    
    <h1>{welcomeTxt}</h1>
    
    <div class="cre-btn">
        <button class="create-btn" on:click={() => navigate('create')}>Create a Chat Room</button>
    </div>
    <div>
        <button class="join-btn" on:click={() => navigate('join')}>Join a Room</button>
    </div>
</main>

<style>

h1 {
    text-align: center;
    color: white;
    margin-top: 20px;
}

.cre-btn {
    margin-top: 40px;
}

.create-btn {
    width: 500px;
    background-color: rgba(238,174,234,1);
    color: white;
    border: none;
    padding: 15px 30px;
    font-size: 1.2rem;
    border-radius: 8px;
    cursor: pointer;
    transition: background-color 0.3s ease, transform 0.2s ease;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.create-btn:hover {
    background-color: rgb(248, 143, 241);
    transform: scale(1.05);
}

.join-btn {
    width: 500px;
    background-color: rgba(148,187,233,1);
    color: white;
    border: none;
    padding: 15px 30px;
    font-size: 1.2rem;
    border-radius: 8px;
    cursor: pointer;
    transition: background-color 0.3s ease, transform 0.2s ease;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.join-btn:hover {
    background-color: rgb(17, 122, 171);
    transform: scale(1.05);
}

button:active {
    transform: scale(0.98);
}

button:focus {
    outline: none;
    box-shadow: 0 0 0 3px rgba(0, 140, 186, 0.5);
}

div {
    display: flex;
    gap: 20px;
    justify-content: center;
    margin-top: 5px;
}
</style>