# 采用docker 搭建windows下python环境

* 使用基于此镜像的 https://github.com/cdrx/docker-pyinstaller的https://github.com/JackMcKew/pyinstaller-action-windows github action 打包成exe文件
* 基于此镜像改造entrypoint （pip download -d ～/packagesdir -r requirements.txt）进行依赖下载，便于在内网机器上安装
  * poetry add xxxx     (如无法下载 可以直接编辑pyproject.toml) 主要目的是生成requirements.txt
  * poetry export -f requirements.txt --output requirements.txt  --without-hashes
  * 内网机器执行：pip install --no-index --ignore-installed --find-links=deps -r requirements.txt

  