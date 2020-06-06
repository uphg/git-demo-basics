<template>
    <div>
        <div class="cell" v-on:click="onClickSelf">
            <template v-if="a">
                <div v-bind:class="addClassName"></div>
            </template>
        </div>
    </div>
</template>

<script>
export default {
    props: ["n"],
    data() {
        return { a: false, text: '', addClassName: '' };
    },
    methods: {
        onClickSelf() {
            if (this.text !== '') { return; }
            this.a = true
            if (this.n % 2 === 0) {
                this.text = 'x'
                this.addClassName = 'fork'
            } else {
                this.text = 'o'
                this.addClassName = 'circle'
            }
            this.$emit("click", this.text);
        }
    }
};
</script>

<style>
.cell {
    width: 100px;
    height: 100px;
    display: flex;
    justify-content: center;
    align-items: center;
}
.fork {
    width: 60px;
    height: 60px;
    position: relative;
}
.fork::after,
.fork::before {
    content: "";
    display: inline-block;
    width: 70px;
    height: 6px;
    background-color: #0063b1;
    position: absolute;
    top: 50%;
    left: -5px;
    margin-top: -3px;
    transform: rotate(45deg);
}
.fork::before {
    transform: rotate(-45deg);
}
.circle {
    width: 48px;
    height: 48px;
    border-radius: 50%;
    border: 6px solid #e74856;
}
</style>
