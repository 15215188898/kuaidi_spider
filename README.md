物流/快递流转信息爬取
===
# 环境说明 #
* Python3
* Requests

# 文件说明 #
* postid.txt: 待爬取物流信息的物流单号，一行一个物流单号
* main.py: 爬虫的主程序，可直接执行

# 参数说明 #
get_wuliu(Result_FileName, SleepTime)
* Result_FileName: 储存文件的名字，可自行修改，默认为“Result.txt”
* sleep_time: 每次爬取的停止间隔，越大越不容易被封，默认为“2”

# 实现原理 #
1. 使用快递100的接口查询物流信息，需要两个必备的参数
    1. 快递公司Code
    2. 快递单号
2. 通过快递100的请求信息可以获取到推荐的快递公司Code
    1. 默认使用第一个Code + 物流单号查询
    2. 如果返回结果为空，则使用第二个Code，直至用完所有推荐
3. 结果储存
    1. 写入标题
    2. 写入物流流转信息