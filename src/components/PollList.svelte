<script>
    import { fade, slide, scale } from 'svelte/transition';
    import { flip } from 'svelte/animate';
//   import { onMount, onDestroy } from 'svelte';
    import PollStore from '../stores/PollStore';
    import PollDetail from "./PollDetail.svelte";
    // export let polls = [];
    
    // const unsub = PollStore.subscribe(data => {
    //     polls = data;
    // });

    // onMount(() => {
    //     // may be get data from db
    //     console.log("component mounted");
    // });

    // onDestroy(() => {
    //     // unsub from store
    //     console.log("component destroyed");
    //     unsub();
    // });

    // Unsub and sub is not required when $PollStore is used directly

</script>

<div class="poll-list">
    {#each $PollStore as poll (poll.id)}
        <div in:fade out:scale|local animate:flip={{duration: 500}}>
            <PollDetail {poll} />
        </div>
    {:else}
        <p>No Polls to show...</p>
    {/each}
</div>

<style>
    .poll-list {
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 20px;
    }
</style>