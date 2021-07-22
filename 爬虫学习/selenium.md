# 爬虫学习之selenium案例



## 1.selenimum介绍

> Selenium是一个Web的自动化测试工具，最初是为网站自动化测试而开发的，Selenium 可以直接调用浏览 器，它支持所有主流的浏览器（包括PhantomJS这些无界面的浏览器），可以接收指令，让浏览器自动加载页 面，获取需要的数据，甚至页面截屏等。我们可以使用selenium很容易完成编写的爬虫，接下来我们就来看一下selenium的运行效果

## 2.selenium使用

> 使用selenium之前需要配置好chromedriver以及安装好selenium模块，注意需要将chromedriver配置到环境变量中，否则需要在创建实例的时候指定driver的绝对路径作为executable_path参数

````python
from selenium import webdriver
# 如果driver没有添加到了环境变量，则需要将driver的绝对路径赋值给executable_path参数
# driver = webdriver.Chrome(executable_path='/home/worker/Desktop/driver/chromedriver') 
# 如果driver添加了环境变量则不需要设置executable_path driver = webdriver.Chrome() 
# 向一个url发起请求 		
driver.get("https://www.sixstaredu.com/") 
# 把网页保存为图片，69版本以上的谷歌浏览器将无法使用截图功能 
driver.save_screenshot("sixstar.png")
print(driver.title) # 打印页面的标题 

# 退出模拟浏览器 
driver.quit() # 不退出会有残留进程
```
````

## 2.代码实例

```python
import time
from selenium import webdriver
driver = webdriver.Chrome()

driver.get('https://mail.sina.com.cn/?from=mail')
time.sleep(1)
driver.find_element_by_id('freename').send_keys('账号')
time.sleep(1)
driver.find_element_by_class_name('password').send_keys('密码')
time.sleep(1)
# driver.find_element_by_class_name('loginBtn').click()

# 操作js进行点击 可以解决很多没有定位到指定位置的问题
# 必须获取元素
ele = driver.find_element_by_xpath('/html/body/div[3]/div/div[2]/div/div/div[4]/div[1]/div[1]/div[7]/div[1]/a[1]')
# 用js进行点击
driver.execute_script('arguments[0].click()',ele)
```



















