# saturn-sdk-node
### 1.npm 引入
开发前需先安装环境依赖：<a  target="_blank" href="https://www.npmjs.com/">npm 地址<a>。

### 2.SDK 获取
npm install aws-sdk

### 3.创建client
#### 1. 引入整个开发工具包
var AWS = require('aws-sdk');
#### 1. 2.仅引入对象存储服务

```javascript
var AWS = require('aws-sdk');
var s3 = new AWS.S3({apiVersion: '2006-03-01'});
s3.endpoint = "https://s3.cn-north-1.jdcloud-oss.com"
s3.config.update({
  accessKeyId: "your_accessKeyId",
  secretAccessKey: "your_secretAccessKey",
  s3ForcePathStyle: true,
  signatureVersion: "v4"
})
```
### 4.创建存储空间（Bucket）

```javascript
// Create Client
var AWS = require('aws-sdk');
// Import the AWS SDK only for S3
var s3 = new AWS.S3({apiVersion: '2006-03-01'});
s3.endpoint = "https://s3.cn-north-1.jdcloud-oss.com"
s3.config.update({
  accessKeyId: "XXXXXXXXXXXXXXXXXXXXXXXXXX",
  secretAccessKey: "yyyyyyyyyyyyyyyyyyyyyyyyyyy",
  signatureVersion: "v4"
})


// Create Bucket
var newBuket = {
  Bucket: 'myAPPname'
}

s3.createBucket(newBuket, function (err, data) {
    if (err) console.log(err, err.stack) // an error occurred
    else {
      console.log(data)
    }
  }
)
```
### 如何把我所有我需要的方法封装成一个脚本，只要输入命令行就可以进行操作？
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210622170301365.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80Mjg0MTkzNw==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210622170353511.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80Mjg0MTkzNw==,size_16,color_FFFFFF,t_70)
通过process.argv.splice(2);可以获取命令行输入的命令，我只需要定义每一个命令所对应的方法就可以实现sdk脚本了
