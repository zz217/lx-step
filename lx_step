# -*- coding: utf8 -*-
import requests
import hashlib
import json
import time
import random

def md5(code):
    res=hashlib.md5()
    res.update(code.encode("utf8"))
    return res.hexdigest()

def get_information(mobile,password):
    header = {
        'Content-Type': 'application/json; charset=utf-8',
        "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/85.0.4183.121 Safari/537.36"
    }
    url="http://sports.lifesense.com/sessions_service/login?systemType=2&version=4.6.7"
    datas = {
        "appType":6,
        "clientId":md5("5454"),
        "loginName":str(mobile),
        "password":md5(str(password)),
        "roleType":0
        }
    response =requests.post(url,headers=header,data=json.dumps(datas))
    return response.text

def update_step(step,information):
    step =int(step)
    url="http://sports.lifesense.com/sport_service/sport/sport/uploadMobileStepV2?version=4.5&systemType=2"
    accessToken=json.loads(information)["data"]["accessToken"]
    userId=json.loads(information)["data"]["userId"]
    #print(accessToken)
    #print(userId)
    #获取当前时间和日期
    timeStamp=time.time()
    localTime = time.localtime(timeStamp) 
    strTime = time.strftime("%Y-%m-%d %H:%M:%S", localTime) 
    print(strTime)
    measureTime=strTime+","+str(int(timeStamp))

    header = {
    'Cookie': 'accessToken='+accessToken,
    'Content-Type': 'application/json; charset=utf-8',
    "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/85.0.4183.121 Safari/537.36"
    }
    sport_datas = {
        "list": [
            {
                "DataSource":2,
                "active":1,
                "calories":str(int(step/4)),
                "dataSource":2,
                "deviceId":"M_NULL",
                "distance":str(int(step/3)),
                "exerciseTime":0,
                "isUpload":0,
                "measurementTime":measureTime,
                "priority":0,
                "step": str(step),
                "type":2,
                "updated":str(int(time.time()*1000)),
                "userId":str(userId)
                }]
                }
    result=requests.post(url,headers=header,data=json.dumps(sport_datas))
    return result.text
def execute_walk(phone,password,step):
    information=get_information(phone,password)
    update_result=update_step(step,information)
    result=json.loads(update_result)["msg"]
    print("刷新步数成功！此次刷取"+str(step)+"步。")if result=="成功" else print("刷新步数失败！")    

def main():
    if phone and password and step != '':
        execute_walk(phone, password, step)
    else:
        print("参数不全,请指定参数。或者在调用中直接指定参数")

# -- 配置--
# ------------------------------
phone = '' # 登陆账号
password = '' # 密码
step = random.randint(30000,40000)# 随机30000-40000步数
# ------------------------------

def main_handler(event, context):
    return main()

if __name__ == '__main__':
    main()
