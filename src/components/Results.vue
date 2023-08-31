<template>
<p>Reaction Time - {{ score }}ms</p>
<p class="rank">{{ rank }}</p>
</template>

<script>
export default {
props :['score'],
data(){
    return{
        rank : null
    }
},
mounted(){
    if (this.score < 250){
        this.rank = 'Wow Ninja Fingers..🥷'
    }else if(this.score < 450){
        this.rank = "Rapid Reflexes..🙅‍♂️"
    }else{
        this.rank = "OHH Your Finger Move Like A Snail..🐌 "
    }
}
}
</script>

<style>
.rank{
    font-size: 1.4em;
    color: #0faf87;
    font-weight: bold;
}
</style>