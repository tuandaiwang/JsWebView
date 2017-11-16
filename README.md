# JsWebView
PSWebView，对H5页面“input”标签的支持，对视频全屏播放的支持，以及优化了基于JSBridge的js与Native的通信。

# Download

---

 Grab via Maven:

```
<dependency>
  <groupId>com.paison.lib</groupId>
  <artifactId>jswebview</artifactId>
  <version>1.0.0</version>
  <type>pom</type>
</dependency>
```
or Gradle:

```
 dependencies  { 
        compile 'com.paison.lib:jswebview:1.0.0' 
    }
```
 ---
 
## Example Use it in Android

### 加载视频

```
mTdAdvertisingWebView = new PsVideoEnabledWebView(this);
        mTdAdvertisingWebView.setLayoutParams(new ViewGroup.LayoutParams(-1, -1));
        setContentView(mTdAdvertisingWebView);
        mTdAdvertisingWebView.setUserAgentType("");
        mTdAdvertisingWebView.setWebChromeClient(new AbstractVideoEnabledWebChromeClient(this,
                mTdAdvertisingWebView) {
                
            }
             @Override
            public void displayImage(Activity activity, Context context, String path,
                // 展示图片
              }

            @Override
            public void clearMemoryCache() {
              //清除缓存
            }

            @Override
            public void applyPermissions(final String[] permissions, 
            final ApplyPermissionsListener listener) {
                 //申请需要的权限
                        });
            }


            @Override
            public void onPageLoading(WebView view, int loadingType, int newProgress) {
                super.onPageLoading(view, loadingType, newProgress);
                //设置加载度
            }
        });
        mTdAdvertisingWebView.loadUrl("https://v.qq.com/x/cover/6t49nzhhbg132je.html");
```

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
 
 ## LICENSE
 
 ---
 ```
 Licensed under the Apache License, Version 2.0 (the "License")And partion of MIT;
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at
 
        http://www.apache.org/licenses/LICENSE-2.0
 
    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
 
 ```
