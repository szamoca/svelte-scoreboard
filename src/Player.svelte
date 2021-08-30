<div class="card">
    <h1>
        Hello {name}!
        <div>
            <button
                class="btn btn-sm"
                on:click={toggleControls}
            >
                {#if showControls}&and;{:else}&or;{/if}
            </button>
            <button
                class="btn btn-sm btn-danger"
                on:click={onDelete}
            >
                &times;
            </button>
        </div>
    </h1>
    <h3>Your points currently: {points}</h3>

    {#if showControls}
        <button
             class="btn btn-secondary"
             on:click={addPoint}
         >
             +1
         </button>
         <button
             class="btn btn-dark"
             on:click={removePoint}
         >
             -1
         </button>
         <input type="number" bind:value={points}>
    {/if}
</div>

<script>
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher();

    export let name;
	export let points;
	export let showControls = false;

	const addPoint = () => points++;
	const removePoint = () => points--;
    const toggleControls = () => showControls = !showControls;
    const onDelete = () => dispatch('deleteplayer', name);
</script>

<style>
	h1 {
		color: var(--primary-color);
		text-transform: uppercase;
		display: flex;
		justify-content: space-between;
	}

	h3 {
		margin-bottom: 1rem;
	}
</style>
