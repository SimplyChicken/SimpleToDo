<script>
    import '$lib/global.scss';
    import ToDoBar from "$lib/toDoBar.svelte";

    let bars = [];

    function addBar() {
        const newBar = { id: Date.now(), text: `Item ${bars.length + 1}` };
        bars = [...bars, newBar];
    }

    function removeBar(id) {
        bars = bars.filter(bar => bar.id !== id);
    }
</script>

<div class="headerDiv1">
    <div class="headerBG">
        <h1 class="headerTitle">To-Do List:</h1>
    </div>
    <button class="buttonAdd" on:click={addBar} style="display: flex; position:relative; margin-left: calc(50% - 13.5vw); align-items: center; justify-content: center;">
        <svg
        width="64"
        height="64"
        viewBox="0 0 64 64"
        >
        <line
        x1="32"
        y1="12"
        x2="32"
        y2="52"
        stroke="currentColor"
        stroke-width="8"
        stroke-linecap="round"
        />
        <line
            x1="12"
            y1="32"
            x2="52"
            y2="32"
            stroke="currentColor"
            stroke-width="8"
            stroke-linecap="round"
        />
        </svg>
    </button>
</div>

<div class="screenCenter">
    <div class="taskContainer">
        {#each bars as bar (bar.id)}
            <ToDoBar on:remove={() => removeBar(bar.id)} style="position: relative; z-index: 1;"/>
        {/each}
    </div>
</div>