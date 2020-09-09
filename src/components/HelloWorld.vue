<script>
import myComponent from './MyComponent.vue';
import funComponent from './FunctionalComponent'
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      placeholderText: '123@qq.com',
      newTodoText: '2',
      tirmData: ' Asb adfded  '
    }
  },
  methods: {
    inputText(e) {
      console.log(e);
    }
  },
  render() {
    const inputAttrs = {
      type: 'email',
      placeholder: 'Enter your email'
    };
    const html = '<p>我是 html</p>'
    return (
      <div>
        <h3>内容</h3>
        {/* 纯文本 */}
        <p>hello, I am Gopal</p>
        {/* 动态内容 */}
        <p>hello { this.msg }</p>
        {/* 输入框 */}
        <input />
        {/* 自定义组件 */}
        <myComponent {
          ...{
            scopedSlots: {
              test: ({user}) => (
                <div>{user.name}</div>
              )
            }
          }
        }></myComponent>
        <h3>Attributes/Props</h3>
        {/* 属性*/}
        <div><input placeholder="111" /></div>
        {/*动态属性*/}
        <div>
        <input
            type="email"
            placeholder={this.placeholderText}
          />
        </div>
        {/* 结构赋值 */}
        <input {...{ attrs: inputAttrs }} /> 
        <h3>Slots</h3>
        {/* 具名插槽 作用域插槽 */}
        <myComponent {
          ...{
            scopedSlots: {
              test: ({user}) => (
                <div>{user.name}</div>
              )
            }
          }
        }>
          <header slot="header">header</header>
          <header slot="content">content</header>
          <footer slot="footer">footer</footer>
        </myComponent>
        {/* 指令 */}
        {/* v-model */}
        <div><input vModel={this.newTodoText} /></div>
        {/* v-model 以及修饰符 */}
        <div><input vModel_trim={this.tirmData} /></div>
        {/* v-on 监听事件 */}
        <div><input vOn:input={this.inputText} /></div>
        {/* v-on 监听事件以及修饰符 */}
        <div><input vOn:click_stop_prevent={this.inputText} /></div>
        {/* v-html */}
        <p domPropsInnerHTML={html} />
        {/* 函数式组件 */}
        <funComponent message="Gopal"></funComponent>
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
