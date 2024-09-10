<template>
    <header>
        <h1>{{ this.title }}</h1>
        <p>{{ this.desc }}</p>
    </header>
</template>

<script>
    export default {
        name: 'header-comp',
        data: function () {
            return {
                title: 'Horror Gallery',
                desc: 'Famous horror movie characters. Probably one of them gave you nightmares as a kid. Most of the information was extracted from Horror Film Wiki.'
            }
        }
    }
</script>

<style scoped>

    header{
        text-align: center;
        margin-bottom: 30px;
    }

    h1{
        font-family: "Creepster", system-ui;
        color: #e8f347;
        font-size: 90px;
        margin-bottom: 20px;
        letter-spacing: 5px;
        text-shadow: #e8f347;
    }

    p{
        font-size: 13px;
    }

</style>