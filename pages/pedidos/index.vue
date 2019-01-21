<template>
  <v-card>
    <header>
      <v-card-title>
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
        item-key="name"
        :search="search"
        :pagination.sync="pagination"
      >
        <template slot="items" slot-scope="props">
          <tr @click="props.expanded = !props.expanded">
            <td>{{ props.item.name }}</td>
            <td class="text-xs-right">{{ props.item.calories }}</td>
            <td class="text-xs-right">{{ props.item.fat }}</td>
            <td class="text-xs-right">{{ props.item.carbs }}</td>
            <td class="text-xs-right">{{ props.item.protein }}</td>
            <td class="text-xs-right">{{ props.item.iron }}</td>
          </tr>
        </template>

        <template slot="expand" slot-scope="props">
          <v-card flat>
            <v-card-text>Teste</v-card-text>
          </v-card>
        </template>
        <v-alert slot="no-results" :value="true" color="error" icon="warning">
          Nenhum resultado encontrado para "{{ search }}".
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
          text: 'Nome',
          align: 'left',
          sortable: false,
          value: 'name'
        },
        { text: 'Calories', value: 'calories' },
        { text: 'Fat (g)', value: 'fat' },
        { text: 'Carbs (g)', value: 'carbs' },
        { text: 'Protein (g)', value: 'protein' },
        { text: 'Iron (%)', value: 'iron' }
      ],
      desserts: [
        {
          value: false,
          name: 'Frozen Yogurt',
          calories: 159,
          fat: 6.0,
          carbs: 24,
          protein: 4.0,
          iron: '1%'
        },
        {
          value: false,
          name: 'Ice cream sandwich',
          calories: 237,
          fat: 9.0,
          carbs: 37,
          protein: 4.3,
          iron: '1%'
        },
        {
          value: false,
          name: 'Eclair',
          calories: 262,
          fat: 16.0,
          carbs: 23,
          protein: 6.0,
          iron: '7%'
        },
        {
          value: false,
          name: 'Cupcake',
          calories: 305,
          fat: 3.7,
          carbs: 67,
          protein: 4.3,
          iron: '8%'
        },
        {
          value: false,
          name: 'Gingerbread',
          calories: 356,
          fat: 16.0,
          carbs: 49,
          protein: 3.9,
          iron: '16%'
        },
        {
          value: false,
          name: 'Jelly bean',
          calories: 375,
          fat: 0.0,
          carbs: 94,
          protein: 0.0,
          iron: '0%'
        },
        {
          value: false,
          name: 'Lollipop',
          calories: 392,
          fat: 0.2,
          carbs: 98,
          protein: 0,
          iron: '2%'
        },
        {
          value: false,
          name: 'Honeycomb',
          calories: 408,
          fat: 3.2,
          carbs: 87,
          protein: 6.5,
          iron: '45%'
        },
        {
          value: false,
          name: 'Donut',
          calories: 452,
          fat: 25.0,
          carbs: 51,
          protein: 4.9,
          iron: '22%'
        },
        {
          value: false,
          name: 'KitKat',
          calories: 518,
          fat: 26.0,
          carbs: 65,
          protein: 7,
          iron: '6%'
        }
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

          return Math.ceil(
            this.pagination.totalItems / this.pagination.rowsPerPage
          )
        }
      }
}
</script>
