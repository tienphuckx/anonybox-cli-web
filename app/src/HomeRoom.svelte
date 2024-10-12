<script>
    import { onMount } from "svelte";
	let welcomeTxt = "Welcome to the Anonymous chat box";
    let canvas;

    const navigate = (page) => {
        currentPage = page;
    }

    onMount(() => {
        const ctx = canvas.getContext('2d');
        let frame;

        (function loop() {
            frame = requestAnimationFrame(loop);

            const imageData = ctx.getImageData(0, 0, canvas.width, canvas.height);

            for (let p = 0; p < imageData.data.length; p += 4) {
                const i = p / 4;
                const x = i % canvas.width;
                const y = (i / canvas.height) >>> 0;

                const t = window.performance.now();

                const r = 64 + (128 * x) / canvas.width + 64 * Math.sin(t / 1000);
                const g = 64 + (128 * y) / canvas.height + 64 * Math.cos(t / 1400);
                const b = 128;

                imageData.data[p + 0] = r;
                imageData.data[p + 1] = g;
                imageData.data[p + 2] = b;
                imageData.data[p + 3] = 255;
            }

            ctx.putImageData(imageData, 0, 0);
        })();

        return () => {
            cancelAnimationFrame(frame);
        };
    });
</script>


<main>
    <!-- Logo canvas -->
    <canvas bind:this={canvas} width={200} height={200}></canvas>
    
    <!-- Welcome text -->
    <h1>{welcomeTxt}</h1>
    
    <!-- Buttons -->
    <div class="cre-btn">
        <button class="create-btn" on:click={() => navigate('create')}>Create a Chat Room</button>
    </div>
    <div>
        <button class="join-btn" on:click={() => navigate('join')}>Join a Room</button>
    </div>
</main>


