<style lang="scss" scoped>
    .counter-component {
        position: relative;
        display: inline-block;
        overflow: hidden;
        vertical-align: middle;
        .counter-btn {
            border: 1px solid #e3e3e3;
            float: left;
            height: 30px;
            line-height: 30px;
            width: 25px;
            text-align: center;
            cursor: pointer;
            &.left{
                border-radius: 4px 0px 0px 4px;
            };
            &.right{
                border-radius: 0px 4px 4px 0px;
            }
        }
        .counter-show {
            float: left;
            input {
                border: none;
                text-align: center;
                border-top: 1px solid #e3e3e3;
                border-bottom: 1px solid #e3e3e3;
                height: 30px;
                line-height: 30px;
                width: 50px;
                outline: none;
            }
        }
    }
</style>

<template>
    <div class="counter-component">
        <div class="counter-btn left" @click="minus"> -</div>
        <div class="counter-show">
            <input type="text" v-model="number" @keyup="fixNumber">
        </div>
        <div class="counter-btn right" @click="add"> +</div>
    </div>
</template>

<script>
    export default {
        props: {
            max: {
                type: Number,
                default: 10
            },
            min: {
                type: Number,
                default: 1
            }
        },
        data() {
            return {
                number: this.min
            }
        },
        watch: {
            number() {
                this.$emit('on-change', this.number)
            }
        },
        methods: {
            fixNumber() {
                let fix
                if (typeof this.number === 'string') {
                    fix = Number(this.number.replace(/\D/g, ''))
                }
                else {
                    fix = this.number
                }
                if (fix > this.max || fix < this.min) {
                    fix = this.min
                }
                this.number = fix
            },
            minus() {
                if (this.number <= this.min) {
                    return
                }
                this.number--
            },
            add() {
                if (this.number >= this.max) {
                    return
                }
                this.number++
            }
        }
    }
</script>