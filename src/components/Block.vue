<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        Click Me
    </div>
</template>

<script>
export default {
    props: [
        'delay'
    ],
    data(){
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },
    mounted(){
        // console.log('Component Mounted!')
        setTimeout(() => {
            this.showBlock = true;
            this.startTimer()
            // console.log(this.delay);
        }, this.delay);
    },
    methods: {
        startTimer(){
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10);
        },
        stopTimer(){
            clearInterval(this.timer)
            // console.log(this.reactionTime)
            this.$emit('end', this.reactionTime)
        }
    }
    // updated(){
    //     console.log("Component updated!")
    // },
    // unmounted(){
    //     console.log("Component Unmounted!");
    // }
}
</script>

<style>
    .block{
        width: 400px;
        border-radius: 20px;
        background: #0faf87;
        color: white;
        align-items: center;
        padding: 100px 0px;
        margin: 40px auto;
    }
    button{
        padding: 10px 30px;
        background: #333;
        color: white;
        font-weight: 600;
        border-radius: 5px;
        cursor: pointer;
    }
    button[disabled]{
        opacity: 0.2;
        cursor: not-allowed;
    }
</style>