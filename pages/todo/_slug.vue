<template>
  <div>
    <hello-world :render-func="md.vue.render" :static-render-funcs="md.vue.staticRenderFns"></hello-world>

    <br>
    {{ md.html }}
  </div>
</template>

<script>
import HelloWorld from "~/components/HelloWorld";

export default {
  name: "Todo",

  async asyncData({ params }) {
    const md = await import(`~/markdowns/${params.slug}.md`);

    return {
      md: md
    };
  },

  components: { HelloWorld }
};
</script>

