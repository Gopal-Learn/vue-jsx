<script>
export default {
  name: 'My',
  props: {
    msg: String
  },
  data() {
    return {
      user: {
        name: 'Gopal'
      }
    }
  },
  render() {
    return (
      <div>
        {/* 纯文本 */}
        <p>我是自定义组件</p>
        {this.$slots.header}
        {this.$slots.content}
        {this.$scopedSlots.test({
          user: this.user
        })}
        {this.$slots.footer}
      </div>
    );
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
