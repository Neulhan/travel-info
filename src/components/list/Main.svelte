<script>
import { beforeUpdate } from "svelte";
    const endpoint = "./data.JSON";
    let filtereData, datas;
    beforeUpdate(()=>{
        fetch(endpoint)
            .then(res => {
                return res.json();
            })
            .then(data => datas=data)
    });
    

    // Map으로 부터 넘겨받아야 함
    let city = "london";
    console.log(datas);
    function filteringData(tag, original){
        let ret = original.filter((data)=>{
            return data.hashTags.includes(tag);
        })
        console.log(ret);
        return ret;
    }
</script>

<style>
    header {
        text-align: center;
    }

</style>

<header>
    <h1>{city}에 놀러가고 싶으시군요!</h1>
</header>
<nav>

</nav>
<container>
    <form>
        <selcet>
            <option>london</option>
            <option>restaurant</option>
        </selcet>
    </form>
    <section>

    </section>
</container>
