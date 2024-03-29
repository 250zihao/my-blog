# myblog

🌍
_[English](/docs/README-en.md) ∙ [简体中文](README.md)_

## 主要功能：

- 文章，页面，分类目录，标签的添加，删除，编辑等。文章、评论及页面支持`Markdown`，支持代码高亮。
- 支持文章全文搜索。
- 完整的评论功能，包括发表回复评论，以及评论的邮件提醒，支持`Markdown`。
- 侧边栏功能，最新文章，最多阅读，标签云等。
- 支持 Oauth 登陆，现已有 Google,GitHub,facebook,微博,QQ 登录。
- 支持`Redis`缓存，支持缓存自动刷新。
- 简单的 SEO 功能，新建文章等会自动通知 Google 和百度。
- 集成了简单的图床功能。
- 集成`django-compressor`，自动压缩`css`，`js`。
- 网站异常邮件提醒，若有未捕捉到的异常会自动发送提醒邮件。
- 集成了微信公众号功能，现在可以使用微信公众号来管理你的 vps 了。

## 安装

mysql 客户端从`pymysql`修改成了`mysqlclient`，具体请参考 [pypi](https://pypi.org/project/mysqlclient/) 查看安装前的准备。

使用 pip 安装： `pip install -Ur requirements.txt`

如果你没有 pip，使用如下方式安装：

- OS X / Linux 电脑，终端下执行:

  ```
  curl http://peak.telecommunity.com/dist/ez_setup.py | python
  curl https://bootstrap.pypa.io/get-pip.py | python
  ```

- Windows 电脑：

  下载 http://peak.telecommunity.com/dist/ez_setup.py 和 https://raw.github.com/pypa/pip/master/contrib/get-pip.py 这两个文件，双击运行。

## 运行

修改`myblog/setting.py` 修改数据库配置，如下所示：

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'myblog',
        'USER': 'root',
        'PASSWORD': '1234',
        'HOST': 'host',
        'PORT': 3306,
    }
}
```

### 创建数据库

mysql 数据库中执行:

```sql
CREATE DATABASE `myblog` /*!40100 DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci */;
```

然后终端下执行:

```bash
python manage.py makemigrations
python manage.py migrate
```

### 创建超级用户

终端下执行:

```bash
python manage.py createsuperuser
```

### 创建测试数据

终端下执行:

```bash
python manage.py create_testdata
```

### 收集静态文件

终端下执行:

```bash
python manage.py collectstatic --noinput
python manage.py compress --force
```

### 开始运行：

执行： `python manage.py runserver`

浏览器打开: http://127.0.0.1:8000/ 就可以看到效果了。

本项目已经支持使用 docker 来部署，如果你有 docker 环境那么可以使用 docker 来部署，具体请参考:[docker 部署](/docs/docker.md)

## 更多配置:

[更多配置介绍](/docs/config.md)  
[集成 elasticsearch](/docs/es.md)
