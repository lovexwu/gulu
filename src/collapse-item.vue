<template>
    <div class="collapseItem" @click="toggle">
        <div class="title">{{title}}</div>
        <div class="content" v-if="open">
            <slot></slot>
        </div>
    </div>

</template>

<script>
    export default {
        name: "GuluCollapseItem",
        props:{
            title:{
                type: String,
                required: true
            },
            name:{
                type: String,
                required: true
            }
        },
        data(){
            return {
                open: false
            }
        },
        inject: ['eventBus'],
        mounted(){
            this.eventBus && this.eventBus.$on('update:selected',(names)=>{
                console.log(names);
                if(names.indexOf(this.name) >=0 ){
                    this.open = true
                }else{
                    this.open = false
                }
            })
        },
        methods:{
            toggle(){
                if(this.open){
                    this.eventBus && this.eventBus.$emit('update:removeSelected',this.name)
                }else{
                    this.eventBus && this.eventBus.$emit('update:addSelected',this.name)
                }
            }
        }
    }
</script>

<style lang="scss" scoped>
    $gray: #ddd;
    $border-radius: 4px;

    .collapseItem{

        > .title{
            border: 1px solid $gray;
            margin: -1px -1px 0;
            min-height: 32px;
            display: flex;
            align-items: center;
            padding: 0 8px;
        }

        &:first-child .title{
            border-top-left-radius: 4px;
            border-top-right-radius: 4px;
        }

        > .content{
            padding: 8px;
        }

        &:last-child .title{
            margin-bottom: -1px;

            &:last-child{
                border-bottom-left-radius: 4px;
                border-bottom-right-radius: 4px;
            }
        }

    }
</style>