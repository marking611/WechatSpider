##WechatSpider 能做什么
* 是一依赖于jsoup通过搜狗引擎来抓取微信公共号最新10篇文章的工具类
* 提供最基础的思路，大家自己自由发挥吧，改成别的语言也比较简单
* 转眼已经两年没有更新了，时光过的好快，有很多中间人模式的更加稳定，但是操作起来稍微复杂一点吧

##如何使用

* 首先导入 wechat.jar（需通过maven编译） 和 jsoup.jar 包到工程目录
* 实例化类 `WechatSpider spider = new WechatSpider("xiaomigongsi0406");` 参数为微信公共号的别名，通过搜过搜索相关的公众号，查看微信号
![我不写java好多年](http://git.oschina.net/uploads/images/2017/0116/201745_69a1cdb8_80950.png "查找示例")
* 然后可以获取标题，作者，时间，内容，url，以及文章内图片等信息的列表

##如何把微信的文章保存到MySQL

* WechatSpider 获取某个公共号最近10篇文件（搜狗限制）

```java
	WechatSpider spider = new WechatSpider("xiaomigongsi0406");//小米
        String listUrl = spider.getListUrl();
        System.out.println(listUrl);
        List<String> list = spider.getTopicUrls(listUrl);
        for (String url : list) {
        	System.out.println(url);
		Topic topic = spider.getTopicByUrl(url);
		System.out.println(topic.getTitle());
	}
```

##程序健壮性
* 运行一个月，每天抓取100条左右，暂时没有异常出现
* 微信推送的文章内的图片都是webp格式,在IOS上显示会有一定的问题，如果下载到自己本地服务器记得转格式
* 验证码问题暂时解决

##有问题反馈
在使用中有任何问题，欢迎留言反馈给我，可以用以下联系方式跟我交流。代码非常简单，希望大家有问题能够自己先解决一下，谢谢。