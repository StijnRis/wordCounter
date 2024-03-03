<script lang="ts">
    export let value: string;
    console.log(value);
</script>

<textarea id="input" bind:value={value}></textarea>

<style>
    #input {
        width: 100%;
        height: 300px;

        color: var(--text--primary);
        background-color: var(--bg--sheet);
        border-color: var(--accent);
        outline: none;

        border-radius: var(--border--radius);
        resize: none;

        box-sizing: border-box;
        padding: 5px;

        font-size: 1.5rem;
        line-height: 2rem;
    }
</style>