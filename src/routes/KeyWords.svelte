<script lang="ts">
    export let words: string[];
    $: wordsRanked = [] as [string, number][];
    $: total = 0;

    $: {
        const wordCounts = new Map<string, number>();
        total = 0;
        for (let word of words) {
            if (!wordCounts.has(word)) {
                wordCounts.set(word, 1);
            } else {
                wordCounts.set(word, wordCounts.get(word)! + 1);
            }
            total += 1;
        }
        wordsRanked = [...wordCounts.entries()].sort((a, b) => b[1] - a[1]);
        wordsRanked = wordsRanked.slice(0, 10);
    }
</script>

<table>
    <tr>
        <th class="wordColumn">Word</th>
        <th class="occurrencesColumn">Occurrences</th>
        <th class="percentageColumn">Percentage</th>
    </tr>
    {#each wordsRanked as word}
        <tr>
            <td>{word[0]}</td>
            <td>{word[1]}</td>
            <td>{Math.round((word[1] / total) * 100)}%</td>
        </tr>
    {/each}
</table>

<style>
    table {
        border-width: 1px;
        border-style: solid;
        border-radius: var(--border--radius);
        border-color: var(--accent);
        width: 100%;
        border-collapse: collapse;
    }

    .wordColumn {
        width: 50%;
    }

    .occurrencesColumn {
        width: 25%;
    }

    .percentageColumn {
        width: 25;
    }

    td {
        text-align: center;
        word-break: break-all;
    }

    tr {
        border-width: 1px 0px;
        border-color: var(--accent);
    }

    tr:nth-child(2n) {
        background-color: var(--bg--sheet);
        border-radius: var(--border--radius);
    }
</style>
