🔗 项目名称

一个书籍交易app，可用于校内购买高年级书籍节约成本，购买其他课外书，可进行二手书交易

🔗 运行条件

应用平台：OpenHarmony、HarmonyOS
编译目标：API9+
应用模型：Stage
🔗 运行说明
进入欢迎页 import router from '@ohos.router' @Entry @Component struct Welcome { @State message: string = 'Hello World'

aboutToAppear(){ setTimeout(function(){ router.replaceUrl({ url:'pages/Loginpage' }) },9000 ) } build() { Column() { Column() { Swiper() { Image($r('app.media.welcome1')) .width("100%") .height("100%") Image($r('app.media.welcome2')) .width("100%") .height("100%") Image($r('app.media.welcome3')) .width("100%") .height("100%") } .width("100%") .height("100%") .autoPlay(true) } .width("100%") .height("100%") .justifyContent(FlexAlign.Center) } .width("100%") .height("100%") } }

等待片刻后登录界（账号admin，密码123456） import Prompt from '@system.prompt' import prompt from '@ohos.prompt' import router from '@ohos.router' @Entry @Component struct Loginpage { @State message: string = 'Hello World' @State users: string = '' @State password: string = ''

build() { Column() { Column() { Text("登录") .width("200vp") .height("60vp") .offset({ x: "-7.98vp", y: "-105.39vp" }) .textAlign(TextAlign.Center) .fontSize("40fp") TextInput({ placeholder: "账号：" }) .width("200vp") .height("60vp") .offset({ x: "0vp", y: "-67.65vp" }) .placeholderFont({ size: 30 }) .onChange((value: string) => { this.users = value; })

    TextInput({ placeholder: "密码：" })
      .width("200vp")
      .height("60vp")
      .offset({ x: "0vp", y: "-30.4vp" })
      .type(InputType.Password)
      .placeholderFont({ size: 30 })
      .onChange((value: string) => {
        this.password = value;
      })
    Row() {
      Text("验证码登录")
        .width("50%")
        .height("60vp")
        .fontSize("20fp")
      Text("忘记密码？")
        .width("50%")
        .height("60vp")
        .textAlign(TextAlign.End)
        .fontSize("20fp")
    }
    .width("360vp")
    .height("68.65vp")
    .offset({ x: "3.93vp", y: "-16.75vp" })

    Button("登录")
      .width("180vp")
      .height("64.11vp")
      .onClick(() => {
        if (this.users == '' || this.password == '') {
          prompt.showToast({
            message: '用户名和密码不能为空',
            duration: 4000
          });
        } else {
          if (this.users != 'admin' || this.password != '123456') {
            prompt.showToast({
              message: '用户名或密码错误',
              duration: 4000
            });
          } else {
            router.replaceUrl({
              url: 'pages/Homepage'
            })
          }
        }
      }


      )
      .fontSize("35fp")
    Button("注册")
      .width("180vp")
      .height("69.4vp")
      .offset({ x: "0vp", y: "27.94vp" })
      .fontSize("35fp")
    Row() {
      Image($r('app.media.huawei'))
        .width("33%")
        .height("100%")
        .objectFit(ImageFit.Contain)
      Image($r('app.media.QQ'))
        .width("33%")
        .height("100%")
        .objectFit(ImageFit.Contain)
      Image($r('app.media.weixin'))
        .width("33%")
        .height("100%")
        .objectFit(ImageFit.Contain)
    }
    .width("360vp")
    .height("66.89vp")
    .offset({ x: "0vp", y: "79.46vp" })
  }
  .width("100%")
  .height("100%")
  .backgroundImage($r('app.media.login'))
  .backgroundImageSize(ImageSize.Cover)
  .justifyContent(FlexAlign.Center)
}
} }

校对成功后进入主页

