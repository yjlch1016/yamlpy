# yamlpy  
yamlpy接口测试框架  
yamlpy即为yaml文件+pytest单元测试框架的缩写  
可看作是一个脚手架工具  
可快速生成项目的各个目录与文件  
只需维护一份或者多份yaml文件即可  

# 安装  
pip install yamlpy  

# 查看参数信息  
yamlpy -h（或yamlpy --help）  

# 查看版本号  
yamlpy -v（或yamlpy --v）  

# 安装最新版  
pip install -U yamlpy  

# 创建项目  
yamlpy --p=项目名称  
例如在某个路径下执行命令：  
yamlpy --p=demo_project  

# 卸载  
pip uninstall yamlpy  

# 运行    
pytest+--cmd=环境缩写  
pytest --cmd=dev  
pytest --cmd=test  
pytest --cmd=pre  
pytest --cmd=formal  
