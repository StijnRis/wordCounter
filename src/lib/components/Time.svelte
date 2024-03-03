<script lang="ts">
    export let seconds: number;

    $: displayHours = Math.floor(seconds / 3600).toString().padStart(2, "0");
    $: displayMinutes = (Math.floor(seconds / 60) % 60).toString().padStart(2, "0");
    $: displaySeconds = (Math.floor(seconds) % 60).toString().padStart(2, "0");
</script>

<p>
    {#if displayHours != "00"}
        {displayHours}:{displayMinutes}:{displaySeconds}
    {:else}
        {displayMinutes}:{displaySeconds}
    {/if}
</p>

<style>
    p {
        margin: 0;
        padding: 0;
    }
</style>