<style>
canvas {
    display: block;
    margin: 0 auto;
    width: 150px;
    height: 150px;
    background-color: #666;
    -webkit-mask: url('data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0idXRmLTgiPz4KCjwhLS0gTGljZW5zZTogR1BMLiBNYWRlIGJ5IG5hZ29zaGlhc2h1bWFyaTogaHR0cHM6Ly9naXRodWIuY29tL25hZ29zaGlhc2h1bWFyaS9ScGctQXdlc29tZSAtLT4KPHN2ZyBmaWxsPSIjMDAwMDAwIiB3aWR0aD0iODAwcHgiIGhlaWdodD0iODAwcHgiIHZpZXdCb3g9IjAgMCAzMiAzMiIgdmVyc2lvbj0iMS4xIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciPgo8dGl0bGU+Y2F0PC90aXRsZT4KPHBhdGggZD0iTTI4LjkyNiAxLjE3bC0yLjE4MiAzLjYwOGMtMS44NzYtMC42MDgtNC42NjktMC40ODktNi40MjYgMGwtMi4xMDItMy41NTdjLTMuNDUyIDYuNDQ4LTIuNDc1IDEwLjUyMyAwLjE1OSAxMi41NDktMC40MDMgMC4yNTItMC44MTggMC41MjktMS4yNDcgMC44MzMtMTAuOTc5LTguNzU5LTIwLjg2MyAxLjEwNi0xNC4zNzkgOS45MmgwLjA1MGMxLjE2MyAxLjY4NyAyLjUwMyAyLjczMSAzLjk1IDMuMjc3IDIuMDUwIDAuNzczIDQuMTU5IDAuNTUxIDYuMjM2IDAuMjU3czQuMTA5LTAuNjYzIDYuMDQ2LTAuNTI1YzEuOTM3IDAuMTM4IDMuODc0IDAuNjM1IDUuNjQ3IDIuNTY5IDEuMjA5IDEuMzE4IDIuOTI2LTAuMTAxIDEuNDg2LTEuNTA3LTIuMTg1LTIuMTM0LTQuNTI1LTIuOTU5LTYuODI1LTMuMTIycy00LjUwNSAwLjI5My02LjUwMiAwLjU3NmMtMS45OTcgMC4yODMtMy43NjEgMC40MDktNS4yNzYtMC4xNjMtMC43MTEtMC4yNjgtMS40MDMtMC42OS0yLjA3MC0xLjM2aDIyLjUxYzEuMDY0LTMuNzU2IDEuMTc3LTcuNzMtMC4wMzMtMTAuMjM3IDMuNjM1LTEuODk3IDUuMDk3LTYuMzc2IDAuOTU4LTEzLjExNnpNMjIuMTc2IDEwLjg3MmMtMi4zMTYgMS4xMTctMy4zNjcgMC4yMTItMy44MTctMS42NTYgMi4yNzMtMS40MSAzLjYyNi0wLjI3OCAzLjgxNyAxLjY1NnpNMjUuMDY3IDEwLjg3MmMwLjE5MS0xLjkzNCAxLjU0NC0zLjA2NyAzLjgxNy0xLjY1Ni0wLjQ1IDEuODY4LTEuNTAyIDIuNzc0LTMuODE3IDEuNjU2eiI+PC9wYXRoPgo8L3N2Zz4=') 50% 50% no-repeat;
    mask: url('data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0idXRmLTgiPz4KCjwhLS0gTGljZW5zZTogR1BMLiBNYWRlIGJ5IG5hZ29zaGlhc2h1bWFyaTogaHR0cHM6Ly9naXRodWIuY29tL25hZ29zaGlhc2h1bWFyaS9ScGctQXdlc29tZSAtLT4KPHN2ZyBmaWxsPSIjMDAwMDAwIiB3aWR0aD0iODAwcHgiIGhlaWdodD0iODAwcHgiIHZpZXdCb3g9IjAgMCAzMiAzMiIgdmVyc2lvbj0iMS4xIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciPgo8dGl0bGU+Y2F0PC90aXRsZT4KPHBhdGggZD0iTTI4LjkyNiAxLjE3bC0yLjE4MiAzLjYwOGMtMS44NzYtMC42MDgtNC42NjktMC40ODktNi40MjYgMGwtMi4xMDItMy41NTdjLTMuNDUyIDYuNDQ4LTIuNDc1IDEwLjUyMyAwLjE1OSAxMi41NDktMC40MDMgMC4yNTItMC44MTggMC41MjktMS4yNDcgMC44MzMtMTAuOTc5LTguNzU5LTIwLjg2MyAxLjEwNi0xNC4zNzkgOS45MmgwLjA1MGMxLjE2MyAxLjY4NyAyLjUwMyAyLjczMSAzLjk1IDMuMjc3IDIuMDUwIDAuNzczIDQuMTU5IDAuNTUxIDYuMjM2IDAuMjU3czQuMTA5LTAuNjYzIDYuMDQ2LTAuNTI1YzEuOTM3IDAuMTM4IDMuODc0IDAuNjM1IDUuNjQ3IDIuNTY5IDEuMjA5IDEuMzE4IDIuOTI2LTAuMTAxIDEuNDg2LTEuNTA3LTIuMTg1LTIuMTM0LTQuNTI1LTIuOTU5LTYuODI1LTMuMTIycy00LjUwNSAwLjI5My02LjUwMiAwLjU3NmMtMS45OTcgMC4yODMtMy43NjEgMC40MDktNS4yNzYtMC4xNjMtMC43MTEtMC4yNjgtMS40MDMtMC42OS0yLjA3MC0xLjM2aDIyLjUxYzEuMDY0LTMuNzU2IDEuMTc3LTcuNzMtMC4wMzMtMTAuMjM3IDMuNjM1LTEuODk3IDUuMDk3LTYuMzc2IDAuOTU4LTEzLjExNnpNMjIuMTc2IDEwLjg3MmMtMi4zMTYgMS4xMTctMy4zNjcgMC4yMTItMy44MTctMS42NTYgMi4yNzMtMS40MSAzLjYyNi0wLjI3OCAzLjgxNyAxLjY1NnpNMjUuMDY3IDEwLjg3MmMwLjE5MS0xLjkzNCAxLjU0NC0zLjA2NyAzLjgxNy0xLjY1Ni0wLjQ1IDEuODY4LTEuNTAyIDIuNzc0LTMuODE3IDEuNjU2eiI+PC9wYXRoPgo8L3N2Zz4=') 50% 50% no-repeat;
    mask-size: contain;
}

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