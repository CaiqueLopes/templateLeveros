<template>
  <v-app>
    <v-navigation-drawer :mini-variant="miniVariant" :clipped="clipped" v-model="drawer" fixed app>
      <v-list>
        <v-list-tile v-for="(item, i) in items" :to="item.to" :key="i" router exact>
          <v-list-tile-action>
            <v-icon v-html="item.icon"/>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title v-text="item.title"/>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar :clipped-left="clipped" fixed app dark color="primary">
      <v-btn icon @click.stop="miniVariant = !miniVariant">
        <v-icon v-html="miniVariant ? 'list' : 'list'"/>
      </v-btn>
      <v-toolbar-title v-text="logo"/>
      <div class="spacer"></div>
      <v-menu bottom left>
        <v-btn slot="activator" dark icon>
          <v-icon>more_vert</v-icon>
        </v-btn>
        <v-list>
          <v-list-tile v-for="(info, inf) in infos" :key="inf" @ click>
            <v-list-tile-title>{{info.dados}}</v-list-tile-title>
          </v-list-tile>
        </v-list>
      </v-menu>
    </v-toolbar>
    <v-content>
      <v-container>
        <nuxt/>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      clipped: true,
      drawer: true,
      fixed: true,
      items: [
        { icon: 'dashboard', title: 'Home', to: '/' },
        { icon: 'edit', title: 'Pedidos', to: '/pedidos' }
      ],
      infos: [
        { dados: 'Click Me' },
        { dados: 'Click Me' },
        { dados: 'Click Me' },
        { dados: 'Click Me' }
      ],
      miniVariant: false,
      logo: 'Nuxtfy.js'
    }
  }
}
</script>