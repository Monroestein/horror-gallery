<template>
    
        <div class="cropping">
            <div class="imageContainer">
              <img @click="showDescription(id)" :src="image" alt="" role="button">
            </div>
        </div>

</template>

<script>
    export default {
        name: 'sidebar-comp',

        props: {
            id:{
                type: Number,
                required: true

            },
            image:{
                type: String,
                required: true
            }
        },

        methods:{
            showDescription(id){
                this.$emit('showDesc', id)
            }
        }
    }
</script>

<style scoped>

.cropping{
    min-height: 250px;
    width: 250px;
    overflow: hidden;
    border: 1px solid #111;
}

.imageContainer{
    height: 100%;
} 
 
.imageContainer img{
    height: 100%;
    margin-left: -28.5%;
    opacity: 0.5;
    transition: opacity .5s;
    cursor: pointer;
} 

.imageContainer img:hover{
    opacity:1;
}


</style>