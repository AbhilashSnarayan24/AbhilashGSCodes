import React from "react";
import Lifecycle from "./Counter.js";

class App extends React.Component {
  constructor() {
    super();
    this.state = {
      showComponent: true,
    };
  }
  render() {
    return (
      <div>
        <button
          onClick={() =>
            this.setState((prev) => {
              showComponent: !prev.showComponent;
            })
          }
        >
          Show/Hide Lifecycle
        </button>
        {this.state.showComponent ? <Lifecycle /> : "null"}
      </div>
    );
  }
}
export default App;
-------------------------------------------------------------------------
import React from "react";
class Lifecycle extends React.Component {
  constructor() {
    super();
    this.state = {
      count: 0,
    };
  }

  componentDidMount() {
    console.log("hello");
  }
  componentDidUpdate(prevState, prevProp) {
    console.log("Update got triggered", this.state.count, prevProp, prevState);
  }
  componentWillUnmount() {
    console.log("unmount phase");
  }
  handleIncrement = () => {
    this.setState({ count: this.state.count + 1 });
  };
  handleDecrement = () => {
    this.setState({ count: this.state.count - 1 });
  };
  render() {
    return (
      <div>
        <button onClick={this.handleIncrement}>+</button>
        <span>{this.state.count}</span>
        <button onClick={this.handleDecrement}>-</button>
      </div>
    );
  }
}
export default Lifecycle;

