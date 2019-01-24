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
      <v-btn icon>
        <v-icon>search</v-icon>
      </v-btn>
      <v-menu bottom left>
        <v-btn slot="activator" dark icon>
          <v-icon>more_vert</v-icon>
        </v-btn>
        <v-card>
          <v-list>
            <v-list-tile avatar>
              <v-list-tile-avatar>
                <img :src="imageLink" alt="user">
              </v-list-tile-avatar>
              <v-list-tile-content>
                <v-list-tile-title>{{userName}}</v-list-tile-title>
                <v-list-tile-sub-title>{{description}}</v-list-tile-sub-title>
              </v-list-tile-content>
            </v-list-tile>
          </v-list>
          <v-divider></v-divider>
          <v-layout align-center row spacer>
            <v-flex xs2 sm2 md2>
              <v-avatar slot="activator">
                <v-icon>person_outline</v-icon>
              </v-avatar>
            </v-flex>
            <v-flex sm10 md10>
              <span class="black--text">&nbsp;Perfil</span>
            </v-flex>
          </v-layout>
          <v-layout align-center row spacer>
            <v-flex xs2 sm2 md2>
              <v-avatar slot="activator">
                <v-icon>settings</v-icon>
              </v-avatar>
            </v-flex>
            <v-flex sm10 md10>
              <span class="black--text">&nbsp;Configurações</span>
            </v-flex>
          </v-layout>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="info" flat @click="menu = false">Logout</v-btn>
          </v-card-actions>
        </v-card>
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
      description: 'Descrição do usuário',
      userName: 'Nome do usuário',
      imageLink:
        'http://icons.iconarchive.com/icons/aha-soft/standard-new-year/128/Snowflake-icon.png',
      fav: true,
      menu: false,
      message: false,
      hints: true,
      miniVariant: false,
      logo: 'Nuxtfy.js'
    }
  }
}
</script>