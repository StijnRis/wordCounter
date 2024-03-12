<script lang="ts">
    import Information from "./Information.svelte";
    import InputField from "./InputField.svelte";
    import Statistics from "./KeyStatistics.svelte";
    import KeyWords from "./KeyWords.svelte";

    let text = "";
    $: words = text.match(/\b(\w+)\b/g) as string[];
    $: {
        if (words == null) {
            words = [];
        }
        console.log(words);
    }
</script>

<svelte:head>
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link
        rel="preconnect"
        href="https://fonts.gstatic.com"
        crossorigin={"true"}
    />
    <link
        href="https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap"
        rel="stylesheet"
    />
</svelte:head>

<h1>Word counter</h1>
<div id="wrapper">
    <div id="content">
        <div id="input">
            <InputField bind:value={text}></InputField>
        </div>
        <div id="statistics">
            <Statistics bind:text bind:words></Statistics>
            <KeyWords bind:words></KeyWords>
        </div>
        <div id="info">
            <Information></Information>
        </div>
    </div>
</div>

<style>
    h1 {
        text-align: center;
    }

    #wrapper {
        display: flex;
        justify-content: center;
    }

    #content {
        max-width: 1200px;
        margin: 0px 50px;

        display: grid;
        gap: 20px;
        grid-template-columns: 1fr;
        grid-template-areas:
            "input"
            "statistics"
            "info";

        @media (min-width: 1280px) {
            grid-template-columns: 1fr 1fr 1fr;
            grid-template-areas:
                "input input statistics"
                "info info statistics";
        }
    }

    #input {
        grid-area: input;
    }

    #statistics {
        grid-area: statistics;

        display: flex;
        flex-direction: column;
        gap: 20px;

        @media (max-width: 800px) {
            flex-direction: row;
        }
    }

    #info {
        grid-area: info;
    }
</style>
