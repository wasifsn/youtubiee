<template>
  <div>
    <input type="text" v-model="search" @input="onInput" />
  </div>
</template>


<script>
export default {
  name: "searchBar",
  data: function() {
    return {
      search: ""
    };
  },
  methods: {
    onInput: function(e) {
      this.$emit("termChange", this.search);
    }
  },
  computed: {}
  //   mounted: {}
};
</script>

<style scoped>
input {
  width: 75%;
}

div {
  text-align: center;
  margin: 20px;
}
</style>