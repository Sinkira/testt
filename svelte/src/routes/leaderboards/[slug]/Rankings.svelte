<script>
    export let build;
    import { getPicForCtgr } from "$lib/leaderboards.js";
    import LbStats from "$lib/components/LbStats.svelte";
    import { charNamesMap } from "$lib/constants.js";

    $: charname = charNamesMap[build["k"]];
    let picSize = 5;
</script>

<div class="stuffOnTheRight" style="overflow: hidden;padding:5px;">
    <div class="container" style="text-align: center;">
        {#each Object.entries(build["lb"]) as [key, value]}
            <div>
                {#if build["lbstats"] && build["lbstats"].hasOwnProperty(key)}
                    <a
                        href={"./lb/" +
                            charname.toLowerCase() +
                            "/" +
                            key +
                            "/1"}
                    >
                        <img
                            src={getPicForCtgr(key)}
                            alt={"..."}
                            class="RelicImg"
                        />
                    </a>
                    <p>
                        {"Rank: " +
                            value["rank"] +
                            " (" +
                            value["percrank"] +
                            ")"}
                    </p>
                    <LbStats lbStats={build["lbstats"][key]} header={key} />
                {/if}
            </div>
        {/each}
    </div>
</div>

<style>
    .container {
        display: flex;
        overflow-x: auto;
        max-width: 100%;
        justify-content: center;
    }
    img {
        width: 5vw;
        height: 5vw;
        margin-bottom: -5px;
    }

    .stuffOnTheRight {
        border-bottom: 1px solid #7cf7ff;
        margin-left: 3vw;
        margin-right: 5vw;
        width: fit-content;
        margin: auto;
        margin-top: 5px;
    }

    p {
        margin: 3px;
    }
    @media (max-width: 850px) {
        p {
            font-size: 11px;
        }
        img {
            width: 50px;
            height: 50px;
        }
    }
</style>
