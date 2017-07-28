<template>
    <div id="app">
        <demonstration
                tag="h2"
                title="Rate 评分"
                :show-content="false">
            <template slot="description">
                评分组件 （<a href="http://element.eleme.io/#/zh-CN/component/rate#rate-ping-fen" target="_blank">Element
                Rate 评分</a>）
            </template>
        </demonstration>
        <demonstration
                title="基础用法"
                anchor="ji-chu-yong-fa"
                :highlight="sourcecodeA">
            <template slot="description">
                默认展示效果
            </template>
            <template slot="source">
                <div class="vd-demo__block vd-demo__block-1">
                    <span class="vd-demo__demonstration">默认不区分颜色</span>
                    <vm-rate v-model="valueA1"></vm-rate>
                </div>
                <div class="vd-demo__block vd-demo__block-1">
                    <span class="vd-demo__demonstration">区分颜色</span>
                    <vm-rate v-model="valueA2" :colors="colorsA2"></vm-rate>
                </div>
                <div class="vd-demo__block vd-demo__block-1">
                    <span class="vd-demo__demonstration">指定大小，默认单位px</span>
                    <vm-rate v-model="valueA3" :size="36">
                    </vm-rate>
                </div>
                <div class="vd-demo__block vd-demo__block-1">
                    <span class="vd-demo__demonstration">指定大小，单位rem</span>
                    <vm-rate v-model="valueA4" size="2rem">
                    </vm-rate>
                </div>
            </template>
            <template slot="explanation">
                评分被分为三个等级，可以利用颜色对分数及情感倾向进行分级（默认情况下不区分颜色）。三个等级所对应的颜色用过 <code>colors</code>属性设置，而它们对应的两个阈值则通过 <code>low-threshold</code>
                和 <code>high-threshold</code> 设定。<b class="new">（<code>low-threshold</code> 和 <code>high-threshold</code> 作用于
                <code>colors</code> 和 <code>iconClasses</code>，用来显示不同的颜色和图标）</b>
            </template>
        </demonstration>
        <demonstration
                anchor="fu-zhu-wen-zi"
                title="辅助文字"
                description="用辅助文字直接地表达对应分数"
                :highlight="sourcecodeB"
                :multiple="true">
            <template slot="source">
                <div class="vd-demo__block vd-demo__block-1">
                    <span class="vd-demo__demonstration">辅助文字数组</span>
                    <vm-rate
                            v-model="valueB1"
                            show-text
                            :texts="['极差', '失望', '一般', '满意', '惊喜']"></vm-rate>
                </div>
                <div class="vd-demo__block vd-demo__block-1">
                    <span class="vd-demo__demonstration">辅助文字模板 <b class="new">(新增特性，新增示例)</b></span>
                    <vm-rate
                            v-model="valueB2"
                            :show-text="true"
                            text-type="number"
                            text-template="{value}星"></vm-rate>
                </div>
            </template>
            <template slot="explanation">
                为组件设置 <code>show-text</code> 属性会在右侧显示辅助文字。通过设置 <code>texts</code> 可以为每一个分值指定对应的辅助文字。<code>texts</code>
                为一个数组，长度应等于最大值 <code>max</code>。<b class="new">（这里做了一些修改，如果你指定了 <code>text-type="number"</code> 那么将会使用 <code>text-template="{value}"</code>
                显示辅助文字）</b>
            </template>
        </demonstration>
        <demonstration
                anchor="qi-ta-icon"
                title="其它 icon"
                description="当有多层评价时，可以用不同类型的 icon 区分评分层级"
                :highlight="sourcecodeC">
            <template slot="source">
                <vm-rate
                        v-model="valueC1"
                        :iconClasses="['vm-icon-sad', 'vm-icon-neutral-full', 'vm-icon-smile']"
                        voidIconClass="vm-icon-neutral-empty"
                        disabledVoidIconClass="vm-icon-neutral-full"
                        :colors="['#99A9BF', '#F7BA2A', '#FF9900']"></vm-rate>
            </template>
            <template slot="explanation">
                设置 <code>icon-classes</code> 属性可以自定义对应 3 个不同分段的图标。本例还使用 <code>void-icon-class</code> 指定了未选中时的图标类名。<b
                    class="new">（还使用了 <code>disabledVoidIconClass</code>
                指定了禁用时的图表类名）</b>
            </template>
        </demonstration>
        <demonstration
                anchor="zhi-du"
                title="只读"
                description="只读的评分用来展示分数，允许出现半星"
                :highlight="sourcecodeD"
                :multiple="true">
            <template slot="source">
                <div class="vd-demo__block vd-demo__block-1">
                    <span class="vd-demo__demonstration">允许出现半星 <b class="new">(修改特性)</b></span>
                    <vm-rate
                            v-model="valueD1"
                            disabled
                            :allow-half="true"
                            show-text
                            text-color="#ff9900"
                            text-template="{value}"></vm-rate>
                </div>
                <div class="vd-demo__block vd-demo__block-1">
                    <span class="vd-demo__demonstration">不允许出现半星 <b class="new">(新增示例)</b></span>
                    <vm-rate
                            v-model="valueD1"
                            disabled
                            :allow-half="false"
                            show-text
                            text-color="#ff9900"
                            text-template="{value}❤"></vm-rate>
                </div>
            </template>
            <template slot="explanation">
                为组件设置 <code>disabled</code>
                属性表示组件为只读，支持小数分值。此时若设置 <code>show-text</code>，则会在右侧显示目前的分值。可以提供 <code>text-template</code>
                作为显示模板，模板为一个包含了 <code>{value}</code>
                的字符串，<code>{value}</code> 会被解析为分值。<b class="new">（你可以通过 <code>allow-half="true"</code>来指定是否允许出现半星， 你也可以修改
                <code>text-template="{value}❤"</code>的修饰文字）</b>
            </template>
        </demonstration>
        <demonstration
                anchor="ban-xing"
                :highlight="sourcecodeE"
                :multiple="true">
            <template slot="title">
                半星 <b class="new">(新增示例)</b>
            </template>
            <template slot="description">
                当进行评价时，可以出现 .5 评分
            </template>
            <template slot="source">
                <div class="vd-demo__block vd-demo__block-1">
                    <span class="vd-demo__demonstration">默认半星</span>
                    <vm-rate
                            v-model="valueE1"
                            :allow-half="true"></vm-rate>
                </div>
                <div class="vd-demo__block vd-demo__block-1">
                    <span class="vd-demo__demonstration">带辅助文字数组</span>
                    <vm-rate
                            v-model="valueE2"
                            :allow-half="true"
                            show-text></vm-rate>
                </div>
                <div class="vd-demo__block vd-demo__block-1">
                    <span class="vd-demo__demonstration">带辅助文字模板</span>
                    <vm-rate
                            v-model="valueE3"
                            :allow-half="true"
                            show-text
                            text-type="number"
                            text-color="#ff9900"
                            text-template="{value}❤"></vm-rate>
                </div>
                <div class="vd-demo__block vd-demo__block-1">
                    <span class="vd-demo__demonstration">评分星星个数为10</span>
                    <vm-rate
                            v-model="valueE4"
                            :max="10"
                            :allow-half="true"
                            show-text></vm-rate>
                </div>
            </template>
            <template slot="explanation">
                为组件设置 <code>allow-half</code> 属性表示组件为是否允许半星，支持小数分值。此时若设置 <code>show-text</code>，则会在右侧显示目前的文字等级。也可以提供 <code>text-type="number"</code>
                文字类型 和 <code>text-template</code> 作为显示模板，模板为一个包含了 <code>{value}</code>
                的字符串，<code>{value}</code> 会被解析为分值。为组件设置 <code>:max="10"</code>属性修改星星个数。
            </template>
        </demonstration>

        <!-- 说明 -->
        <demonstration
                :show-content="false">
            <p>示例使用详情请参考：（<a href="https://github.com/savoygu/vue-demonstration">https://github.com/savoygu/vue-demonstration</a>）
            </p>
        </demonstration>
    </div>
</template>

<script type="es6">
    import { sourcecodeA, sourcecodeB, sourcecodeC, sourcecodeD, sourcecodeE } from './template'

    export default {
        data () {
            return {
                valueA1: 0,
                valueA2: 0,
                valueA3: 0,
                valueA4: 0,
                colorsA2: ['#99A9BF', '#F7BA2A', '#FF9900'],
                valueB1: 3,
                valueB2: 3,
                valueC1: 0,
                valueD1: 3.7,
                valueD2: 3.7,
                valueE1: 0,
                valueE2: 0,
                valueE3: 0,
                valueE4: 0,
                sourcecodeA,
                sourcecodeB,
                sourcecodeC,
                sourcecodeD,
                sourcecodeE
            }
        },
    }
</script>

<style lang="less" rel="stylesheet/less">
    #app {
        margin: 60px auto;
    }
</style>
