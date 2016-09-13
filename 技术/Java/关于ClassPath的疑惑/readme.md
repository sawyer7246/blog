#0914
最近极忙。一来黄金交易所的项目到UAT其他开发要么去别的项目组，要么去日本玩，留下来的bug都是一个人兜着，焦头烂额。
再加上新项目要自己深入了解很多新技术
	ssl，MQ，jboss
以前都没接触过，光搭个jboss集成Mybatis，SpringMVC就折腾了很久，结果今天想把log4j换成logback也花了将近半天时间，晚上回家才实验通。
深感自己技术不全面，十分的惶恐。

#关于classpath的疑问、
	classpath这个概念一致就没太搞明白。第一，什么是classpath？第二，Web工程中classpath怎么设置，路径到底是什么？
	第一个问题，对于刚开始学习java的人一定很熟悉，因为安装jdk时候就需要配置classpath。
	所以简而言之，设置Classpath的目的，在于告诉Java执行环境，在哪些目录下可以找到您所要执行的Java程序所需要的类或者包。
	对于web工程来说，配置web.xml时，需要配置各种文件路径，比如Spring的ApplicationContext.xml还有logback的xml，这些东西可以用classpath来定位，比如：classpath：***.xml。一般classpath目录就是web-inf/class。
	而今天的问题是maven在build时候，并没有把我配置logback.xml打进classpath下，经过各种尝试，发现还是不行（无头苍蝇），最后百度了下关键词，发现maven在打包时候会默认把main下的resources中的文件打到classpath下，所以就解决。
#关于MAVEN编译的xml文件在classpath的问题
	问题：maven打包时如何把包下面的XML配置文件也包含
	方法一：pom.xml文件配置：如果配置文件放在src/main/resources目录下，maven默认会把这个文件夹下的文件复制到classes目录下，如果你不死放在默认目录下，你可以手动指定Resources目录和输出目录。配置如下：
	<build>
		<sourceDirectory>src/</sourceDirectory>
		<outputDirectory>build/</outputDirectory>
	</build>
	方法二：把配置文件打包到其他人员目录：可以使用org.apache.maven.plugins插件。

#关于logback的配置
	网上得方法大部分都是可行的，不同得是有的人用了logback.ext中的listener，有的是自己写的。晚上试了下，写文件也成功了。Good。

#关于jboss配置
	这个坑得慢慢填。。。