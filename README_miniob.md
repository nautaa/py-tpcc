# 如何在 MiniOB 上运行该测试

## 准备环境
**安装 Python 2.x**
目前只支持 Python 2.7 或 Python 2.6，因此需要先安装 Python 2.x

**安装相关依赖**
需要安装 pymysql 0.9.3，例如在 centos 环境下，可以执行以下命令安装：
```
sudo pip2 install pymysql==0.9.3 --trusted-host pypi.python.org --trusted-host pypi.org --trusted-host files.pythonhosted.org
```

## 运行测试

1. 准备 config 文件，例如:
```
[miniob]

# The path to the unix socket
unix_socket          = /tmp/miniob.sock

```

2. 启动 MiniOB，例如：
```
./bin/observer -E lsm -t lsm -P mysql -s /tmp/miniob.sock -f ../etc/observer.ini
```

3. 运行 tpcc 测试，例如：
```
python ./tpcc.py --config=miniob.config  miniob  --debug --clients 4 --ddl ./tpcc-miniob.sql
```

注意：为了便于在资源受限的测试环境中运行 TPCC 测试，同时受限于 MiniOB 当前的性能，此版本简化了某些测试参数。