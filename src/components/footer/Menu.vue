<template>
    <section class="menu" id="menu">
        <router-link v-for="item in menu" :key="item.name" :to="item.path" :class="{orange: item.path == $route.path}">
            <svgicon
                    :name="item.meta.icon"
                    :class="{orange: item.path == $route.path}"
                    width="25"
                    height="25"
            ></svgicon>
            <span>{{item.meta.title}}</span>
        </router-link>
    </section>
</template>

<script>
import _ from 'lodash'

export default {
    data() {
      return{
        change: false
      }
    },
    mounted() {

    },
    methods: {

    },
    computed: {
      menu() {
        let routes = _.map(this.$router.options.routes,(o)=>{
          if (o.menu) return o
        })
        routes = _.without(routes, undefined)
        return routes
      }
    }
}
</script>

<style lang="less">
    #menu{
        width: 100%;
        background: #FFFFFF;
        border-top: 1px solid #e1e1e1;
        position: fixed;
        bottom: 0;
        padding: 10px 0;
        .flex-vertical-middle;
        a{
            text-align: center;
            flex: 1;
            span{
                display: block;
                font-size: 20px;
                padding-top: 8px;
            }
            &.router-link-exact-active{
                color: @orange;
            }
        }
        .svg-icon{
            width: 200px;
        }
    }
</style>