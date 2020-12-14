# EchoChien
### 1. React的事件绑定
    <button onClick={() => this.handleClick()}>Click me</button> /* handleClick（） {....} */
    每次渲染组件时都会创建不同的回调函数，大多数情况是没有问题，但如果该回调函数作为 prop 传入子组件时，这些组件可能会进行额外的重新渲染
    所以比较好的写法：
    在constructor中绑定this； 
    <button onClick={this.handleClick}>Click me</button> /* handleClick= （） => {....}* /;
    <button onClick={this.handleClick.bind(this)}>Click me</button> /* handleClick（） {....} */
### 2.React向事件处理程序传递参数
    <button onClick={(e) => this.deleteRow(id, e)}>Delete Row</button>
    <button onClick={this.deleteRow.bind(this, id)}>Delete Row</button>
    React 的事件对象 e 会被作为第二个参数传递。如果通过箭头函数的方式，事件对象必须显式的进行传递，而通过 bind 的方式，事件对象以及更多的参数将会被隐式的进行传递
    
### 3.React-form表单处理多个输入
    当需要处理多个 input 元素时，我们可以给每个元素添加 name 属性，并让处理函数根据 event.target.name 的值选择要执行的操作：如：
    class Reservation extends React.Component {
      constructor(props) {
        super(props);
        this.state = {
          isGoing: true,
          numberOfGuests: 2
        };
        this.handleInputChange = this.handleInputChange.bind(this);
      }
      handleInputChange(event) {
        const target = event.target;
        const value = target.name === 'isGoing' ? target.checked : target.value;
        const name = target.name;
        this.setState({
          [name]: value
        });
      }
      render() {
        return (
          <form>
            <label>
              参与:
              <input
                name="isGoing"
                type="checkbox"
                checked={this.state.isGoing}
                onChange={this.handleInputChange} />
            </label>
            <br />
            <label>
              来宾人数:
              <input
                name="numberOfGuests"
                type="number"
                value={this.state.numberOfGuests}
                onChange={this.handleInputChange} />
            </label>
          </form>
        );
      }
    }








































