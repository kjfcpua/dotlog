# DotLog
Simple and easy go log micro framework

## 1. Install

```
go get -u github.com/devfeel/dotlog
```

## 2. Getting Started
```go
func main() {
	dotlog.StartLogService("/home/log.conf")
	log1 := dotlog.GetLogger("FileLogger")
	log1.Info("example-normal test main")
}
```
log.conf
```
<?xml version="1.0" encoding="utf-8" ?>
<config>
  <!-- 日志组件全局配置 -->
  <global islog="True" innerlogpath="D:\gotmp\golog\logs\" innerlogencode="gb2312"/>

  <!-- 日志组件用户自定义变量 -->
  <variable>
    <var name="LogDir" value="D:\gotmp\golog\logs\"/>
    <var name="LogDateDir" value="D:\gotmp\golog\logs\{year}\{month}\{day}\"/>
    <var name="MailServer" value="smtp.xxxx.cn"/>
    <var name="ToMail" value="xxxx"/>
    <var name="MailAccount" value="xxx@xxx.cn"/>
    <var name="MailPassword" value="xxxx"/>
    <var name="SysName" value="Devfeel.DotLog"/>
  </variable>

  <!-- 日志组件日志记录媒体 -->
  <targets>
  </targets>

  <!-- 日志对象 -->
  <loggers>
    <logger name="ClassicsLogger" configmode="classics" layout="{DateTime} - {message}" />
    <logger name="FileLogger" configmode="file" layout="{DateTime} - {message}" />
 </loggers>

</config>
```


## 3. Features
* 简单易用，100%配置化
* 支持文件、UDP、Http、EMail四种日志目标
* 支持自定义变量
* 文件支持单文件最大尺寸设置
* 更多待完善