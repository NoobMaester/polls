<script>
    export let type = 'primary';
    export let flat = false;
    export let inverse = false;
</script>

<button class={type} class:flat = {flat} class:inverse = {inverse}>
    <slot></slot>
</button>

<style>
    button{
        border: 0;
        cursor: pointer;
        border-radius: 6px;
        padding: 8px 12px;
        font-weight: bold;
        box-shadow: 1px 2px 3px rgba(0,0,0,0.2);
    }
    .primary{
        background: blueviolet;
        color: #fff;
    }
    .secondary{
        background: #d91b42;
        color: #fff
    }
    .flat{
        box-shadow: none;
    }
    .primary.inverse{
        color: blueviolet;
        background: #fff;
        border: 2px solid blueviolet;
    }
    .secondary.inverse{
        color: #d91b42;
        background: #fff;
        border: 2px solid #d91b42;
    }

</style>