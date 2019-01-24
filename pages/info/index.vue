<template>
  <div class="v-sheet v-sheet--tile theme--light">
    <v-container fluid grid-list-lg>
      <v-layout row wrap>
        <v-flex d-flex xs12 sm3 md3>
          <v-card>
            <v-card>
              <v-img
                src="https://multiar.hubin.io/marketplace/b2w_background_card.16cfb512055cc794cc98.jpg"
                height="235px"
              ></v-img>
              <v-card-title primary-title>
                <div>
                  <div class="headline blue--text">B2W-2020211820</div>
                </div>
              </v-card-title>
            </v-card>
          </v-card>
        </v-flex>
        <v-flex d-flex xs12 sm3 md3>
          <v-layout row wrap>
            <v-flex d-flex>
              <v-layout row wrap>
                <v-flex v-for="n in 1" :key="n" d-flex xs12>
                  <v-card>
                    <v-card-title primary class="subheading">Endereço de entrega</v-card-title>
                    <v-card-text class="headline">Nome Estado</v-card-text>
                    <v-card-text>
                      <p class="caption">JOERG BRUDER (VL S FRANCISCO), 31
                        <br>SANTO AMARO
                        <br>SAO PAULO - SP
                        <br>04710200 / BR
                      </p>
                      <hr class="v-divider theme--light">
                      <br>Data Estimada de Entrega: 01/02/2019
                    </v-card-text>
                  </v-card>
                </v-flex>
              </v-layout>
            </v-flex>
          </v-layout>
        </v-flex>
        <v-flex d-flex xs12 sm3 md3>
          <v-layout row wrap>
            <v-flex d-flex>
              <v-layout row wrap>
                <v-flex v-for="n in 1" :key="n" d-flex xs12>
                  <v-card>
                    <v-card-title primary class="subheading">Valores</v-card-title>
                    <v-card-text class="headline">R$ Valor do pedido</v-card-text>
                    <v-card-text>
                      <p class="caption">Valor total do desconto: R$ 0,00
                        <br>Total do frete : R$ 49,90
                      </p>
                    </v-card-text>
                  </v-card>
                </v-flex>
              </v-layout>
            </v-flex>
          </v-layout>
        </v-flex>
        <v-flex d-flex xs12 sm3 md3>
          <v-layout row wrap>
            <v-flex d-flex>
              <v-layout row wrap>
                <v-flex v-for="n in 1" :key="n" d-flex xs12>
                  <v-card>
                    <v-card-title primary class="subheading">Status</v-card-title>
                    <v-card-text class="headline">Status atualo do pedido (colorido)</v-card-text>
                    <v-layout align-end justify-center>
                      <v-btn round color="info" class="white--text">Reprocessar
                        <v-icon right dark>cached</v-icon>
                      </v-btn>
                    </v-layout>
                  </v-card>
                </v-flex>
              </v-layout>
            </v-flex>
          </v-layout>
        </v-flex>
        <v-flex d-flex xs12 sm6 md8 child-flex>
          <v-card>
            <v-card-text>
              <v-layout row>
                <v-flex xs12 sm12>
                  <v-list>
                    <v-list-group
                      v-for="item in items"
                      v-model="item.active"
                      :key="item.title"
                      :prepend-icon="item.action"
                      no-action
                    >
                      <v-list-tile slot="activator">
                        <v-list-tile-content>
                          <v-list-tile-title>{{ item.title}}</v-list-tile-title>
                          <v-list-tile-action-text>{{ item.sku }} | {{ item.refId }}</v-list-tile-action-text>
                        </v-list-tile-content>
                      </v-list-tile>
                      <v-list-tile v-for="subItem in item.items" :key="subItem.title" @click>
                        <v-list-tile-content>
                          <v-list-tile-title>{{ subItem.title }}</v-list-tile-title>
                        </v-list-tile-content>
                        <v-list-tile-action>
                          <v-icon>{{ subItem.action }}</v-icon>
                        </v-list-tile-action>
                      </v-list-tile>
                    </v-list-group>
                  </v-list>
                </v-flex>
              </v-layout>
            </v-card-text>
          </v-card>
        </v-flex>
        <v-flex d-flex xs12 sm6 md4>
          <v-card>
            <v-card-text>
              <v-card-title primary class="subheading">Meios de Pagamento</v-card-title>
              <v-card-text class="headline">Cartão de crédito</v-card-text>
              <v-card-text>
                <p class="caption">R$ 2.298,90
                  <br>Data de vencimento: 24/01/2019
                </p>
              </v-card-text>
            </v-card-text>
          </v-card>
        </v-flex>
        <v-flex d-flex xs12 sm12 md12>
          <v-card-text>
            <v-timeline>
              <v-timeline-item v-for="n in 4" :key="n" color="green" large>
                <span slot="opposite">HORA - DIA/MES</span>
                <v-card class="elevation-2">
                  <v-card-title class="headline">Lorem ipsum</v-card-title>
                  <v-card-text>Lorem ipsum dolor sit amet, no nam oblique veritus. Commune scaevola imperdiet nec ut, sed euismod convenire principes at. Est et nobis iisque percipit, an vim zril disputando voluptatibus, vix an salutandi sententiae.</v-card-text>
                </v-card>
              </v-timeline-item>
            </v-timeline>
          </v-card-text>
        </v-flex>
      </v-layout>
    </v-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      lorem:
        'Lorem ipsum dolor sit amet, mel at clita quando. Te sit oratio vituperatoribus, nam ad ipsum posidonium mediocritatem, explicari dissentiunt cu mea. Repudiare disputationi vim in, mollis iriure nec cu, alienum argumentum ius ad. Pri eu justo aeque torquatos.',
      items: [
        {
          action: 'shopping_cart',
          title: 'Nome do Conjunto',
          sku: 'SKU do Conjunto',
          refId: 'REF_IF do Conjunto',
          active: true,
          items: [
            { title: 'Desc. Componente do prod' },
            { title: 'SKU do componente' },
            { title: 'REF_ID do componente' }
          ]
        },
        {
          action: 'shopping_cart',
          title: 'Nome do Conjunto',
          sku: 'SKU do Conjunto',
          refId: 'REF_IF do Conjunto',
          items: [
            { title: 'Desc. Componente do prod' },
            { title: 'SKU do componente' },
            { title: 'REF_ID do componente' }
          ]
        }
      ]
    }
  }
}
</script>


