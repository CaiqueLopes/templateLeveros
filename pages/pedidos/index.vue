<template>
  <v-card>
    <header>
      <v-card-title>
        <!--AJUSTAR COM A CSS TAG CORRETA>>>>> <v-flex tag="h1" class="headline">Exemplo</v-flex> -->
        <h1 style="color:#4a99ca;">Pedidos</h1>
      </v-card-title>
      <v-container fluid grid-list-xl>
        <v-layout row>
          <v-flex xs12 sm3>
            <v-select v-model="value" :items="items" chips label="Tipo" multiple solo></v-select>
          </v-flex>
          <v-flex xs12 sm9>
            <v-text-field v-model="search" append-icon="search" label="Número do pedido ou CPF"></v-text-field>
          </v-flex>
        </v-layout>
      </v-container>
      <v-layout row>
        <v-spacer></v-spacer>
        <v-btn round color="#4a99ca" class="white--text" @click.stop="expand = !expand">
          {{ expand ? 'Fechar todos' : 'Abrir todos'}}
          <v-icon right dark v-html="expand ? 'keyboard_arrow_up' : 'keyboard_arrow_down'"></v-icon>
        </v-btn>
      </v-layout>
    </header>
    <div>
      <v-data-table
        :headers="headers"
        :items="desserts"
        :expand="expand"
        item-key="order"
        :search="search"
        :pagination.sync="pagination"
      >
        <template slot="items" slot-scope="props">
          <tr @click="props.expanded = !props.expanded">
            <td><a href="#">{{ props.item.order }}</a></td>
            <td class="text-xs-right">{{ props.item.chanel }}</td>
            <td class="text-xs-right">{{ props.item.status }}</td>
            <td class="text-xs-right">{{ props.item.lastUpdate }}</td>
            <td class="text-xs-right"><v-icon>{{ props.item.ico }}</v-icon></td>
          </tr>
        </template>
        <template slot="expand" slot-scope="props">
          <v-card flat>
            <v-card-text>
              <div v-for="item in dados" :key="item.title">
                <v-layout row>
                  <v-flex>
                    <v-menu
                      v-model="menu"
                      :close-on-content-click="false"
                      :nudge-width="100"
                      offset-x
                    >
                      <v-btn slot="activator" color="info" round class="white--text">mostrar mais</v-btn>
                      <v-card>
                        <v-layout align-center row spacer>
                          <v-flex xs2 sm2 md2>
                            <v-avatar slot="activator">
                              <v-icon>autorenew</v-icon>
                            </v-avatar>
                          </v-flex>
                          <v-flex sm10 md10>
                            <span class="black--text">&nbsp; Reprocessar</span>
                          </v-flex>
                        </v-layout>
                        <v-layout align-center row spacer>
                          <v-flex xs2 sm2 md2>
                            <v-avatar slot="activator">
                              <v-icon>autorenew</v-icon>
                            </v-avatar>
                          </v-flex>
                          <v-flex sm10 md10>
                            <span class="black--text">&nbsp; Ignorar divergência e reprocessar</span>
                          </v-flex>
                        </v-layout>
                      </v-card>
                    </v-menu>
                  </v-flex>
                  <v-flex>
                    <v-card-text>
                  
                    </v-card-text>
                  </v-flex>
                  <v-flex>
                    <v-card-text>{{ item.err }}</v-card-text>
                  </v-flex>
                  <v-flex>
                    <v-card-text>{{ item.lastUpdate }}</v-card-text>
                  </v-flex>
                  <v-flex justify-end>
                    <v-icon v-html="item.ico"></v-icon>
                  </v-flex>
                </v-layout>
              </div>
            </v-card-text>
          </v-card>
        </template>
        <v-alert slot="no-results" :value="true" color="error" icon="warning">
          Nenhum resultado encontrado para "{{search}}".
          <br>:(
        </v-alert>
      </v-data-table>
      <div class="text-xs-center pt-2">
        <v-pagination color="#4a99ca" v-model="pagination.page" :length="pages"></v-pagination>
      </div>
    </div>
  </v-card>
</template>

<script>
export default {
  data() {
    return {
      search: '',
      pagination: {},
      items: ['Sucesso', 'Aguardando', 'Erro'],
      value: ['foo'],
      expand: false,
      headers: [
        {
          text: 'Pedido',
          align: 'center',
          sortable: true,
          value: 'order'
        },
        { text: 'Canal', align: 'center', value: 'chanel' },
        { text: 'Status', align: 'center', value: 'status' },
        { text: 'Data', align: 'center', value: 'lastUpdate' },
        { text: '.', align: 'center', value: 'ico' }
      ],
      desserts: [
        {
          value: false,
          order: 'PEDIDO 0000-00',
          chanel: 'Canal da compra',
          status: 'success',
          lastUpdate: 'Data do ultimo processamento',
          ico: 'check_circle_outline'
        },
        {
          value: false,
          order: 'PEDIDO 3569-00',
          chanel: 'Canal da compra',
          status: 'success',
          lastUpdate: 'Data do ultimo processamento',
          ico: 'check_circle_outline'
        },
        {
          value: false,
          order: 'PEDIDO 8627-00',
          chanel: 'Canal da compra',
          status: 'success',
          lastUpdate: 'Data do ultimo processamento',
          ico: 'check_circle_outline'
        },
        {
          value: false,
          order: 'PEDIDO 0547-00',
          chanel: 'Canal da compra',
          status: 'success',
          lastUpdate: 'Data do ultimo processamento',
          ico: 'check_circle_outline'
        },
        {
          value: false,
          order: 'PEDIDO 1324-00',
          chanel: 'Canal da compra',
          status: 'success',
          lastUpdate: 'Data do ultimo processamento',
          ico: 'check_circle_outline'
        },
        {
          value: false,
          order: 'PEDIDO 7722-10',
          chanel: 'Canal da compra',
          status: 'success',
          lastUpdate: 'Data do ultimo processamento',
          ico: 'check_circle_outline'
        },
        {
          value: false,
          order: 'PEDIDO 3044-00',
          chanel: 'Canal da compra',
          status: 'success',
          lastUpdate: 'Data do ultimo processamento',
          ico: 'check_circle_outline'
        },
        {
          value: false,
          order: 'PEDIDO 2010-00',
          chanel: 'Canal da compra',
          status: 'success',
          lastUpdate: 'Data do ultimo processamento',
          ico: 'check_circle_outline'
        },
        {
          value: false,
          order: 'PEDIDO 0000-01',
          chanel: 'Canal da compra',
          status: 'success',
          lastUpdate: 'Data do ultimo processamento',
          ico: 'check_circle_outline'
        },
        {
          value: false,
          order: 'PEDIDO 1010-00',
          chanel: 'Canal da compra',
          status: 'success',
          lastUpdate: 'Data do ultimo processamento',
          ico: 'check_circle_outline'
        }
      ],
      dados: [
        {
          order:'numero do pedido',
          err: 'Tipo do erro caso tenha algum erro com todos os detalhes'
        } /*,
        {
          ico: 'error_outline',
          order: 'PEDIDO 1111-00',
          buyer: 'E-MAIL DO COMPRADOR',
          status: 'Erro',
          lastUpdate: 'Data do ultimo processamento'
        }*/
      ]
    }
  },
  computed: {
    pages() {
      if (
        this.pagination.rowsPerPage == null ||
        this.pagination.totalItems == null
      )
        return 0

      return Math.ceil(this.pagination.totalItems / this.pagination.rowsPerPage)
    }
  }
}
</script>