import router from '@ohos.router' import web_webview from '@ohos.web.webview'; @Entry @Component struct New { @State message: string = 'Hello World' webviewController:web_webview.WebviewController=new web_webview.WebviewController(); build() { Column() { Column() { Tabs({ barPosition: BarPosition.End }) { TabContent() { Column() { Row() {

            Image($r('app.media.qiandao'))
              .width("15%")
              .height("100%")
              .offset({ x: "42.45vp", y: "0vp" })
              .objectFit(ImageFit.Contain)

            Image($r('app.media.local'))
              .width("15%")
              .height("100%")
              .offset({ x: "180.11vp", y: "0vp" })
              .objectFit(ImageFit.Contain)
            Text("上海")
              .width("20%")
              .height("100%")
              .align(Alignment.End)
              .offset({ x: "180vp", y: "0vp" })
              .fontSize("15fp")
          }
          .width("100%")
          .height("8%")
          Search({})
            .width("100%")
            .height("40vp")
          Column() {
            Text("精选推荐")
              .width("200vp")
              .height("5%")
              .align(Alignment.TopStart)
              .offset({ x: "-80vp", y: "0vp" })
              .fontSize("20fp")
            Swiper() {
                
              Image($r('app.media.chaguan'))
                .width("100%")
                .height("100%")
                .objectFit(ImageFit.Fill)
                .onClick(() => {
                  router.pushUrl({
                    url: 'pages/webbb'

                  });
                })
              Image($r('app.media.huozhe'))
                .width("100%")
                .height("100%")
                .objectFit(ImageFit.Fill)
              Image($r('app.media.shaoyou'))
                .width("100%")
                .height("100%")
                .objectFit(ImageFit.Fill)
            }

            .width("100%")
            .height("25%")
            .autoPlay(true)
            .vertical(false)
            Text("热门书单")
              .width("200vp")
              .height("5%")
              .offset({ x: "-80vp", y: "2.7vp" })
              .fontSize("15fp")
            Row() {
              Row() {
                Image($r('app.media.tuili'))
                  .width("40%")
                  .height("90%")
                  .objectFit(ImageFit.Fill)
                Image($r('app.media.kehuan'))
                  .width("40%")
                  .height("90%")
                  .objectFit(ImageFit.Fill)
              }
              .width("100%")
              .height("80%")
              .align(Alignment.Top)
              .offset({ x: "0vp", y: "-10%" })
              .justifyContent(FlexAlign.SpaceEvenly)
              Row() {
                Text("推理")
                  .width("40%")
                  .height("100%")
                  .textAlign(TextAlign.Center)
                  .fontSize("15fp")
                Text("科幻小说")
                  .width("40%")
                  .height("100%")
                  .textAlign(TextAlign.Center)
                  .fontSize("15fp")
              }
              .width("100%")
              .height("20%")
              .offset({ x: "-360vp", y: "40%" })
              .justifyContent(FlexAlign.SpaceEvenly)
            }
            .width("100%")
            .height("35%")
            .offset({ x: "0vp", y: "4.7vp" })
            Row() {
              Row() {
                Image($r('app.media.lishi'))
                  .width("40%")
                  .height("90%")
                  .objectFit(ImageFit.Fill)
                Image($r('app.media.zhexue'))
                  .width("40%")
                  .height("90%")
                  .objectFit(ImageFit.Fill)
              }
              .width("100%")
              .height("80%")
              .align(Alignment.Top)
              .offset({ x: "0vp", y: "-10%" })
              .justifyContent(FlexAlign.SpaceEvenly)
              Row() {
                Text("历史经典")
                  .width("40%")
                  .height("100%")
                  .textAlign(TextAlign.Center)
                  .fontSize("15fp")
                Text("哲学")
                  .width("40%")
                  .height("100%")
                  .textAlign(TextAlign.Center)
                  .fontSize("15fp")
              }
              .width("100%")
              .height("20%")
              .offset({ x: "-360vp", y: "40%" })
              .justifyContent(FlexAlign.SpaceEvenly)
            }
            .width("100%")
            .height("35%")
            .offset({ x: "0vp", y: "4.7vp" })
          }
          .width("100%")
          .height("85%")
        }
        .width("100%")
        .height("93%")
      }
      .tabBar({ icon: $r('app.media.home'), text: "首页" })
      TabContent() {
        Column() {
          Row() {
            Text("书圈")
              .width("200vp")
              .height("60vp")
              .align(Alignment.Center)
              .offset({ x: "74.59vp", y: "0vp" })
              .textAlign(TextAlign.Center)
              .fontSize("25fp")
            Image($r('app.media.fabu'))
              .width("20%")
              .height("100%")
              .align(Alignment.End)
              .offset({ x: "88vp", y: "0vp" })
              .objectFit(ImageFit.Contain)
          }
          .width("360vp")
          .height("60vp")
          .alignItems(VerticalAlign.Top)
          Row() {
            Image($r('app.media.touxiang'))
              .width("15%")
              .height("20%")
              .objectFit(ImageFit.Contain)
            Column() {
              Text("书友1")
                .width("100%")
                .height("10%")
                .offset({ x: "0vp", y: "0vp" })
              Image($r('app.media.shaoyou'))
                .width("50%")
                .height("50%")
                .offset({ x: "-25%", y: "0vp" })
                .objectFit(ImageFit.Contain)
              Row() {
                Text("这本书很好看，推荐")
                  .width("100%")
                  .height("100%")
                  .align(Alignment.Top)
                  .fontSize("15fp")
                  .fontStyle(FontStyle.Italic)
                  .fontWeight(FontWeight.Normal)
              }
              .width("100%")
              .height("30%")
              Row() {
                Row() {
                  Image($r('app.media.dianzan'))
                    .width("20%")
                    .height("100%")
                    .objectFit(ImageFit.Contain)
                  Text("点赞")
                    .width("80%")
                    .height("100%")
                    .fontSize("15fp")
                }
                .width("50%")
                .height("100%")
                Row() {
                  Image($r('app.media.pinglun'))
                    .width("20%")
                    .height("100%")
                    .objectFit(ImageFit.Contain)
                  Text("评论")
                    .width("80%")
                    .height("100%")
                    .fontSize("15fp")
                }
                .width("50%")
                .height("100%")
              }
              .width("100%")
              .height("10%")
            }
            .width("85%")
            .height("100%")
            .justifyContent(FlexAlign.Start)
          }
          .width("100%")
          .height("45%")
          .offset({ x: "0vp", y: "0.82vp" })
          .alignItems(VerticalAlign.Top)
          Row() {
            Image($r('app.media.touxiang'))
              .width("15%")
              .height("20%")
              .objectFit(ImageFit.Contain)
            Column() {
              Text("书友2")
                .width("100%")
                .height("10%")
              Image($r('app.media.zhexue'))
                .width("50%")
                .height("50%")
                .offset({ x: "-25%", y: "0vp" })
                .objectFit(ImageFit.Contain)
              Row() {
                Text("这本书很好看，推荐")
                  .width("100%")
                  .height("100%")
                  .align(Alignment.Top)
                  .fontSize("15fp")
                  .fontStyle(FontStyle.Italic)
                  .fontWeight(FontWeight.Normal)
              }
              .width("100%")
              .height("30%")
              Row() {
                Row() {
                  Image($r('app.media.dianzan'))
                    .width("20%")
                    .height("100%")
                    .objectFit(ImageFit.Contain)
                  Text("点赞")
                    .width("80%")
                    .height("100%")
                    .fontSize("15fp")
                }
                .width("50%")
                .height("100%")
                Row() {
                  Image($r('app.media.pinglun'))
                    .width("20%")
                    .height("100%")
                    .objectFit(ImageFit.Contain)
                  Text("评论")
                    .width("80%")
                    .height("100%")
                    .fontSize("15fp")
                }
                .width("50%")
                .height("100%")
              }
              .width("100%")
              .height("10%")
            }
            .width("85%")
            .height("100%")
            .justifyContent(FlexAlign.Start)
          }
          .width("100%")
          .height("45%")
          .offset({ x: "0vp", y: "1.11vp" })
          .alignItems(VerticalAlign.Top)
        }
        .width("100%")
        .height("93%")
      }
      .tabBar({ icon: $r('app.media.circle'), text: "书圈" })
      TabContent() {
        Column() {
          Text("出售")
            .width("200vp")
            .height("60vp")
            .textAlign(TextAlign.Center)
            .fontSize("25fp")
          Text("出售流程")
            .width("100%")
            .height("5%")
            .fontSize("15fp")
          Text("1.卖家需完成实名认证")
            .width("100%")
            .height("5%")
            .fontSize("15fp")
          Text("2.点击下面出售填写书籍详情")
            .width("100%")
            .height("5%")
            .fontSize("15fp")
          Text("3.买家下单并填写快递信息")
            .width("100%")
            .height("5%")
            .fontSize("15fp")
          Text("4.交易成功后，卖家可在余额中体现")
            .width("100%")
            .height("5%")
            .fontSize("15fp")
          Text("审核规则")
            .width("100%")
            .height("5%")
            .fontSize("15fp")
          Button("出售")
            .width("180vp")
            .height("55.71vp")
            .offset({ x: "0vp", y: "66.03vp" })
            .fontSize("20fp")
        }
        .width("100%")
        .height("93%")
      }
      .tabBar({ icon: $r('app.media.pron'), text: "出售" })
      TabContent() {
        Column() {
          Text("消息")
            .width("200vp")
            .height("60vp")
            .textAlign(TextAlign.Center)
            .fontSize("25fp")
          Row() {
            Image($r('app.media.tongzhi'))
              .width("15%")
              .height("80%")
              .objectFit(ImageFit.Contain)
            Text("通知消息")
              .width("200vp")
              .height("50%")
              .offset({ x: "0", y: "-25%" })
              .fontSize("15fp")
            Text("暂无通知")
              .width("200vp")
              .height("50%")
              .offset({ x: "-199.47vp", y: "25%" })
              .fontSize("15fp")
          }
          .width("100%")
          .height("10%")
        }
        .width("100%")
        .height("93%")
      }
      .tabBar({ icon: $r('app.media.message'), text: "消息" })
      TabContent() {
        Column() {
          Text("我的")
            .width("200vp")
            .height("60vp")
            .textAlign(TextAlign.Center)
            .fontSize("25fp")
          Row() {
            Image($r('app.media.touxiang'))
              .width("15%")
              .height("80%")
              .objectFit(ImageFit.Contain)
            Text("请登录")
              .width("200vp")
              .height("60vp")
              .fontSize("15fp")
          }
          .width("100%")
          .height("8%")
          Row() {
            Row() {
              Image($r('app.media.gouwuche'))
                .width("20%")
                .height("80%")
                .objectFit(ImageFit.Contain)
              Image($r('app.media.dingdan'))
                .width("20%")
                .height("80%")
                .objectFit(ImageFit.Contain)
              Image($r('app.media.wancheng'))
                .width("20%")
                .height("80%")
                .objectFit(ImageFit.Contain)
              Image($r('app.media.tushu'))
                .width("20%")
                .height("80%")
                .objectFit(ImageFit.Contain)
            }
            .width("100%")
            .height("70%")
            .align(Alignment.Top)
            .offset({ x: "0vp", y: "-15%" })
            .justifyContent(FlexAlign.SpaceEvenly)
            Row() {
              Text("购物车")
                .width("20%")
                .height("100%")
                .textAlign(TextAlign.Center)
                .fontSize("15fp")
              Text("交易中")
                .width("20%")
                .height("100%")
                .textAlign(TextAlign.Center)
                .fontSize("15fp")
              Text("全部订单")
                .width("20%")
                .height("100%")
                .textAlign(TextAlign.Center)
                .fontSize("15fp")
              Text("图书管理")
                .width("20%")
                .height("100%")
                .textAlign(TextAlign.Center)
                .fontSize("15fp")
            }
            .width("100%")
            .height("30%")
            .align(Alignment.Top)
            .offset({ x: "-360vp", y: "35%" })
            .justifyContent(FlexAlign.SpaceEvenly)
          }
          .width("100%")
          .height("10%")
          Row() {
            Image($r('app.media.yue'))
              .width("15%")
              .height("80%")
              .objectFit(ImageFit.Contain)
            Text("余额")
              .width("200vp")
              .height("60vp")
              .fontSize("15fp")
          }
          .width("100%")
          .height("8%")
          Row() {
            Image($r('app.media.jifen'))
              .width("15%")
              .height("80%")
              .objectFit(ImageFit.Contain)
            Text("积分")
              .width("200vp")
              .height("60vp")
              .fontSize("15fp")
          }
          .width("100%")
          .height("8%")
          Row() {
            Image($r('app.media.chengjiu'))
              .width("15%")
              .height("80%")
              .objectFit(ImageFit.Contain)
            Text("成就")
              .width("200vp")
              .height("60vp")
              .fontSize("15fp")
              .onClick(() => {
                router.pushUrl({
                  url: 'pages/chengjiu'

                });
              })
          }
          .width("100%")
          .height("8%")
          Row() {
            Image($r('app.media.shezhi'))
              .width("15%")
              .height("80%")
              .objectFit(ImageFit.Contain)
            Text("设置")
              .width("200vp")
              .height("60vp")
              .fontSize("15fp")
          }
          .width("100%")
          .height("8%")
          Row() {
            Image($r('app.media.kefu'))
              .width("15%")
              .height("80%")
              .objectFit(ImageFit.Contain)
            Text("客服帮助")
              .width("200vp")
              .height("60vp")
              .fontSize("15fp")
          }
          .width("100%")
          .height("8%")
        }
        .width("100%")
        .height("93%")
      }
      .tabBar({ icon: $r('app.media.me'), text: "我的" })
    }
    .width("100%")
    .height("100%")
  }
  .width("100%")
  .height("100%")
  .justifyContent(FlexAlign.Center)
}
.width("100%")
.height("100%")
} }

