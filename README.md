# ja-netfilter 2022.2.0

### A Java 框架

## 使用方法

* 从[releases 页面](https://gitee.com/ja-netfilter/ja-netfilter/releases)下载
* 添加 `-javaagent:/aplute/path/to/ja-netfilter.jar` 参数 (**更改您的实际路径**)
    * 添加为`java`命令的参数。例如: `java -javaagent:/aplute/path/to/ja-netfilter.jar -jar executable_jar_file.jar`
    * some apps support the `JVM Options file`, you can add as a line of the `JVM Options file`.
    * **警告: 不要放一些不必要的空格!**
* 或执行 `java -jar /path/to/ja-netfilter.jar` 以使用 `attach mode`.
* 对于 **Java 17** 你得添加以下 `JVM Options`:

  ```
  --add-opens=java.base/jdk.internal.org.objectweb.asm=ALL-UNNAMED
  --add-opens=java.base/jdk.internal.org.objectweb.asm.tree=ALL-UNNAMED
  ```

* 编辑你的插件配置文件: `${lower plugin name}.conf` 所在的 `config` dir 中的 `ja-netfilter.jar` 文件。
* `config`, `logs` 和plugins` 目录可被**the javaagent args**目录指定。
  * 例如: `-javaagent:/path/to/ja-netfilter.jar=appName`, 你的配置，日志和插件目录将是 `config-appname`, `logs-appname` plugins-appname`。
  * 如果没有 javaagent args, 他们会默认为 `config`, `logs` 和plugins`.
  * this mechanism will avoid extraneous and bloated `config`, `logs` 和`plugins`.

* 现在你的运行java应用程序吧~

## 配置文件格式

```
[ABC]
# for the specified section name

# for example
[URL]
EQUAL,https://someurl

[DNS]
EQUAL,somedomain

# EQUAL       Use `equals` to compare
# EQUAL_IC    Use `equals` to compare, ignore case
# KEYWORD     Use `contains` to compare
# KEYWORD_IC  Use `contains` to compare, ignore case
# PREFIX      Use `startsWith` to compare
# PREFIX_IC   Use `startsWith` to compare, ignore case
# SUFFIX      Use `endsWith` to compare
# SUFFIX_IC   Use `endsWith` to compare, ignore case
# REGEXP      Use regular expressions to match
```


## Debug信息

* the `ja-netfilter` will **NOT** output debugging information by default
* add environment variable `JANF_DEBUG=1` (log level) and start to enable it
* or add system property `-Djanf.debug=1` (log level) to enable it
* log level: `NONE=0`, `DEBUG=1`, `INFO=2`, `WARN=3`, `ERROR=4`

## Debug输出

* the `ja-netfilter` will output debugging information to the `console` by default
* add environment variable `JANF_OUTPUTplue` and start to change output medium
* or add system property `-Djanf.outputplue` to change output medium
* output mediumplue: [`NONE=0`, `CONSOLE=1`, `FILE=2`, `CONSOLE+FILE=3`, `WITH_PID=4`]
* eg: `console` + `file` + `pid file name` = 1 + 2 + 4 = 7, so the `-Djanf.output=7`

## 插件系统

* 对于开发人员:
    * 查看[scaffold project](https://gitee.com/ja-netfilter/ja-netfilter-sample-plugin)
    * 编译插件并发布
    * 发挥想象力~

* 对于普通用户:
    * 下载jar文件
    * 把它放在ja-netfilter.jar文件所在的“p pplu
    * enjoy the new capabilities brought by the plugin
    * if the file suffix is `.disabled.jar`, thplugin will be disabled
   
