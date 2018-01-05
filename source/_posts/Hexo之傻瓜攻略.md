---
title: Hexo博客流程
---
### Hexo搭建个人技术博客的网站，从零开始流程 ###
1. 搭建篇
2. github部署篇
3. 异地速写博客篇
<!-- more -->
### 搭建篇 ###
1. 必备Node.js环境
2. 安装配置hexo：
	- `npm install -g hexo` 安装cli
	- `hexo init` 初始化hexo
	- `npm install` 安装依赖
	- 输入命令：`git clone https://github.com/iissnan/hexo-theme-next themes/next` （next为主题名字），来获得更多主题
	- 更改_config.yml文件更换主题，另外注意以下配置项

            theme: next
         	deploy:
            type: git
            repo: https://github.com/Github昵称/Github昵称.github.io.git
            branch: master
3. 设置文章title，在md文件中如下写 
	 >     ---
   	 >     title: 我的博客
  	 >     ---
4. `hexo deploy -g` 或者 `hexo g` 生成博客页面 
5. `hexo server -g` 或者 `hexo s` 本地服务器查看 
    > http://localhost:4000/

### github部署篇 ###
1. 注册Github账号，并创建仓库，名字为 `Github昵称.github.io`
2. 安装hexo-deployer-git自动部署发布工具 `npm install lhexo-deployer-git  --save`
3. hexo g （生成），hexo d （部署），可合并为 hexo d -g
3. 在浏览器访问：https://Github昵称.github.io/

### 异地速写博客篇 ###
先吐槽一下这个title，意思就是我换电脑了，从公司换到家里或者哪天出去旅游在网吧。。。突然想写博客了有木有，怎么办，好着急。。。

**解决方案：** 使用github分支。一个分支用来存放Hexo生成的网站原始的文件，另一个分支用来存放生成的静态网页。

-  直接删除主题文件下的.git文件
-  本地博客根文件夹路径下执行以下命令： 	

	    git init
 		git checkout -b hexo
		git remote add origin https://github.com/Github昵称/Github昵称.github.io.git
		git add .
 		git commit -m "提交说明"
 		git push origin hexo

-  执行到这里，已经把本地的源文件添加到了分支hexo上
-  另外一台电脑上执行 `git clone -b hexo https://github.com/Github昵称/Github昵称.github.io.git`,然后再博客项目执行 `npm install`即可安装好博客环境
-  添加新的 `XX.md`文件放到	`Hexo\source\_posts\` 路径下
-  生成新的博客并部署：
	> hexo g （生成），hexo d （部署），可合并为 hexo d -g
-  上面一步只是生成博客页面并且发布了，不要忘记把你写的 `XX.md` 文件 `add` 上传到你的github仓库中备份！
	