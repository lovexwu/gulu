<template>
    <div style="padding-top: 15px;">
        <g-row class="demoRow" gutter="10">
            <g-col span="8"><div class="demoCol">8</div></g-col>
            <g-col span="2" offset="4"><div class="demoCol">8</div></g-col>
            <g-col span="8" offset="2"><div class="demoCol">8</div></g-col>
        </g-row>
        <g-row class="demoRow" gutter="10">
            <g-col span="4" offset="2"><div class="demoCol">6</div></g-col>
            <g-col span="6"><div class="demoCol">6</div></g-col>
            <g-col span="6"><div class="demoCol">6</div></g-col>
            <g-col span="6"><div class="demoCol">6</div></g-col>
        </g-row>
        <g-row class="demoRow" gutter="10">
            <g-col span="12"><div class="demoCol">12</div></g-col>
            <g-col span="9" offset="3"><div class="demoCol">12</div></g-col>
        </g-row>
    </div>
</template>


<style scoped>
    *{box-sizing: border-box;}
    .demoRow{margin: 10px 0;}
    .demoCol {
        height: 50px;
        border: 1px solid #e5e9f2;
        background: #d3dce6;
        display: flex;
        justify-content: center;
        align-items: center;
    }
</style>

<script>
    import Row from '../../../src/row'
    import Col from '../../../src/col'

    export default {
        components: {
            'g-row': Row,
            'g-col': Col
        }
    }
</script>