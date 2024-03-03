<script lang="ts">
</script>

<div id="main">
    <slot />
</div>

<style>
    :root {
        --border--radius: 5px;
    }

    @media (prefers-color-scheme: light) {
        :root {
            --text--primary: #111;
            --text--secondary: #0000008f;
            --bg--page: #f6f5f0;
            --bg--sheet: #ffffff;
            --accent: #e15a46;
        }
    }

    @media (prefers-color-scheme: dark) {
        :root {
            --text--primary: #e1e1e1;
            --text--secondary: #ffffff8f;
            --bg--page: #202124;
            --bg--sheet: #555555;
            --accent: #e15a46;
        }
    }

    #main {
        width: 100%;
        min-height: 100vh;

        overflow: auto;

        color: var(--text--primary);
        background-color: var(--bg--page);

        font-family: Poppins, serif;
        font-optical-sizing: auto;
        font-weight: 400;
        font-style: normal;
    }
</style>
