
# 项目发布快照

[![license](https://img.shields.io/badge/license-Apache%202.0-blue)](http://www.apache.org/licenses/LICENSE-2.0.html) [![Central](https://img.shields.io/badge/maven%20central-v1-brightgreen)](https://search.maven.org/artifact/com.viiyue.plugins/plugin-release-parent/1/pom)

用于抽离项目发布到Maven中央库的一些基础配置，从而使子项目可以忽略这些繁琐的基础信息，仅关注于当前项目所需的配置。

凡是继承此pom配置的子项目使用一些基础命令即可将项目发布到Maven中央库。



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



## 发布到中央仓库

```shell
$ mvn clean deploy -Prelease
```



## 生成License注释

```shell
$ mvn clean install -Plicense
$ mvn clean install
```

以上两种命令都可以，只有在根目录下存在 `license.txt` 许可证头部文件才会自动为指定文件添加许可证头部信息。以下文件会被忽略添加头部许可证信息：

```java
// Miscellaneous typical temporary files
"**/*~"
"**/#*#"
"**/.#*"
"**/%*%"
"**/._*"
"**/.repository/**"

// CVS
"**/CVS"
"**/CVS/**"
"**/.cvsignore"

// RCS
"**/RCS"
"**/RCS/**"

// SCCS
"**/SCCS"
"**/SCCS/**"

// Visual SourceSafe
"**/vssver.scc"

// Subversion
"**/.svn"
"**/.svn/**"

// Arch
"**/.arch-ids"
"**/.arch-ids/**"

// Bazaar
"**/.bzr"
"**/.bzr/**"

//SurroundSCM
"**/.MySCMServerInfo"

// Mac
"**/.DS_Store"

// Serena Dimensions Version 10
"**/.metadata"
"**/.metadata/**"

// Mercurial
"**/.hg"
"**/.hg/**"
"**/.hgignore"

// Git
"**/.git"
"**/.git/**"
"**/.gitignore"
"**/.gitmodules"

// BitKeeper
"**/BitKeeper"
"**/BitKeeper/**"
"**/ChangeSet"
"**/ChangeSet/**"

// Darcs
"**/_darcs"
"**/_darcs/**"
"**/.darcsrepo"
"**/.darcsrepo/**"
"**/-darcs-backup*"
"**/.darcs-temp-mail"

// Maven project's temporary files
"**/target/**"
"**/test-output/**"
"**/release.properties"
"**/dependency-reduced-pom.xml"
"**/release-pom.xml"
"**/pom.xml.releaseBackup"

// Code coverage tools
"**/cobertura.ser"
"**/.clover/**"

// Eclipse project files
"**/.classpath"
"**/.project"
"**/.settings/**"

// IDEA projet files
"**/*.iml"
"**/*.ipr"
"**/*.iws"
".idea/**"

// Netbeans
"**/nb-configuration.xml"

// Descriptors
"**/MANIFEST.MF"

// Binary files - images
"**/*.jpg"
"**/*.png"
"**/*.gif"
"**/*.ico"
"**/*.bmp"
"**/*.tiff"
"**/*.tif"
"**/*.cr2"
"**/*.xcf"

// Binary files - programs
"**/*.class"
"**/*.exe"
"**/*.dll"
"**/*.so"

// Checksum files
"**/*.md5"
"**/*.sha1"

// Binary files - archives
"**/*.jar"
"**/*.zip"
"**/*.rar"
"**/*.tar"
"**/*.tar.gz"
"**/*.tar.bz2"
"**/*.gz"

// Binary files - documents
"**/*.xls"

// ServiceLoader files
"**/META-INF/services/**"

// Markdown files
"**/*.md"

// Office documents
"**/*.xls"
"**/*.doc"
"**/*.odt"
"**/*.ods"
"**/*.pdf"

// Travis
"**/.travis.yml"

// Flash
"**/*.swf"

// Json files
"**/*.json"

// Fonts
"**/*.svg"
"**/*.eot"
"**/*.ttf"
"**/*.woff"

// Office documents
"**/*.xlsx"
"**/*.docx"
"**/*.ppt"
"**/*.pptx"
    
// Others
"**/*.dat"
"**/*.lck"
"**/*.log"
"**/*.ctrl"
"**/*.providers"
"**/*.factories"
"**/*.properties"
"**/META-INF/**"
".factorypath"
".gitattributes"
"mvnw"
"mvnw.cmd"
"ICLA"
"KEYS"
"NOTICE"
"LICENSE"
```



## 关于作者

- 邮箱：tangxbai@hotmail.com
- 掘金： https://juejin.im/user/5da5621ce51d4524f007f35f
- 简书： https://www.jianshu.com/u/e62f4302c51f
- Issuse：https://github.com/tangxbai/viiyue-release-snapshot/issues