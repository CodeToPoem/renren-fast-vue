<template>
  <el-tree :data="menus" :props="defaultProps" @node-click="handleNodeClick"></el-tree>
</template>

<script>
export default {
  props: {},
  data() {
    return {
      menus: [],
      defaultProps: {
        children: "children",
        label: "name"
      }
    };
  },
  methods: {
    handleNodeClick(data) {
      console.log(data);
    },
    getMenus() {
      this.$http({
        url: this.$http.adornUrl("/product/category/list/tree"),
        method: "get"
      }).then(({ data }) => {
        console.log("成功获取到菜单", data.data);
        this.menus = data.data;
      });
    }
  },
  computed: {},
  created() {
    this.getMenus();
  },
  mounted() {},
  watch: {},
  components: {}
};
</script>

<style scoped>
</style>
