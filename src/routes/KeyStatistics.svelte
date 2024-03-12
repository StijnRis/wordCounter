<script lang="ts">
    import Time from "$lib/components/Time.svelte";

    export let text: string;
    export let words: string[];

    const readingSpeed = 255 / 60;
    const speakingSpeed = 180 / 60;
    $: console.log(text.match(/(\w[.?!](\s|$))/g));

    $: amountOfWords = words.length;
    $: amountOfCharacters = text.length;
    $: sentences = text.match(/\w[.?!](\s|$)/g);
    $: amountOfSentences = sentences ? sentences.length : 0;
    $: readingTime = amountOfWords / readingSpeed;
    $: speakingTime = amountOfWords / speakingSpeed;
</script>

<div class="container">
    <div class="item">
        <p class="big">{amountOfWords}</p>
        <p class="small">Words</p>
    </div>
    <div class="item">
        <p class="big">{amountOfCharacters}</p>
        <p class="small">Characters</p>
    </div>
    <div class="item">
        <p class="big">{amountOfSentences}</p>
        <p class="small">Sentences</p>
    </div>
    <div class="item">
        <p class="big"><Time seconds={readingTime}></Time></p>
        <p class="small">Reading time</p>
    </div>
    <div class="item">
        <p class="big"><Time seconds={speakingTime}></Time></p>
        <p class="small">Speaking time</p>
    </div>
</div>

<style>
    .container {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr;
        grid-gap: 4px;
    }

    .item {
        border: 1px solid var(--accent);
        border-radius: var(--border--radius);
        padding: 10px;
    }

    .big {
        font-size: 2rem;
        text-align: center;
        margin: 0;
    }

    .small {
        font-size: 1rem;
        text-align: center;
        margin: 0;
    }
</style>
