# ClamAV Scanner Web & C++ Backend
## 项目简介
这是一个基于 C++ 后端 + Flutter Web 前端 的病毒扫描演示项目。
主要功能包括：

后端使用 C++ 与 ClamAV 交互，实现文件扫描。

前端使用 Flutter Web 提供简单的页面展示。

提供 基础 ping 功能，确保服务可用。

支持 对单个文件进行病毒/健康文件检测。

## 项目功能

### Ping 服务

检测后端服务是否在线。

用于前端快速确认服务状态。

### 单文件扫描

上传单个文件到后端进行病毒扫描。

支持对已知病毒文件或健康文件进行检测。

返回扫描结果（例如 OK 或 FOUND）。

## 环境要求

操作系统：Linux（推荐 Ubuntu 20.04+）

依赖软件：

Docker ≥ 20.x

Docker Compose ≥ 1.29

硬件要求（可选）：

CPU：2 核以上

内存：2GB+（ClamAV 扫描大文件时会占用内存）

## 项目结构
/Clamav/    
├─ clamav-demo.tar.xz/ 
│  ├─ web                  # web：Flutter构建的前端
│  │  ├─ web
│  │  ├─ nginx.conf
│  │  └─ Dockerfile
│  ├─ scanner              # scanner：C++逻辑
│  │  ├─ scanner_simple.pro.user
│  │  ├─ main.cpp                
│  │  ├─ request.h    
│  │  ├─ request.cpp 
│  │  ├─ httpserver.h  
│  │  ├─ httpserver.cpp  
│  │  ├─ clamclient.h  
│  │  ├─ clamclient.cpp   
│  │  └─ Dockerfile
│  ├─ docker-compose.yml   # 配置文件格式   
├─ README.md
└─ test_cases.xlsx

## 部署步骤

1. 克隆项目

git clone https://github.com/ivrdpkwn/Clamav.git

2. 解压并进入项目目录

tar -xJvf clamav-demo.tar.xz
cd clamav-demo

3. 检查配置文件

修改 docker-compose.yml 中的端口映射（如 web 服务 80:80）。

4. 启动服务

docker-compose up -d


5. 验证运行

打开浏览器访问 http://localhost:80 → Web UI

测试容器通信 Ping Server

测试扫描正常文件 Scan File（例如 scan/test1.txt）

测试扫描异常文件 Scan File（例如 scan/eicar.txt）


## 技术栈

后端：C++17、ClamAV、SQLite3、pthread

前端：Flutter Web

容器化：Docker、Nginx

## 注意事项

扫描单个文件功能仅用于演示，不适合生产环境大规模使用。

确保 ClamAV 数据库已更新，否则可能无法检测最新病毒。

压缩包内包含伪病毒文件用于测试。

完整测试用例请参见 docs/test_cases.xlsx。
