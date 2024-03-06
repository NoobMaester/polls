<script>
    import PollDetails from "./PollDetails.svelte";
    export let polls = [];
</script>

<div class='poll-list'>
    {#each polls as poll (poll.id)}
        <PollDetails {poll} on:vote/>
    {/each}
</div>

<style>
    .poll-list{
        margin: 5rem;
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 1rem;
    }
    @media(max-width:800px){
        .poll-list{
            grid-template-columns: 1fr;
        }
    }
</style>