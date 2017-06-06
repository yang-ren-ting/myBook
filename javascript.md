##react学习
1.过完了阮大神的文章http://www.ruanyifeng.com/blog/2015/03/react.html。
2.使用了阮大神的react，webapck脚手架https://github.com/ruanyf/react-babel-webpack-boilerplate;
3.遇到的问题 
- 尽量使用多使用ES6箭头函数
```javascript
   class App extends Component {
  constructor(props) {
    super(props);
    this.state = { liked: 'aaa' };
    // this.doclick = this.doclick.bind(this); //doclick 使用普通函数 则需要这行代码
  };
  doclick = () => {
    this.setState({
      liked: 'bbb'
    })
  };
  render() {
    var name = ['java', 'javascript', 'css'];
    return (
      <div className="App">
        {
          name.map((x, key) => <p key={key}>{x}</p>)
        }
        <button onClick={this.doclick}>{this.state.liked}</button>
      </div>
    );
  }
}
```
- React Router <br>
开始写的如下代码，一直hashHistory报错;
```javascript
import { Router, Route, hashHistory } from 'react-router';
render((
  <Router history={hashHistory}>
    <Route path="/" component={App}/>
  </Router>,
), document.getElementById('app'));
```
查阅资料后才知道，react-router 更新到了4.0，很多API已经不一样了。history 被纳入了 react-router-dom 文件下的 HashRouter、BrowserRouter等。
因此，写法也改变了，如下：
```javascript
  import { BrowserRouter, Route } from 'react-router-dom'ReactDOM.render(
  <BrowserRouter>
       <Route path="/" component={App}/>
  </BrowserRouter>,
  document.body.appendChild(document.createElement('div'))
);
```








