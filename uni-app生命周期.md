####应用声明周期


1.<kbd>onLaunch</kbd> 当uni-app初始化完成时触发（全局只触发一次）  
2.<kbd>onShow</kbd> 当uni-app启动，或从后台进入前台显示  
3.<kbd>onHide</kbd> 当uni-app从前台进入后台
4.<kbd>onUniNViewMessage</kbd> 对nvue页面发送的数据进行监听

*应用声明周期仅可在App.vue中监听，在其它页面监听无效。*

####页面生命周期

1.<kbd>onLoad</kbd> 监听页面加载，其参数为上个页面传递的数，参数类型为Object
2.<kbd>onShow</kbd> 监听页面显示。页面每次出现在屏幕上都触发，包括从下级页面点返回露出当前页面
3.<kbd>onReady</kbd> 监听页面初次渲染完成。*注意如果渲染速度快，会在页面进入动画完成前触发*
4.<kbd>onHide</kbd> 监听页面隐藏
5.<kbd>onUnload</kbd> 监听页面卸载
6.<kbd>onResize</kbd> 监听窗口尺寸变化(APP、微信小程序)
7.<kbd>onPullDownRefresh</kbd> 监听用户下拉动作，一般用于下拉刷新
8.<kbd>onReachBottom</kbd> 页面滚动到底部的事件，常用于上拉加载下一页数据。
9.<kbd>onTabItemTap</kbd> 点击tab时触发，参数为Object（微信小程序、百度小程序、H5、App（自定义组件模式））
10.<kbd>onShareAppMessage</kbd> 用户点击右上角分享 （微信小程序、百度小程序、字节跳动小程序、支付宝小程序）
11.<kbd>onPageScroll</kbd> 监听页面滚动，参数为Object
12.<kbd>onNavigationBarButtonTap</kbd> 监听原生标题栏按钮点击事件，参数为Object
13.<kbd>onBackPress</kbd> 监听页面返回，返回 event ={from:backbutton、 navigateBack} ，backbutton 表示来源是左上角返回按钮或 android 返回键；navigateBack表示来源是 uni.navigateBack 
*H5端只能监听页面导航栏的返回按钮的点击事件，不能监听浏览器返回以及手机的返回*
14.<kbd>onNavigationBarSearchInputChanged</kbd> 监听原生标题栏搜索输入框输入内容变化事件
15.<kbd>onNavigationBarSearchInputConfirmed</kbd> 监听原生标题栏搜索输入框搜索事件，用户点击软键盘上的“搜索”按钮时触发。
16.<kbd>onNavigationBarSearchInputClicked</kbd> 监听原生标题栏搜索输入框点击事件
  