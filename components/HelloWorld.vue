
<script>
export default {
  props: {
    renderFunc: {
      type: String,
      required: true
    },
    staticRenderFuncs: {
      type: String,
      required: true
    }
  },
  data() {
    return {
      templateRender: null
    };
  },

  created() {
    /* eslint no-new-func: "off" */
    this.templateRender = new Function(this.renderFunc)();
    this.$options.staticRenderFns = new Function(this.staticRenderFuncs)();
  },
  render(createElement) {
    return this.templateRender
      ? this.templateRender()
      : createElement("div", "rendering");
  }
};
</script>
