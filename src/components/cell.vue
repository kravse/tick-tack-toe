<template>
  <div class="cell">
    <p>{{current}}</p>
  </div>
</template>

<script>
export default {
  name: 'cell',
  props: ['current'],
  data () {
    return {
      value: ''
    }
  },
  methods: {
    hello: function () {}
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.cell {
  border: 1px solid;
  height: 60px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}
</style>
