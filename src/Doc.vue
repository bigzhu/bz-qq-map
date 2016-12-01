<template>
  <div class="ui container segment">
    <h1>{{name}}</h1>
    <p>
      {{desc}}
    </p>
    <table class="ui celled table">
      <thead>
        <tr><th>参数</th><th>说明</th></tr>
      </thead>
      <tbody>
        <tr v-for="parm in parms"> <td class="single line"> {{parm.parm}} </td> <td> {{parm.desc}} </td></tr>
        <tr>
          <td colspan="2"></td>
        </tr>
      </tbody>
    </table>
    <code v-text="code">
    </code>
    <div class="ui divider"></div>
    <q-map style="height: 500px;" v-model="map" :config_map="config_map" class="map"></q-map>
  </div>
</template>

<script>
  import QMap from './Bz.vue'
  export default {
    components: {
      QMap
    },
    data: function () {
      return {
        name: 'Qmap',
        desc: '目前就是简单的显示了一个腾讯地图, 解决了资源加载问题, 但是污染了window.initMap 名字空间, 以后功能再添加',
        parms: [
          { parm: 'map', desc: '双向绑定的map实例' },
          { parm: 'config_map', desc: '自定义的参数修改, map 做为参数传进来' }
        ],
        map: null,
        code: `<q-map></q-map>`
      }
    },
    methods: {
      config_map: function (map) {
        console.log(map)
      }
    }
  }
</script>
