## 小程序踩坑&&记录
<p>此文档仅记录taro+ts+react的钉钉小程序的踩坑记录</p>

- taro日期选择框Picker 钉钉端存在选择器颗粒度的问题，原因：官方bug，目前已有issue:
 [#9350](https://github.com/NervJS/taro/issues/9350)
- taro设置flex布局时子元素将不适用position:absulute布局,定位父级元素将出现高度问题，如需定位确保父元素没有flex属性即可
- 在ios和android之间原生列表的渲染可能会出现string || number类型判断的错误而导致渲染失败的，常会出现在switch 的case语句中，解决方案是类型强制转换=>Number(str.toSting())或其他方式也可（ios会默认转换为number，但android不会）
- @antmJS/vantUI日期选择框Picker 钉钉端存在选择器颗粒度的问题，原因：官方bug，已提issue:
 [#151](https://github.com/AntmJS/vantui/issues/151)
- position:sticky 存在兼容性问题，具体表现为滚动下拉时存在点击属性项失效的情况，改为滚动事件实现即可
## uni-app 打包android记录
- 接收低功率蓝牙二进制码的时候需要用到TextDecoder 和 TextEncoder转码，具体表现为使用uni-app第三方插件实现mqtt连接，目前只有一个可以实现tcp://请求头连接，个人推测是需要在安卓原生插件上实现一些请求逻辑，目前收费偏多，个人实现流程为https://ext.dcloud.net.cn/plugin?id=9178#detail 此插件+ TextDecoder实现
