<script>
    import { starRailRes } from "$lib/constants.js";
    export let charId;
    let picSize = 5;
</script>

<div class="sutffInMiddle">
    <img
    src={starRailRes +  "icon/avatar/" + charId + ".png"}
    alt={"avatar"}
    class="avatar"
/>
</div>

<style>
    .avatar {
        width: 6vw;
        height: 6vw;
        border-bottom: 3px solid #7cf7ff;
        border-top: 3px solid #7cf7ff;
        border-radius: 50%;
        margin-bottom: 5px;
    }
    @media (max-width: 850px) {
       
        .avatar {
            width: 70px;
            height: 70px;
        }
       
    }
    .sutffInMiddle {
        display: flex;
        flex-direction: column;
        align-items: center;
    }
</style>
