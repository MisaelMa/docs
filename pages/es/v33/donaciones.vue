<template>
  <section>
    <p>
      Donar ayudara a mantener el proyecto vivo y actualizado
      Mi Principal proposito es ayudar a otros programadores que quieran realizar facturas con la estrutura mexicana, yo
      como programador me encontraba en la situacion de realizar facturacion pero no tenia herramientas para hacerlo de
      manera rapida como el cliente me lo exigia, entonces conforme paso el tiempo me interese mas en aprende la forma
      de las facturas en xml y pense en desarrollar una herramineta que permita la creaccion de xml en forma de clases y
      objetos y desde luego sellar los comprobantes como lo marca el anexo 20 de mexico
    </p>
    <form action="https://www.paypal.com/cgi-bin/webscr" method="post" target="_top">
      <input type="hidden" name="cmd" value="_s-xclick"/>
      <input type="hidden" name="hosted_button_id" value="LYAK7CBWDNVMY"/>
      <input type="image" src="/Paypal.png" border="0"
             name="submit" title="PayPal - The safer, easier way to pay online!" alt="Donate with PayPal button"/>
      <img alt="" border="0" src="/static/Paypal.png" width="1" height="1"/>
    </form>
  </section>

</template>

<script lang="ts">
import { defineComponent, onMounted, useStore } from "@nuxtjs/composition-api";
import Markup from "~/components/Markup.vue";

export default defineComponent({
  components: {
    Markup
  },
  setup() {
    const { commit } = useStore()
    onMounted(() => {
      commit('menu/setRoutes', [

      ])
    })
    return {}
  }
})
</script>

<style scoped>

</style>
