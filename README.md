### 数据库相关
遵循gorm的惯例, 表结构中默认包含下列字段, 列名由字段名称进行下划线分割来生成:

```
// gorm.Model 定义
type Model struct {
  ID        uint `gorm:"primary_key"`
  CreatedAt time.Time // 列名为 `created_at`
  UpdatedAt time.Time
  DeletedAt *time.Time 
}
```

**注意:**
 - 1 如果模型有DeletedAt字段，调用Delete删除该记录时，将会设置DeletedAt字段为当前时间，而不是直接将记录从数据库中删除
 - 2 如果模型有 CreatedAt字段，该字段的值将会是初次创建记录的时间
 - 3 如果模型有UpdatedAt字段，该字段的值将会是每次更新记录的时间。

### 接口鉴权
 - 每个接口需要附加一个query参数(token)
 - jwt 通过调用 [auth]() `base_url/auth`接口获得
 - jwt 有效期默认为 1h
 - 不建议使用该简单方式. 建议使用oauth2.0

### 日志(logrus)
 - 使用logrus,默认加载了App主日志实例,通过`log.App.Info/Warn...()`调用
 - 支持自定义其他日志实例,参考App实列定义即可

### 编码规范
[Uber Go 语言编码规范](https://github.com/xxjwxc/uber_go_guide_cn)
