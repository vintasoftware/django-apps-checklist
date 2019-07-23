## 1. 概念
  * [ ] 检查你的应用以遵循 [Unix 哲学](https://zh.wikipedia.org/wiki/Unix%E5%93%B2%E5%AD%A6): "让程序只做好一件事"
  * [ ] 检查你的应用是否可以被一句话描述，参考:
    * [django-taggit](https://github.com/alex/django-taggit): django-taggit 一个基于 Django 的易用打标签方案
    * [django-js-reverse](https://github.com/ierror/django-js-reverse): 针对 Django 的 Javascript 链接处理应用
    * [django-impersonate](https://bitbucket.org/petersanchez/django-impersonate): 一个用于使超级用户可以"冒充"其他普通用户的应用
  * [ ] 检查你的应用描述是否介绍多个功能，如果是的话，请将其拆解为多个应用

## 2. 易于安装
  * [ ] 添加 [许可证](https://choosealicense.com/) 文件
  * [ ] [在 PyPI 上发布：](https://packaging.python.org/distributing/)
    * [ ] 检查命名冲突以避免像 [django-filter](https://pypi.python.org/pypi/django-filter) 和 [django-filters.](https://pypi.python.org/pypi/django-filters) 的问题
    * [ ] 使用 [Wheels.](https://packaging.python.org/distributing/#wheels)
  * [ ] 在 [Django Packages.](https://djangopackages.org/) 上发布
  * [ ] 自动安装依赖库:
    * [ ] 在 setup.py 文件中的 `install_requires` 添加依赖
    * [ ] 不要在 `install_requires` 中添加 Django
    * [ ] 不要在 `install_requires` 中使用 `==` 限制版本，请使用 `>=`
  * [ ] 确认你需要一个 Django 应用还是一个常规的 Python 库:
    * Django 应用需要被添加至 `INSTALLED_APPS` 中，常规 Python 库不需用添加
    * 一些常规的 Python 库:  
      * [django-templated-email.](https://github.com/vintasoftware/django-templated-email)
      * [django-hashid-field.](https://github.com/nshafer/django-hashid-field)  
      * [django-downloadview.](https://github.com/benoitbryon/django-downloadview)  
  * [ ] 包含健全及设计良好的默认值:
    * [ ] 默认即可运行
    * [ ] 不要要求开发者复制粘贴代码片段
    * [ ] 默认不要做危险的操作，如，缓存
  * [ ] 危险操作需要被显式的定义:
    * 不要在未设置时默认显式全部，例如，`fields = None` 不代表所有 fields
  * [ ] 使用明确的 settings 以简化配置:
    * [ ] 为此应用的所有设置添加前缀，例如，`MYAPP_SETTING_KEY`
    * [ ] 将硬编码的内部参数替换为配置:
      * 例如，[django-avatar](http://django-avatar.readthedocs.io/en/latest/#AVATAR_MAX_SIZE) 中的 `AVATAR_MAX_SIZE` 可以被硬编码，但他被定义为单个配置
    * [ ] 如果开发者经常需要调整行为，也请在配置中调整
    * [ ] 如果开发者经常需要调整自定义类或函数，也请在配置中通过路径设置:
      * 例如，[django-taggit](https://django-taggit.readthedocs.io/en/latest/custom_tagging.html#using-a-custom-tag-string-parser) 在 settings 中设置自定义 tag 解析器
  * [ ] 请使用管道声明的方式设置工作流:
    * 请查看 [python-social-auth.](http://python-social-auth-docs.readthedocs.io/en/latest/configuration/django.html#personalized-configuration) 的实现
  * [ ] 提供默认 views，templates 和 URLs 以简化应用的集成
  * [ ] 提供友好的升级策略:
    * [ ] 删除前先弃用一段时间，抛出弃用警告，使用 Python 内建模块 [warnings](https://docs.python.org/3/library/warnings.html)
    * [ ] 不要改写旧的 migrations:
      * 用户已在他们的数据集上运行了你那旧的 migration 文件
    * [ ] [维护更新日志](http://keepachangelog.com/)
    * [ ] 遵循 [语义化版本控制](http://semver.org/)
  * [ ] 给参与者以鼓励，提供 [作者清单:](https://github.com/django/django/blob/master/AUTHORS)
    * 基于 git 历史记录，使用 [脚本](https://kev.inburke.com/kevin/easy-maintenance-of-your-authors-file/) 生成作者清单

## 3. 易于使用
  * [ ] 提供文档:
    * [ ] 先写文档
    * [ ] 提供自述文件
    * [ ] 提供快速入门教程，其中包含常见的使用案例
    * [ ] 区分高级和初级内容
    * [ ] 使用性别中立的人称代词
    * [ ] 部署在 [Read the Docs.](http://readthedocs.org/) 上
  * [ ] 提供测试:
    * [ ] 测试 [custom user model.](https://docs.djangoproject.com/en/dev/topics/auth/customizing/#specifying-a-custom-user-model)
    * [ ] 提供 [coverage.](http://coverage.readthedocs.io/en/latest/)
  * [ ] 提供持续集成:
    * [ ] 使用 [tox](https://tox.readthedocs.io/en/latest/) 在不同 Python 及 Django 版本下测试
      * 参考热门项目的 tox.ini 文件，例如，[django-filter](https://github.com/carltongibson/django-filter/blob/develop/tox.ini) 和 [django-taggit.](https://github.com/alex/django-taggit/blob/master/tox.ini) 
    * [ ] 遵循 PEP 8 规范，使用 [flake8.](https://gitlab.com/pycqa/flake8)
  * [ ] 提供样例工程:
    * 一些实现如下: 
      * [django-guardian.](https://github.com/django-guardian/django-guardian/tree/devel/example_project)
      * [django-haystack.](https://github.com/django-haystack/django-haystack/tree/master/example_project)
      * [django-avatar.](https://github.com/grantmcconnaughey/django-avatar/tree/master/test_proj)
  * [ ] 将应用以 Django 的抽象方式分成 [常用文件名](https://gist.github.com/fjsj/65ecfec09cfd2a684d53294d01677b9b) 像 views.py，forms.py，fields.py 等
  * [ ] 在 URLs 命名中遵循模式 `resource_action`，例如， `password_reset`， `product_detail`
  * [ ] 绝不依赖 Django 默认的用户模型，支持 [自定义用户模型:](https://docs.djangoproject.com/en/dev/topics/auth/customizing/#specifying-a-custom-user-model)
    * 参考 [django-registration.](http://django-registration.readthedocs.io/en/latest/custom-user.html) 的实现
  * [ ] 提供明确的用法:
    * 一些实现如下: 
      * [django-filter filtersets.](https://django-filter.readthedocs.io/en/develop/guide/usage.html#generating-filters-with-meta-fields)   
      * [django-import-export resources.](http://django-import-export.readthedocs.io/en/latest/getting_started.html#advanced-data-manipulation)
  * [ ] 不要隐式的绑定代码与名称或模块，提供注册机制:
    * 一些实现如下:
      * [django-contrib-comments moderator registry.](http://django-contrib-comments.readthedocs.io/en/latest/moderation.html#module-django_comments.moderation)  
      * [django-activity-stream registry.](http://django-activity-stream.readthedocs.io/en/latest/configuration.html)
  * [ ] 为开发者提供常用的管理命令:
    * 一些实现如下:
      * [django-reversion commands.](http://django-reversion.readthedocs.io/en/latest/commands.html)  
      * [django-haystack commands.](http://django-haystack.readthedocs.io/en/latest/tutorial.html)
  * [ ] 和主项目交互时，请使用 `_default_manager` 而不是 `objects`
  * [ ] Be Pythonic:
    * [ ] 使用生成器进行惰性求值
    * [ ] 使用上下文管理语句 `with` 处理未管理的资源
  * [ ] 预防错误:
    * [ ] 基于 [Django System check framework.](https://docs.djangoproject.com/en/dev/topics/checks/) 提供检查脚本
  * [ ] 快速失败:
    * [ ] 如果开发者写错配置文件，抛出 `ImproperlyConfigured` 异常:
      * 例如，当开发者忘记在 `FilterView` 中指定 `filterset_class` 或 `model` 时，[django-filter raises `ImproperlyConfigured`](https://github.com/carltongibson/django-filter/blob/0883cb6b25cd3bb2fa337fb9c54f0a3d2159f676/django_filters/views.py#L18-L28)
    * [ ] 当应用传入了不合法的参数时，抛出 `TypeError` 或 `ValueError`

- [ ] [国际化](https://docs.djangoproject.com/en/dev/topics/i18n/translation/) (I18N) 你的字符串

## 4. 易于集成
  * [ ] 保证集成的连续性:
    * [ ] 将类行为由不同方法实现
    * [ ] 拆解类行为至 mixins
    * [ ] 将业务函数或类中的逻辑拆解至帮助模块中
  * [ ] 使用 [`AppConfig`:](https://docs.djangoproject.com/en/dev/ref/applications/)
    * [ ] 确保扩展 AppConfig 时，应用不会出错
  * [ ] 提供默认模板:
    * [ ] 不要将他们直接放在 `templates/` 下，放在对应 `templates/app_name/` 下
    * [ ] 确保开发者自定义模板时，相同路径下的模板可以被覆盖
  * [ ] 提供模板标签去呈现复杂的数据:
    * [ ] 只在模板标签中保留展示逻辑，其他逻辑请移入帮助模块
      * 例如，django-avatar 有一个 `avatar` 模板标签用于生成 HTML `img` 标签，但是生成头像路径的逻辑 [独立于 `providers.py`.](https://github.com/grantmcconnaughey/django-avatar/blob/master/avatar/providers.py)
  * [ ] 提供默认的视图:
    * [ ] 不要破坏 class-based views 的可配置性，保持 Django views 的属性和方法可以被重载
    * [ ] 提取通用的 views 逻辑至 mixins
  * [ ] 尽可能避免使用内建的 models:
    * [ ] 如果必须使用，请提供一个 abstract model，并为你的应用提供对应的变种实现，一些实现如下:
      * [django-taggit custom tag model.](https://django-taggit.readthedocs.io/en/latest/custom_tagging.html#custom-tag)  
      * [django-blog-zinnia custom entry model.](http://docs.django-blog-zinnia.com/en/develop/how-to/extending_entry_model.html)  
      * [django-contrib-comments custom app.](https://django-contrib-comments.readthedocs.io/en/latest/custom.html)
  * [ ] 提取通用的 models 至 abstract models
  * [ ] 不要使用 model mixins，使用 abstract models:
    * 原因见 [StackOverflow answer.](http://stackoverflow.com/a/25817237/145349)
  * [ ] 通用外键应该可以被直接外键覆盖，一些实现如下:  
    * [django-guardian support of direct foreign keys.](http://django-guardian.readthedocs.io/en/latest/userguide/performance.html#direct-foreign-keys)  
    * [django-taggit support of custom through model.](https://django-taggit.readthedocs.io/en/latest/custom_tagging.html#custom-foreignkeys)
  * [ ] 隔离 form field 逻辑至 form fields 和 widgets:
    * 参考 [django-recaptcha.](https://github.com/praekelt/django-recaptcha)
  * [ ] 隔离 model field 逻辑至 model fields:
    * 参考 [django-hashid-field.](https://github.com/nshafer/django-hashid-field)
  * [ ] 隔离查询逻辑至 queryset，如，filter，update 和 delete
  * [ ] 隔离表级别逻辑至 managers，如，create
  * [ ] 隔离校验逻辑至 validators
  * [ ] 只把 context processors 用于全局逻辑
  * [ ] 只把 middlewares 用于涉及全局逻辑的请求-响应循环或当前用户
  * [ ] 使用 signals 以避免意大利面式代码

## 5. 维护
  * [ ] 坦率的对待 bugs，尤其是安全问题:
    * [ ] 在变更日志中加入安全警告，确保他们可以被 [safety](https://github.com/pyupio/safety) 解析
  * [ ] 不要废弃项目，可以捐给社区
