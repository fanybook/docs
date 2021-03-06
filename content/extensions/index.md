---
title: 插件技术文档
---

## 什么是插件

**插件** 是对 Notadd 主体 及 Notadd 模块 的功能扩展或增强。

## 目录结构

```
# extensions/vendor/ext-navigation                                                模块目录
    # resources                                                                资源目录
        # mixes                                                                前端资源目录
        # translations                                                         多语言资源目录
        # views                                                                视图目录
    # src                                                                      源码目录
        # Controllers                                                          控制器目录
        # Subscribers                                                          事件订阅者目录（支持自动发现）
        # Extension.php                                                        插件的服务提供者
    # composer.json                                                            Composer 配置文件
    # configuration.yaml                                                       模块配置文件
    # readme.md                                                                模块说明文件
```

### 资源目录

**资源目录**包含**前端资源文件**(**mixes**)、**多语言资源文件**(**translations**)和**视图文件**(**views**)。

### 源码目录

**源码目录**包含 PHP 源码。

### Composer 配置文件

**Composer 配置文件** (composer.json) 是符合 [Composer 官方规范](https://getcomposer.org/doc/04-schema.md) 的JSON格式的文档，Composer 相关规范，可以查阅 [Composer 官方文档](https://getcomposer.org)。

#### Type

将 **type** 设置为 **notadd-extension**，可以将当前模块包（Package）安装到 **extensions/vendor** 目录下，vendor 为厂商名称。

#### Require

实现 **type** 的重定向安装目录的特性，必须添加对包（Package）：[notadd/installers](https://packagist.org/packages/notadd/installers)的依赖，建议添加到 **require-dev** 下。

## 插件配置文件

**插件配置文件** (configuration.yaml) 除了包含插件基本信息配置外，还是 Notadd 插件功能注入的一部分，主要实现以下部分的注入：

```markdown
* csrf                                                                         # CSRF 例外
* dashboards                                                                   # 后台首页仪表盘模块
* menus                                                                        # 后台菜单
* pages                                                                        # 后台自定义页面
* publishes                                                                    # 资源发布
```

与模块共享配置文档规范，请参阅 [**配置文件规范文档**](../configurations/)。
