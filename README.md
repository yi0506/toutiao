# 说明

## 启动设置

### 开发模式

```shell
export FLASK_ENV=development
export TOUTIAO_WEB_SETTINGS=/path/to/config/file
```

### 线上模式

```shell
export FLASK_ENV=production
export TOUTIAO_WEB_SETTINGS=/path/to/config/file
export TOUTIAO_CELERY_SETTINGS=/path/to/config/file
```


### 代码结构
```
toutiao-backend
├── common                                  # 存放用户端、自媒体端、MIS端等应用的公共代码
│   ├── cache                                # 缓存层的实现代码
│   │   ├── __init__.py
│   ├── celery_tasks                        # celery的异步任务代码
│   │   ├── __init__.py
│   │   ├── main.py                            # celery的启动代码
│   │   └── sms                                # 发送短信的异步任务    
│   ├── models                                # 数据库ORM模型类相关
│   │   ├── init.sql                        # 数据库建标SQL语句
│   │   └── ....py                            # 模型类文件
│   ├── rpc                                    # gRPC接口代码文件
│   │   ├── __init__.py
│   │   ├── chatbot                            # 聊天机器人接口
│   │   └── recommend                        # 推荐系统接口
│   ├── settings                            # 工程默认配置代码
│   │   ├── __init__.py
│   │   ├── default.py
│   └── utils                                # 工具代码
│       ├── __init__.py
│       ├── constants.py                    # 工程常量
│       ├── converters.py                    # flask转换器
│       ├── decorators.py                    # 自定义装饰器
│       ├── dysms                            # 阿里大于短信库
│       ├── gt3                                # 极验验证码库
│       ├── jwt_util.py                        # JWT封装库
│       ├── limiter.py                        # flask限流扩展
│       ├── logging.py                        # 日志配置
│       ├── output.py                        # flask-restful输出格式定制
│       ├── parser.py                        # 自定义flask-restful RequstParser验证方法
│       ├── snowflake                        # 分布式ID雪花算法实现
│       └── storage.py                        # 七牛对象存储上传方法封装
├── docs                                    # 开发文档记录
├── im                                        # 即时通讯代码目录        
├── mis                                        # MIS后台接口代码目录
├── mp                                        # 自媒体平台接口代码目录
├── requirements.txt                        # 项目依赖包
├── schedule                                # 定时任务
├── scripts                                    # 脚本目录
└── toutiao                                    # 用户端接口代码目录
    ├── __init__.py                            # flask app工厂函数文件
    ├── main.py                                # 用户端后端启动文件
    └── resources                            # 视图目录
        ├── __init__.py            
        ├── news                            # 文章蓝图
        ├── notice                            # 系统公告蓝图
        ├── search                            # 搜索蓝图
        └── user                            # 用户蓝图
            ├── __init__.py                    # 蓝图初始化文件
            ├── constants.py                # 常量文件
            └── passport.py                    # 蓝图视图文件
```