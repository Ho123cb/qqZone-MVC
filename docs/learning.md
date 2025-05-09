## Errors:

### 1.为什么`Artifacts`中没有显示`lib`内容呢？

因为你先配置`Artifacts`，后进行导入`lib`，所以没有配置成功。

解决方案：

1. 手动配置相关`jar`进行

   在项目配置文件中点击`Artifacts`，创建一个`lib`文件夹，再导入相关`jar`包即可

2. 删除配置好的`Artifacts`以及`lib`，重新按照顺序配置即可

2.兼容错误`Can not set`

>java.lang.IllegalArgumentException: Can not set java.util.Date field com.atguigu.qqzone.pojo.Topic.topicDate to java.time.LocalDateTime
>	at 

**JDBC 4.2 之后**，如果你的数据库列是 `DATETIME/TIMESTAMP`，
标准驱动(尤其是新版 MySQL / MariaDB) 会直接把它映射成 `java.time.LocalDateTime`。
而你的实体 `Topic` 里仍旧用的是 “老时代” 的 `java.util.Date`。
于是，一旦走到 `field.set()` 就崩。

解决方案：

1. 把实体字段改成 `java.time.LocalDateTime`（简单有效）
2. 获取通过反射，将其进行二次反转（抽象）