跳转淘宝 import web_webview from '@ohos.web.webview';

@Entry @Component struct Index { @State message: string = 'Hello World'; webviewController:web_webview.WebviewController=new web_webview.WebviewController();

build() { Column() { Row() { Button(($r('app.media.qiandao'))).onClick(() => { this.webviewController.clearHistory(); }) } .padding(12) .backgroundColor(Color.Gray) .width('100%')

  Web({ src: 'https://taobao.com/', controller: this.webviewController })
}
.height('100%')
} }

成就界面 @Entry @Component struct chengjiu { @State message: string = 'Hello World'

build() { Column() { Column() { Row() { Text("成就中心") .width("200vp") .height("60vp") .offset({ x: "0vp", y: "-360vp" }) .fontSize("25fp") Row() { Image($r('app.media.1')) .width("30%") .height("80%") Image($r('app.media.3')) .width("30%") .height("80%") Image($r('app.media.7')) .width("30%") .height("80%") }
.width("360vp") .height("144.08vp") .offset({ x: "-200vp", y: "-237.89vp" }) .justifyContent(FlexAlign.SpaceEvenly) Row() { Image($r('app.media.15')) .width("30%") .height("80%") Image($r('app.media.30')) .width("30%") .height("80%") Image($r('app.media.60')) .width("30%") .height("80%") }
.width("360vp") .height("144.08vp") .offset({ x: "-560vp", y: "-53.52vp" }) .justifyContent(FlexAlign.SpaceEvenly) Row() { Image($r('app.media.90')) .width("30%") .height("80%") Image($r('app.media.200')) .width("30%") .height("80%") Image($r('app.media.365')) .width("30%") .height("80%") }
.width("360vp") .height("144.08vp") .offset({ x: "-920vp", y: "134.31vp" }) .justifyContent(FlexAlign.SpaceEvenly) }
.width("360vp") .height("100%") .offset({ x: "0vp", y: "0vp" }) }
.width("100%") .height("100%") .position({ x: "0px", y: "0px" }) .justifyContent(FlexAlign.Center) }
.width("100%") .height("100%") } }

🔗 测试说明
如果有测试相关内容需要说明，请填写在这里

🔗 技术架构
H5页面跳转
加密技术
🔗 协作者
AtomGit Logo
zhenghui/yishu27
 公开
搜索...
