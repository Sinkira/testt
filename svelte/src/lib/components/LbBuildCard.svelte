<script>
    import RelicSetDisplay from "$lib/components/RelicSetDisplay.svelte";
    import RelicsBulk from "$lib/components/RelicsBulk.svelte";
    import LbStats from "$lib/components/LbStats.svelte";
    export let build;
    export let ctgr;
    export let header;
    let showBuild = false;
</script>

<button
    class="show-build-button"
    on:click={() => (showBuild = true)}
    style="display: {showBuild ? 'none' : 'block'}"
>
    Show Build
</button>

<div class="tooglable" style="display: {showBuild ? 'block' : 'none'}">
    <LbStats lbStats={build["lbstats"][ctgr]} {header} />

    <div class="centeringDiv">
        <RelicSetDisplay relicSets={build["rs"]} />
    </div>
    <RelicsBulk relics={build["r"]} />
</div>

<button
    class="hide-build-button"
    on:click={() => (showBuild = false)}
    style="display: {showBuild ? 'block' : 'none'}"
>
    Hide Build
</button>

<style>
    .centeringDiv {
        display: flex;
        align-items: center;
        justify-content: center;
        margin: 0;
    }

    .show-build-button,
    .hide-build-button {
        background-color: transparent;
        cursor: pointer;
        display: block;
        margin: 0 auto;
        text-align: center;
        font-size: 1vw;
        outline: none;
    }

    @media (max-width: 850px) {
        .show-build-button,
        .hide-build-button {
            background-color: transparent;
            cursor: pointer;
            display: block;
            margin: 0 auto;
            text-align: center;
            font-size: 12px;
            outline: none;
            width: 100px;
            height: 20px;
        }
    }
</style>
