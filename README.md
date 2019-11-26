
# 项目发布快照

[![license](https://img.shields.io/badge/license-Apache%202.0-blue)](http://www.apache.org/licenses/LICENSE-2.0.html) [![Central](https://img.shields.io/badge/maven%20central-v2-brightgreen)](https://search.maven.org/artifact/com.viiyue.plugins/plugin-release-parent/2/pom)

用于抽离项目发布到Maven中央库的一些基础配置，从而使子项目可以忽略这些繁琐的配置，仅关注于当前项目所需的配置。

凡是继承此pom配置的子项目将获得这些公用配置，并使用一些基础命令即可将项目发布到Maven中央库。



## 公共内容

- Licenses
  - license
    - name - The Apache Software License, Version 2.0
    - url - http://www.apache.org/licenses/LICENSE-2.0.txt
- Developer
  - developer
    - id - xbai
    - name - tangxbai
    - email - tangxbai@hotmail.com
    - url - https://github.com/tangxbai
    - roles - Java Developer
- Repositories
  - repository
    - id - ossrh
    - name - Sonatype Nexus Snapshots
    - url - https://oss.sonatype.org/content/repositories/snapshots
- DistributionManagement
  - snapshotRepository
    - id - ossrh
    - name - Sonatype Nexus Snapshots
    - url - https://oss.sonatype.org/content/repositories/snapshots
  - repository
    - id - ossrh
    - name - Nexus Release Repository
    - url - https://oss.sonatype.org/service/local/staging/deploy/maven2
- Profiles
  - default
    - 生成项目相关jar包 - xxx.jar
  - license
    - 添加文件许可证头部注释
  - release
    - 生成项目jar源文件 - xxx-source.jar
    - 生成项目文档 - xxx-javadoc.jar
    - 对文件进行签名 - xxx-xxx.xxx.asc



## 配置setting.xml

更改Maven配置，这一步骤是必不可少的，如果已经配置了其他server，再添加一个 `ossrh` 的server节点即可。

```xml
<servers>
    <server>
        <id>ossrh</id>
        <username>...</username>
        <password>***</password>
    </server>
</servers>
```



## 基础命令

```shell
# 清空安装目录
$ mvn clean

# 清空并打包项目资源
$ mvn clean package

# 清空并安装项目资源（会判断是否有license.txt文件，有则自动添加文件头部许可证注释）
$ mvn clean install
$ mvn clean install -Plicense

# 清空并打包项目然后发布资源到Maven中央库
$ mvn clean deploy -Prelease
```



## 许可证忽略文件规则

```ini
[Mac]
**/.DS_Store

[RCS]
**/RCS
**/RCS/**

[SCCS]
**/SCCS
**/SCCS/**

[CVS]
**/CVS
**/CVS/**
**/.cvsignore

[Arch]
**/.arch-ids
**/.arch-ids/**

[Flash]
**/*.swf

[Fonts]
**/*.svg
**/*.eot
**/*.ttf
**/*.woff

[Bazaar]
**/.bzr
**/.bzr/**

[Git]
**/.git
**/.git/**
**/.gitignore
**/.gitmodules

[Darcs]
**/_darcs
**/_darcs/**
**/.darcsrepo
**/.darcsrepo/**
**/-darcs-backup*
**/.darcs-temp-mail

[Travis]
**/.travis.yml

[BitKeeper]
**/BitKeeper
**/BitKeeper/**
**/ChangeSet
**/ChangeSet/**

[Mercurial]
**/.hg
**/.hg/**
**/.hgignore

[Subversion]
**/.svn
**/.svn/**

[Json files]
**/*.json

[Netbeans]
**/nb-configuration.xml

[Descriptors]
**/MANIFEST.MF

[SurroundSCM]
**/.MySCMServerInfo

[Markdown files]
**/*.md

[Checksum files]
**/*.md5
**/*.sha1

[IDEA projet files]
**/*.iml
**/*.ipr
**/*.iws
.idea/**

[Visual SourceSafe]
**/vssver.scc

[ServiceLoader files]
**/META-INF/services/**

[Code coverage tools]
**/cobertura.ser
**/.clover/**

[Eclipse project files]
**/.classpath
**/.project
**/.settings/**

[Binary files - images]
**/*.jpg
**/*.png
**/*.gif
**/*.ico
**/*.bmp
**/*.tiff
**/*.tif
**/*.cr2
**/*.xcf

[Binary files - programs]
**/*.class
**/*.exe
**/*.dll
**/*.so

[Binary files - archives]
**/*.jar
**/*.zip
**/*.rar
**/*.tar
**/*.tar.gz
**/*.tar.bz2
**/*.gz

[Office documents]
**/*.xls
**/*.doc
**/*.odt
**/*.ods
**/*.pdf
**/*.xlsx
**/*.docx
**/*.ppt
**/*.pptx

[Serena Dimensions Version 10]
**/.metadata
**/.metadata/**

[Maven project's temporary files]
**/target/**
**/test-output/**
**/release.properties
**/dependency-reduced-pom.xml
**/release-pom.xml
**/pom.xml.releaseBackup

[Miscellaneous typical temporary files]
**/*~
**/#*#
**/.#*
**/%*%
**/._*
**/.repository/**

[Customize]
mvnw
mvnw.cmd
ICLA
KEYS
NOTICE
LICENSE
**/*.dat
**/*.lck
**/*.log
**/*.doc
**/*.docx
**/*.ppt
**/*.ctrl
**/*.providers
**/*.factories
**/*.properties
**/META-INF/**
.factorypath
.gitattributes
```



## 关于作者

- 邮箱：tangxbai@hotmail.com
- 掘金： https://juejin.im/user/5da5621ce51d4524f007f35f
- 简书： https://www.jianshu.com/u/e62f4302c51f
- Issuse：https://github.com/tangxbai/viiyue-release-snapshot/issues