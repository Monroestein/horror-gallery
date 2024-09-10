<template>
    <div class="container">
        
        <header>
            <h1>{{ name }}</h1>
            <!-- <img :src="image" alt=""> -->
        </header>

        <div class="tooMuchText">
            <!-- <p>Name: {{ name }}</p> -->
            <p>Movie: <b>{{ movie }}</b> </p>
            <p>{{ description }}</p>
        </div>

    </div>
</template>

<script>
    export default {
        name: 'content-comp',
        props:{
            id: {
                type: Number,
                required: true
            },
            name: {
                type: String,
                required: true
            },
            movie: {
                type: String,
                required: true
            },
            description:{
                type: String,
                required: true
            },
            image: {
                type: String,
                required: true
            },
            selectedCharacter:{
                type: Boolean,
                required: true
            }
        }
    }
</script>

<style scoped>

.container{
    padding: 0px 10px;
    line-height: 25px;
}

header{
    width: 100%;
    /* background: #666; */
}

h1{
    font-size: 130px;
    letter-spacing: -19.5px;
}

p{
    padding: 0px 30px;
}

img{
    width: 100%;
}

</style>