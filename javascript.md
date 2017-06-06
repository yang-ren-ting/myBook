##react学习
1.过完了阮大神的文章http://www.ruanyifeng.com/blog/2015/03/react.html。
2.使用了阮大神的react，webapck脚手架https://github.com/ruanyf/react-babel-webpack-boilerplate;
3.遇到的问题
 `class App extends Component {
  constructor(props) {
    super(props);
    this.state = { liked: 'aaa' };
    // this.doclick = this.doclick.bind(this); //doclick 使用普通函数 则需要这行代码
  };
  doclick = () => {
    this.setState({
      liked: 'bbb'
    })
    fetch('https://api.github.com/users/octocat/gists')
      .then(function (response) {
        console.log(response)
      }).then(function (body) {
        // document.body.innerHTML = body
      })
  };
  componentWillMount = () => {
    console.log('app componentWillMount ')
  };
  render() {
    var name = ['java', 'javascript', 'css'];
    return (
      <div className="App">
        {
          name.map((x, key) => <p key={key}>{x}</p>)
        }
        <button onClick={this.doclick}>{this.state.liked}</button>
        <Input />
      </div>
    );
  }
}`
