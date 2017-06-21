项目地址:https://github.com/yang-ren-ting/AwesomeProject
###TabNavigator的运用
```
const Home = TabNavigator({
  Chat: {
    screen: Chat,
    navigationOptions:{
            tabBarLabel: '聊天',
            tabBarIcon: ({tintColor，focused}) => (
                <Image
                source={require('')} //加上图片路径
                style={[styles.tabBarIcon, {tintColor:tintColor}]}
            />
            ),
        },
        headerTitle:'聊天',//推荐这种方式设置tab的导航标题
  }
}, {
    animationEnabled: false, // 切换页面时是否有动画效果
    tabBarPosition: 'bottom', // 显示在底端，android 默认是显示在页面顶端的
    swipeEnabled: false, // 是否可以左右滑动切换tab
    backBehavior: 'none', // 按 back 键是否跳转到第一个Tab(首页)， none 为不跳转
    tabBarOptions: {
      activeTintColor: 'green', // 文字和图片选中颜色
      inactiveTintColor: '#f3f3f3', // 文字和图片未选中颜色
      showIcon: true, // android 默认不显示 icon, 需要设置为 true 才会显示
      indicatorStyle: {
        height: 0  // 如TabBar下面显示有一条线，可以设高度为0后隐藏
      },
      style: {
        backgroundColor: '#fff', // TabBar 背景色
        // height: 44
      },
      labelStyle: {
        fontSize: 12, // 文字大小
      },
    },
  });
Home.navigationOptions = {  
    title: 'My Chats',  
}; //这种方式不推荐
```
这是最基本的TabNavigator的使用，然而，这样写的话代码重复太多，并且不便于维护，所以我们将最通用的属性navigationOptions 进行了封装
```
onst TabOptions = (tabBarTitle,normalImage,tintColor,headTitle) => {
    const tabBarLabel = tabBarTitle;
    const tabBarIcon = (({tintColor,focused})=> {
        return(
            <Image
                source={normalImage}
                style={[styles.tabBarIcon, {tintColor: focused}]}
            />
        )
    });
    const headerTitle = headTitle;
    const headerTitleStyle = {fontSize:16,color:'white',alignSelf:'center'};
    // header的style
    const headerStyle = {backgroundColor:'#999'};
    const tabBarVisible = true;
    const header = null;
    return {tabBarLabel,tabBarIcon,headerTitle,headerTitleStyle,headerStyle,tabBarVisible};
};
```
下面我们写tab的navigationOptions属性直接这样即可
```
 navigationOptions: ()=> TabOptions('titile','图片路径','图片颜色','导航标题')。
```