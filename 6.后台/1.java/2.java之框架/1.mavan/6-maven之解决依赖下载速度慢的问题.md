### 一、maven的中央仓库在国外网站，国内下载速度极慢，当然也可以通过翻墙来提高速度。

### 二、国内阿里为我们提供了公共的maven镜像，可将它设置为我们的中央仓库镜像

- 1.maven安装目录下conf文件夹中的setting.xml文件，里面的`<mirrorOf></mirrorOf>`标签便是用来配置镜像的

- 2.<mirrorOf></mirrorOf>标签里面放置的是要被镜像的Repository ID。为了满足一些复杂的需求，Maven还支持更高级的镜像配置：

    ①`<mirrorOf>*</mirrorOf>`: 匹配所有远程仓库

    ②`<mirrorOf>repo1,repo2</mirrorOf>`: 匹配仓库repo1和repo2，使用逗号分隔多个远程仓库

    ③`<mirrorOf>*,!repo1</miiroOf>`: 匹配所有远程仓库，repo1除外，使用感叹号将仓库从匹配中排除

### 三、解决方法

编辑setting.xml文件中的`<mirrorOf></mirrorOf>`:

```

    <mirror> 

        <id>alimaven</id> 

        <name>aliyun maven</name> <url>http://maven.aliyun.com/nexus/content/groups/public/</url> 

        <mirrorOf>central</mirrorOf> 

    </mirror> 

```

**注意：由于镜像仓库完全屏蔽了被镜像仓库，当镜像仓库不稳定或者停止服务的时候，Maven仍将无法访问被镜像仓库，因而将无法下载构件。**

    