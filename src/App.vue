<template>
    <div class="window">
        <table class="chess">
            <thead>
                <tr>
                    <td>
                        <p>{{result}}</p>
                    </td>
                </tr>
            </thead>
            <tbody>
                <tr class="row">
                    <td>
                        <Cell @click="onClickCell(0, $event)" :n="n" />
                    </td>
                    <td>
                        <Cell @click="onClickCell(1, $event)" :n="n" />
                    </td>
                    <td>
                        <Cell @click="onClickCell(2, $event)" :n="n" />
                    </td>
                </tr>
                <tr class="row">
                    <td>
                        <Cell @click="onClickCell(3, $event)" :n="n" />
                    </td>
                    <td>
                        <Cell @click="onClickCell(4, $event)" :n="n" />
                    </td>
                    <td>
                        <Cell @click="onClickCell(5, $event)" :n="n" />
                    </td>
                </tr>
                <tr class="row">
                    <td>
                        <Cell @click="onClickCell(6, $event)" :n="n" />
                    </td>
                    <td>
                        <Cell @click="onClickCell(7, $event)" :n="n" />
                    </td>
                    <td>
                        <Cell @click="onClickCell(8, $event)" :n="n" />
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
import Cell from "./Cell";
export default {
    components: { Cell },
    data() {
        return {
            n: 0,
            shut: false,
            map: [
                [null, null, null],
                [null, null, null],
                [null, null, null]
            ],
            result: 'x先手'
        }
    },
    methods: {
        onClickCell(i, text) {
            this.map[Math.floor(i / 3)][i % 3] = text
            this.n += 1
            if (this.shut) { return }
            if (text === 'x') {
                this.result = '轮到o了'
            } else if (text === 'o') {
                this.result = '轮到x了'
            }
            this.tell()
        },
        tell() {
            const map = this.map;
            for (let i = 0; i < 3; i++) {
                if (map[i][0] !== null && map[i][0] === map[i][1] && map[i][1] === map[i][2]) {
                    this.result = '游戏结束' + map[i][0] + '赢了';
                    this.shut = true;
                }
            }
            for (let t = 0; t < 3; t++) {
                if (map[0][t] !== null && map[0][t] === map[1][t] && map[1][t] === map[2][t]) {
                    this.result = '游戏结束' + map[0][t] + '赢了';
                    this.shut = true;
                }
            }
            if (map[1][1] !== null) {
                if (map[0][0] === map[1][1] && map[1][1] === map[2][2]) {
                    this.result = '游戏结束' + map[0][0] + '赢了';
                    this.shut = true;
                }
                if (map[0][2] === map[1][1] && map[1][1] === map[2][0]) {
                    this.result = '游戏结束' + map[0][2] + '赢了';
                    this.shut = true;
                }
            }
            if (this.shut!==true&&map[0][0]&&map[0][1]&&map[0][2]&&map[1][0]&&map[1][1]&&map[1][2]&&map[2][0]&&map[2][1]&&map[2][2]) {
                this.result = '游戏结束，平局~';
                this.shut = true;
            }
        }
    }
};

</script>

<style>
body {
    box-sizing: border-box;
}
.window {
    height: 80vh;
    display: flex;
    justify-content: center;
    align-items: center;
}
.chess {
    border-collapse: collapse;
}
.chess thead {
    text-align: center;
    font-size: 20px;
    font-weight: bold;
    font-family: "黑体";
    color: #343a40;
}
.chess tbody {
    border: 6px solid #ccc;
    background-color: #f1f3f4;
}

.chess tbody td {
    border-spacing: 10px;
    /* background-color: #fff; */
    border-right: 6px solid #ccc;
    border-bottom: 6px solid #ccc;
}
.chess tbody tr td:nth-child(3) {
    border-right: 0px;
}
.chess tbody tr:nth-child(3) td {
    border-bottom: 0px;
}
.row {
    display: flex;
}
</style>
