<form
    class="grid-3"
    on:submit={onSubmit}
>
    <div class="form-group">
        <label for="player_name">
            Player Name
        </label>
        <input
            name="player_name"
            type="text"
            placeholder="Valami majmos legyen azért!"
            bind:value={player.name}
        >
    </div>
    <div class="form-group">
        <label for="points">Initial Points</label>
        <input
            type="number"
            name="points"
            placeholder="Player points"
            bind:value={player.points}
        >
    </div>
    <div class="form-group submit-group">
        <input
            type="submit"
            class="btn btn-primary"
            value="Add Player"
        >
    </div>
</form>

<script>
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher();

    let player = {
        name: '',
        points: 0
    };

    const onSubmit = (event) => {
        event.preventDefault();
        dispatch('addplayer', player);
        player = {
            name: '',
            points: 0
        };
    }
</script>

<style>
    input:focus {
        outline: none;
        border-color: var(--primary-color);
    }

    .form-group.submit-group {
        display: flex;
        flex-direction: column-reverse;
    }
</style>
