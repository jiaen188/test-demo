<template>
    <div>
        <h2>支持 HTML</h2>
        <p><strong>预览</strong></p>

        <div>
            <g-button @click="onClickBtn">点击弹出</g-button>
        </div>

        <p><strong>代码</strong></p>
        <pre><code>{{content}}</code></pre>
    </div>
</template>

<script>
import plugin from '../../../src/plugin.js'
import button from '../../../src/button.vue'
import Vue from 'vue'

Vue.use(plugin)

export default {
    components: {
        'g-button': button
    },
    data () {
        return {
            content: `
            <style>
            /* 设置toast 样式，因为toast组件 是直接插入到body中， 所以不能是局部的样式 */
            .wrapper {
                z-index: 30 !important;
            }
            </style>

            <g-button @click="onClickBtn">点击弹出</g-button>

            methods: {
                onClickBtn () {
                    this.$toast('<strong style="color: red;">支持HTML的内容</strong>', {
                        enableHtml: true
                    })
                }
            }
            `.replace(/^ {8}/gm, '').trim()
        }
    },
    methods: {
        onClickBtn () {
            this.$toast('<strong style="color: red;">支持HTML的内容</strong>', {
                enableHtml: true
            })
        }
    }
}
</script>

<style scoped>
* {
    box-sizing: border-box;
}
</style>

<style>
/* 设置toast 样式，因为toast组件 是直接插入到body中， 所以不能是局部的样式 */
.wrapper {
    z-index: 30 !important;
}
</style>
