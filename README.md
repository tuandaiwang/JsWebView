# JsWebView
PSWebView，对H5页面“input”标签的支持，对视频全屏播放的支持，以及优化了基于JSBridge的js与Native的通信，
具体使用如下：  <br/>
## WebView:  <br/>
- WebView采用继承模式拓展原有webview的功能，目前继承关系如下。  <br/>
- PsVideoEnabledWebView -> PsSettingWebView -> PsJsBridgeWebView -> BridgeWebView -> WebView;
- BridgeWebView :  <br/>
- 该类为JSBridge原生类，主要解决js与Native的通信；<br/>
- PsJsBridgeWebView :  <br/>
- 针对团贷业务逻辑中的生命周期进行的封装，该类中提供了JS调用Nativie传递数据的处理接口：IJsResponsibilityChain，采用责任链模式设计；
- PsSettingWebView ：  <br/>
- 针对团贷的通用基础设置进行了封装； <br/>
- PsVideoEnabledWebView ： <br/>
- 针对视频全屏播放进行了封装；  <br/>

## WebChromeClient：  <br/>
- WebChromeClient同样采用集成模式拓展原有功能，目前继承关系如下：  <br/>
- AbstractVideoEnabledWebChromeClient -> AbstractInputLabelChromeClient -> ProgressChromeClient -> WebChromeClient;  <br/>
- AbstractVideoEnabledWebChromeClient ：  <br/>
- 适配视频全屏模式，配合PsVideoEnabledWebView使用；  <br/>
- AbstractInputLabelChromeClient ：  <br/>
- 兼容H5的input标签，该类为抽象类，需要实现，权限请求（读取存储卡权限）、图片加载、接口；<br/>
- ProgressChromeClient ： <br/>
- 对页面加载进度的封装，其中onPageLoading为空实现，可根据需求覆写该方法；  <br/>

上述WebView和WebChromeClient可以根据实际需求自由搭配使用！<br/>
