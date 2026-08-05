杏悦2地址娱乐【Q-——333307——】杏悦2地址娱乐【 辋芷《888yx●vip》 】
杏悦2地址娱乐【Q-——333307——】杏悦2地址娱乐【 辋芷《888yx●vip》 】

 从0到1：用Github Action自动化部署你的前端项目

前端开发最繁琐的环节是什么？部署。每次改完代码，手动npm run build，再上传服务器...这种重复劳动不仅浪费时间，还容易出错。今天我们就来聊聊如何用Github Action一键解决部署难题。

 为什么选择Github Action？

Github Action是Github官方推出的CI/CD工具，它最大的优势就是自动化——你的代码推送到仓库的那一刻，构建、测试、部署全部自动完成，全程无需人工干预。

相比传统Jenkins，Github Action的配置简单得多，直接在仓库里写一个YAML文件就能搞定。

 核心配置解析

首先，在项目根目录创建`.github/workflows/deploy.yml`文件：

```yaml
name: Deploy to Server

on:
  push:
    branches: [ main ]

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v4
        
      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'
          
      - name: Install dependencies
        run: npm ci
        
      - name: Build project
        run: npm run build
        
      - name: Deploy to server
        uses: easingthemes/ssh-deploy@main
        with:
          SSH_PRIVATE_KEY: ${{ secrets.SSH_PRIVATE_KEY }}
          ARGS: "-rlgoDzvc -i --delete"
          SOURCE: "dist/"
          REMOTE_HOST: ${{ secrets.REMOTE_HOST }}
          REMOTE_USER: ${{ secrets.REMOTE_USER }}
          TARGET: "/var/www/html"
```

 你需要准备什么？

1. SSH密钥对：生成后，将公钥添加到服务器，私钥配置到Github仓库的Secrets中
2. 服务器信息：IP地址、用户名，同样存入Secrets
3. 构建命令：确保你的项目能在CI环境正常构建

 踩坑提醒

- 构建环境默认是纯净的，记得安装必要的依赖
- Secrets是加密存储的，不用担心泄露问题
- 如果构建时间长，考虑使用缓存策略优化

 进阶玩法

搞定基础部署后，你还可以扩展：

- 部署成功后自动发邮件通知
- 集成自动化测试，测试不通过不部署
- 多环境部署（测试环境、生产环境）

现在就开始动手吧！把你的部署配置告诉Github，让重复劳动力彻底解放。有任何配置报错或者疑问，欢迎在评论区留言交流，我会第一时间帮你排查解决。如果这篇文章帮到了你，点个赞和在看支持一下，让更多朋友看到这个效率神器！

相关推荐：

https://github.com/adamsjonathan8709/jjgpxy/blob/main/ch%E1%BB%8Di%20g%C3%A0%20%F0%9F%90%94%20%EF%BC%9A%E6%9D%8F%E6%82%A62%E5%AE%98%E6%96%B9%E6%B5%8B%E9%80%9F_%E5%95%AA%E5%A5%88%E5%93%AA%E8%B1%AA%E5%91%80jpcjx.md

<img src="https://i.postimg.cc/JnGs5yWs/xingyue2-00007.png" />

相关推荐：

https://github.com/adamsjonathan8709/jjgpxy/commit/8acba816f618dd7aaffe29fafacbfc99e6920d51

<img src="https://i.postimg.cc/50T67xx8/xingyue2-00009.png" />
相关推荐：

https://github.com/jordanjason7600/yjodzh/blob/main/Th%E1%BB%83%20thao%20%E2%9A%BD%EF%B8%8F%EF%BC%9A%E6%9D%8F%E6%82%A62%E5%AE%98%E6%96%B9%E7%99%BB%E5%BD%95_%E5%B8%9C%E8%BF%9C%E7%B0%A7%E8%AF%A9%E7%87%8Ewvocg.md

<img src="https://i.postimg.cc/XJmpHVVv/xingyue2-00008.png" />
相关推荐：

https://github.com/jordanjason7600/yjodzh/commit/02bb6252c4e29c3edf4ef7d074644d77c48bd9cb

<img src="https://i.postimg.cc/YS2Gjnnm/xingyue2-00001.png" />

资讯来源：新华网、人民网、央视新闻、中新网、凤凰网、澎湃新闻、界面新闻、新浪新闻、搜狐网、财新网、观察者网、第一财经等主流平台，以独树一帜的观察视角与扎实的深度报道能力，在资讯领域收获广泛关注。
