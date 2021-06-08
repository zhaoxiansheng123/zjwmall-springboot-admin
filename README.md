# springboot-admin-demo
Spring Boot Admin 本身提供监控告警功能，但是默认只提供了Hipchat、Slack等国外流行的通讯软件的集成；默认也支持邮件通知，本示例主要考虑到国内很多公司使用钉钉进行办公交流，故扩展了钉钉机器人通知；

### 钉钉机器人开通方法
1. 新建一个群聊；
2. 添加钉钉机器人；

![](https://github.com/luoyoubao/springboot-admin-demo/blob/master/images/dingtalk01.jpg)
![](https://github.com/luoyoubao/springboot-admin-demo/blob/master/images/dingtalk02.jpg)

3. 将钉钉机器人webhook-token配置到项目中，当有服务上下线的时候即会有消息通知；
PS:关于钉钉机器人更详细的文档请参见:<br>
https://open-doc.dingtalk.com/docs/doc.htm?spm=a219a.7629140.0.0.xSiICS&treeId=257&articleId=105735&docType=1#s0


--------zjw 必须是公网IP，局域网不行
1.下载钉钉PC 18511321960/zjw103697
2.https://developers.dingtalk.com/document/app/custom-robot-access?spm=ding_open_doc.document.0.0.6d9d28e1tCgCJW#topic-2026027
<dependency>
    <groupId>commons-codec</groupId>
    <artifactId>commons-codec</artifactId>
    <version>1.10</version>
</dependency>

docker打包，参考mall的
右侧 Maven Project lifecycle类别查看
1.首先mall-common、mall-mbg、mall-security依次执行install
2.然后在对单个进行打包即可：
    mall-registry 执行package
    mall-config 执行package
    mall-admin 执行package
    按照上面的顺序1,2,3,4,5...8执行就行，然后执行下面的

1.springboot-admin
	- http://39.98.113.91:8001
	--
	docker run -p 8101:8101 --name springboot-admin \
        -v /etc/localtime:/etc/localtime \
        -v /mydata/app/demo/logs:/var/logs \
        -d mall/springboot-admin:1.0.0-SNAPSHOT
