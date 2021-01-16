<script>
import {
    beforeUpdate,
    onMount
} from "svelte";
import Items from './Items.svelte';
let datas, filtered_datas;
beforeUpdate(() => {
    const endpoint = "https://forif-travel-info.s3.ap-northeast-2.amazonaws.com/data.json";
    fetch(endpoint)
        .then(res => {
            return res.json();
        })
        .then(data => {
            datas = data;
        })
});
onMount(()=>{
    setTimeout(()=>{
        isHeaderShown=true;
    },1000);
    setTimeout(()=>{
        isBtnShown=true;
    },2000);   
});
// Map으로 부터 넘겨받아야 함
let city = "London";
let isHeaderShown = false;
let isBtnShown = false;
function onTagPress(tag) {
    const ret = datas.filter((data) => {
        return data['hashTags'][0] === city && data['hashTags'][1] === tag;
    })
    filtered_datas = ret;
}
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css?family=Montserrat&display=swap");

header {
    text-align: center;
    padding-bottom: 1rem;
}

h1 {
    padding-bottom: 0.5rem;
}

nav {
    display: flex;
    flex-flow: row;
    justify-content: center;
    button {
        flex-basis: 10rem;
        margin-right: 3rem;
        background: #f3f0f1;
        background: #f3f0f1;
        margin-bottom: 25px;
        border-radius: 32px;
        text-align: center;
        cursor: pointer;
        transition: all 0.1s ease-in-out;
        box-shadow: -6px -6px 10px rgba(255, 255, 255, 0.8),
            6px 6px 10px rgba(0, 0, 0, 0.2);
        color: #6f6cde;
        span {
            font-family: "Montserrat", sans-serif;
            font-weight: semibold;
        }
        &:hover {
        opacity: 0.3;
        box-shadow: -6px -6px 10px rgba(255, 255, 255, 0.8),
          6px 6px 10px rgba(0, 0, 0, 0.2);
        }
        &:active {
            opacity: 1;
            box-shadow: inset -4px -4px 8px rgba(255, 255, 255, 0.5),
            inset 8px 8px 16px rgba(0, 0, 0, 0.1);
            color: #79e3b6;
        }
    }
}

</style>

<header class="header">
    <h1>{city}에 놀러가고 싶으시군요!</h1>
    {#if isHeaderShown===true}
        <h2>아래의 해쉬태그들중에 원하는 태그를 골라보세요!</h2>
    {/if}
</header>
{#if isBtnShown===true}
<nav class="nav">
    <button on:click={()=>onTagPress('restaurant')}><span>식당</span></button>
    <button on:click={()=>onTagPress('hotel')}><span>호텔</span></button>
    <button on:click={()=>onTagPress('sights')}><span>명소</span></button>
</nav>
{/if}
<container>
    <Items bind:filtered_datas/>
</container>
