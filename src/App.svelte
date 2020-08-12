<script>
    import CharityList from './CharityList.svelte';

    let title = "Charity";
    setTimeout(() => {
        title = "Donation";
    }, 2000);

    let charities = [];
</script>

<!-- <svelte:head>
    <link rel="stylesheet" href="https://cdn.rawgit.com/kimeiga/bahunya/css/bahunya-0.1.3.css" />
</svelte:head> -->

<div>
    <h1>{title}</h1>
    <CharityList {charities} />
</div>

<style>
    :global(div) {
        border: 5px solid black;
        padding: 10px;
    }
</style>

