<template>
    <div class="tabs-head">
        <slot></slot>
        <div class="line" ref="line"></div>
        <div class="actions-wrapper">
            <slot name="actions"></slot>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'GuluTabsHead',
        inject: ['eventBus'],
        mounted(){
            this.eventBus.$on('update:selected',(item,vm) => {
                let {width} = vm.$el.getBoundingClientRect()
                let left = vm.$el.offsetLeft
                this.$refs.line.style.width = `${width}px`
                this.$refs.line.style.left = `${left}px`
            })
        }
    }
</script>

<style lang="scss" scoped>
    $tab-height: 40px;
    $blue: #3182bd;
    $border-color: #ddd;
    .tabs-head{
        display: flex;
        justify-content: flex-start;
        height: $tab-height;
        position: relative;
        border-bottom: 1px solid $border-color;

        > .line{
            position: absolute;
            bottom: 0;
            border-bottom:1px solid $blue;
            transition: all .3s;
        }

        > .actions-wrapper{
            margin-left: auto;
            display: flex;
            padding: 0 1em;
            justify-content: center;
            align-items: center;
        }
    }
</style>

