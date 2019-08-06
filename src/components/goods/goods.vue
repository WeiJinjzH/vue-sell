<template>
    <div class="goods">
        <div class="menu-wrapper">
            <ul>
                <li v-for="item in goods" :key="item" class="menu-item">
                    <span class="text border-1px">
                        <span v-show="item.type>0" class="icon" :class="classMap[item.type]"></span>{{item.name}}
                    </span>
                </li>
            </ul>
        </div>
        <div class="foods-wrapper"></div>
    </div>
</template>
<script type="text/ecmascrpt-6">
    const ERR_OK = 0

    export default {
        props: {
            seller: {
                type: Object
            }
        },
        data() {
            return {
                goods: [],
            }
        },
        created() {
            this.classMap = ['decrease', 'discount', 'special', 'invoice', 'guarantee']
            this.$http.get('/api/goods').then((res) => {
                res = res.body
                if (res.errno === ERR_OK) {
                    this.goods = res.data
                }
            })
        },
    }
</script>
<style lang="stylus" rel="stylesheet/stylus">
    @import '../../common/stylus/mixin.styl'

    .goods
        display: flex
        position: absolute
        top: 184px
        bottom: 46px
        left: 0
        width: 100%
        overflow: hidden
        .menu-wrapper
            flex: 0 0 80px
            width: 80px
            background: #f3f5f7
            .menu-item
                display: table
                padding: 0 12px
                height: 54px
                width: 56px
                line-height: 14px
                .icon
                    display: inline-block
                    vertical-align: top
                    margin-right: 2px
                    width: 12px
                    height: 12px
                    background-size: 12px 12px
                    background-repeat: no-repeat
                    &.decrease
                        bg-image('decrease_3')
                    &.discount
                        bg-image('discount_3')
                    &.guarantee
                        bg-image('guarantee_3')
                    &.invoice
                        bg-image('invoice_3')
                    &.special
                        bg-image('special_3')
                .text
                    display: table-cell
                    width: 56px
                    vertical-align: middle
                    border-1px(rgba(7, 17, 27, 0.1))
                    font-size: 12px
        .foods-wrapper
            flex: 1    
</style>