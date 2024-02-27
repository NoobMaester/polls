<script>
    
    import {createEventDispatcher} from 'svelte'
    const dispatch = createEventDispatcher();

    export let items;
    export let activeItem;

</script>

<div class='tabs'>
    <ul>
        {#each items as item}
        <!-- svelte-ignore a11y-click-events-have-key-events -->
        <li on:click={() => dispatch('tabChange', item)}>
          <div class:active={item === activeItem}>{item}</div>
        </li>
        {/each}
    </ul>
</div>

<style>
    .tabs{
        margin-bottom: 4rem;
    }
    ul{
        display: flex;
        justify-content: center;
        padding: 0;
        list-style: none;
    }
    li{
        margin: 0 1.6rem;
        font-size: 18px;
        color: #555;
        cursor: pointer;
    }
    .active{
        color:blueviolet;
        border-bottom: 2px solid blueviolet;
        padding-bottom: 1rem;
    }
</style>