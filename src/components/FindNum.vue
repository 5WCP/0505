<script>
    export default {
        data() {
            return {
                answer: null,
                maxN: 100,
                minN: 1,
                target: Math.floor((Math.random() * 99) + 1),
                message: null
            }
        },

        methods: {
            findN() {
                if(this.answer > this.maxN || this.answer < this.minN) {
                    this.message = "超出猜測範圍";
                    this.answer = null;
                    return;
                }
                if(this.answer > this.target) {
                    this.message = "數字過大";
                    this.maxN = this.answer;
                    this.answer = null;
                    return;
                }
                if(this.answer < this.target) {
                    this.message = "數字過小";
                    this.minN = this.answer;
                    this.answer = null;
                    return;
                }
                if(this.answer === this.target) {
                    this.message = "恭喜答對";
                    this.answer = null;
                    this.$refs.title.innerText = "遊戲結束";
                    this.$refs.range.innerText = this.target;
                    return;
                }
            }
        },

        mounted() {
            
        }
    }
</script>

<template>
    <div class="findNum">
        <p ref="title">猜一個數字</p>
        <h2 ref="range">{{ minN }} ~ {{ maxN }}</h2>
        <p>{{ message }}</p>
        <input type="number" v-model="answer">
        <button type="button" @:click="findN">回答</button>
    </div>
</template>

<style lang="scss" scoped>
    .findNum {
        width: 200px;
        background-color: #fff;
        border-radius: 6px;
        padding: 8px 12px;
        text-align: center;

        button {
            margin-top: 15px;
            background-color: #acaac2;
            border-radius: 3px;
            padding: 4px 6px;
            transition: 0.6s;
            border: none;
            cursor: pointer;

            &:hover {
                background-color: #1088b8;
                color: aliceblue;
            }

            &:active {
                transform: scale(0.9);
            }
        }
    }
</style>