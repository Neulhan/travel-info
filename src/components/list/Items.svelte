<script>
export let filtered_datas = [];
</script>

<style lang="scss">
.container {
    margin-left: 50px;
    margin-right: 50px;
    display: flex;
    flex-flow: row wrap;
}

body {
    font-family: 'RobotoDraft', 'Roboto', sans-serif;
}

* {
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
}

h5 {
    margin: 0px;
    font-size: 1.4em;
    font-weight: 700;
}

p {
    font-size: 12px;
}

.center {
    display: flex;
    justify-content: center;
    align-items: center;
}

/* End Non-Essential  */

.property-card {
    height: 18em;
    width: 14em;
    margin : 2em;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-orient: vertical;
    -webkit-box-direction: normal;
    -ms-flex-direction: column;
    flex-direction: column;
    position: relative;
    -webkit-transition: all 0.4s cubic-bezier(0.645, 0.045, 0.355, 1);
    -o-transition: all 0.4s cubic-bezier(0.645, 0.045, 0.355, 1);
    transition: all 0.4s cubic-bezier(0.645, 0.045, 0.355, 1);
    border-radius: 16px;
    overflow: hidden;
    box-shadow: 15px 15px 27px #dfd7f0, -15px -15px 27px #dfd7f0;
}

.property-image {
    height: 6em;
    width: 14em;
    padding: 1em 2em;
    top: 0px;
    -webkit-transition: all 0.4s cubic-bezier(0.645, 0.045, 0.355, 1);
    -o-transition: all 0.4s cubic-bezier(0.645, 0.045, 0.355, 1);
    transition: all 0.4s cubic-bezier(0.645, 0.045, 0.355, 1);
}

/* Bottom Card Section */

.property-description {
    background-color:skyblue;
    height: 12em;
    width: 14em;
    position: absolute;
    bottom: 0em;
    -webkit-transition: all 0.4s cubic-bezier(0.645, 0.045, 0.355, 1);
    -o-transition: all 0.4s cubic-bezier(0.645, 0.045, 0.355, 1);
    transition: all 0.4s cubic-bezier(0.645, 0.045, 0.355, 1);
    padding: 0.5em 1em;
    text-align: center;
}


/* Property Cards Hover States */

.property-card:hover .property-description {
    height: 0em;
    padding: 0px 1em;
}

.property-card:hover .property-image {
    height: 18em;
}

.property-card:hover {
    background-color: white;
}

.property-card:hover {
    background-color: blue;
    cursor: pointer;
}
</style>

<div class="container">
    {#each filtered_datas as data}
    <div class="center">
        <div class="property-card">
            <a href="#">
                <img class="property-image" src={data.img}/>
            </a>
            <div class="property-description">
                <h5> {data.name} </h5>
                <p>Rate :  {data.rating}</p>
            </div>
            <a href="#">
            </a>
        </div>
    </div>
    {/each}
</div>


