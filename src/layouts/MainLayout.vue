<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />

        <q-toolbar-title>
          Quasar App
        </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      content-class="bg-grey-1"
    >
      <q-list>
        <q-item-label
          header
          class="text-grey-8"
        >
          Essential Links
        </q-item-label>
        <q-tree
          :nodes="simple"
          selected-color="blue"
          node-key="label"
          :selected.sync="selected">
        </q-tree>
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>

export default {
  name: 'MainLayout',
  data () {
    return {
      leftDrawerOpen: false,
      selected: '',
      toEmit: {
        initUrl: '',
        updateUrl: '',
        initContent: ''
      },
      simple: [
        {
          label: '基本配置',
          children: [
            { handler: (node) => this.handleClick(node), label: '客户端基本配置', url: 'map' }
          ]
        }
      ]
    }
  },
  methods: {
    handleClick (node) {
      console.log(`node: ${JSON.stringify(node)}`)
      this.$router.push(node.url)
    }
  }
}
</script>
