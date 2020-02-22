# yamlpy  
接口测试框架  


# 一、思路         
1、采用requests+PyMySQL+demjson+loguru+PyYAML+ruamel.yaml+pytest+pytest-html+allure-pytest+pytest-assume+pytest-rerunfailures+pytest-sugar+pytest-timeout  
2、requests是发起HTTP请求的第三方库    
3、PyMySQL是连接MySQL的第三方库   
4、demjson是解析json的第三方库  
5、loguru是记录日志的第三方库  
6、PyYAML与ruamel.yaml是读写yaml文件的第三方库  
7、pytest是单元测试的第三方库  
8、pytest-html是生成html测试报告的插件  
9、allure-pytest是生成allure测试报告的插件  
10、pytest-assume是多重断言的插件  
11、pytest-rerunfailures是失败重跑的插件   
12、pytest-sugar是显示进度的插件  
13、pytest-timeout是设置超时时间的插件  


# 二、目录结构    
1、case是测试用例包              
2、log是日志目录         
3、report是测试报告的目录       
4、resource是yaml文件的目录      
5、setting是工程的配置文件包            
6、tool是常用方法的封装包         


# 三、yaml文件说明  
1、字段（命名和格式不可修改，顺序可以修改）  
case_name: 用例名称  
mysql: MySQL语句，列表格式，顺序不可修改  
mysql[0]  
mysql[1]  
mysql[2]  
第一行为增删改语句，第二行为查语句，第三行为查语句（数据库双重断言）  
第一行是发起请求之前的动作，没有返回结果  
第二行是发起请求之前的动作，有返回结果，是为了动态传参  
第三行是发起请求之后的动作，有返回结果，但是不可用于动态传参，是为了断言实际的响应结果  
当不需要增删改查和双重断言时，三行都为空  
当只需要增删改时，第一行为增删改语句，第二行为空，第三行为空  
当只需要查时，第一行为空，第二行为查语句，第三行为空  
当只需要双重断言时，第一行为空，第二行为空，第三行为查语句  
request_mode: 请求方式  
api: 接口路径  
data: 请求体，缩进字典格式或者json格式     
headers: 请求头，缩进字典格式或者json格式    
query_string: 请求参数，缩进字典格式或者json格式    
expected_code: 预期的响应代码    
expected_result: 预期的响应结果，缩进字典格式或者json格式  
regular: 正则，缩进字典格式  
>>variable:变量名，-列表格式  
>>expression:表达式，-列表格式  

2、参数化  
正则表达式提取的结果用${变量名}匹配，一条用例里面可以有多个    
MySQL查询语句返回的结果，即第二行mysql[1]  
用{__SQL0}、{__SQL1}、{__SQL2}、{__SQL3}。。。。。。匹配，一条用例里面可以有多个   
随机数字用{__RN位数}，一条用例里面可以有多个   
随机英文字母用{__RL位数}，一条用例里面可以有多个  
以上4种类型在一条用例里面可以混合使用  
${变量名}的作用域是全局的，其它3种的作用域仅限该条用例  


# 四、运行  
在工程的根目录下执行命令  
pytest+--cmd=环境缩写  
pytest --cmd=dev  
pytest --cmd=test  
pytest --cmd=pre  
pytest --cmd=formal  
