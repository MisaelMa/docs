<template>
  <v-row>
    <v-col cols="12" v-for="sect of complementsList" :key="sect.uuid">
      <section :id="sect.uuid" class="container pa-4 pa-sm-6 pa-md-8 container--fluid">
        <h3 class="display-1 basil--text">
          # {{ sect.title }}
        </h3>
        <v-card v-for="(table,st) of sect.table" :key="st" elevation="0">
          <v-card-text>
            {{ table.title }}
            <v-simple-table>
              <thead>
              <tr>
                <th align="center">Function</th>
                <th align="center">Type</th>
                <th align="center">properties</th>
                <th align="center">Enum</th>
                <th align="center">Descripcion</th>
              </tr>
              </thead>
              <tbody>
              <tr v-for="(item,t) of table.data" :key="t">
                <td>
                  <v-btn text link tile color="primary">
                    {{ item.function }}
                  </v-btn>
                </td>
                <td>{{ item.type }}</td>
                <td v-html="item.properties"></td>
                <td>{{ item.enum }}</td>
                <td>{{ item.descripcion }}</td>
              </tr>
              </tbody>
            </v-simple-table>
          </v-card-text>
        </v-card>
        <div v-for="(code,c) of sect.markup" :key="c">
          <Markup :code="code.code" :language="code.language"/>
          <br>
        </div>
      </section>
    </v-col>
  </v-row>
</template>

<script lang="ts">
import { defineComponent, onMounted, useStore } from "@nuxtjs/composition-api";
import Markup from "~/components/Markup.vue";
import { complementsList } from "~/util/complements-list";

export default defineComponent({
  components: {
    Markup
  },
  setup() {

    const m = () => {
      return test.map((d, i) => {
        return {
          id: 50 + i,
          isActive: 1,
          name: d.toLowerCase(),
          fatherID: 1,
          level: '1',
          url: '/es/v33/complementos/#' + d.toLowerCase(),
          icon: '',
          children: []
        }
      })
    }
    const test = [
      "INE",
      "PAGO10",
      "CCE11",
      "AEROLINEAS",
      "COMBUSTIBLE",
      "DECRETO",
      "DESTRUCCION",
      "REGISTRO-FISCAL",
      "DONATARIAS",
      "OBRAS-ARTE",
      "VALES-DESPENSA",
      "DIVISAS",
      "TURISTAS",
      "LEYENDA-FISCAL",
      "PAGO-ESPECIE",
      "SPEI",
      "SERVICIOS-PARCIALES-DE-CONTRUCCION",
      "VEHICULO-USADO",
      "INGRESOS-HIDROCARBUROS",
      "GASTOS-HIDROCARBUROS",
      "IMPLOCAL"
    ]
    const { commit } = useStore()
    onMounted(() => {
      commit('menu/setRoutes', m())
    })
    return {
      complementsList
    }
  }
})
</script>

<style scoped>

</style>
