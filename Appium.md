# 
## 教程

###### excel数据行
![excel数据行](http://pr30yn96y.bkt.clouddn.com/Fk1KaA2XeyiSruL-zyaX41Sj-0UY)
******
  
  &emsp;这里我们的代码里面真正用到的列是定位方式、控件元素、操作方法和测试数据。定位方式  
  和空间元素是用来在app中定位到元素的数据，操作方法和测试数据则是对此元素所要进行的操作的
  数据，其中操作方法中的click、clear、text、get_attribute等方法都是无键盘操作，也就是说不
  需要测试数据，send_keys属于键盘操作方法，需要填我们希望的输入值来在app里真实的输入(**测试
  数据一栏在excel里的数据类型不要为数字**)  
  
  + click：模拟点击操作，就是说在app上如果需要我们点击才能实现的效果，那么我们就填click
  + clear：清除操作，一般用来清空输入框中的值
  + text：获取元素的文字信息，例如获取登录界面的登录按钮的文字信息就是“登录”
  + get_attribute：获取元素的属性
  + send_keys：模拟键盘输入操作，此方法需要我们填写希望向app输入的内容

### 实例：
###### app默认加载页
![avatar](http://pr30yn96y.bkt.clouddn.com/FhQuKdERbAcQ-zjw1DoddTAQNwu3?imageView2/2/w/360/h/520/q/100)

  &emsp;这是我们app加载后自动进入的页面，我们首先的操作就是找到图片中圈起来的“我的”按钮，并在excel里
  填入此元素的定位方式和元素标识，找到此元素后由于我们的期望是进入“我的”页面，既点击当前页面的“我的”
  按钮进入“我的”页面，所以我们要在excel的操作方法里填入click,是appium在找到此元素后模拟点击进入“我的”
  页面，因为click是无键盘操作，所以测试数据此栏不用填数据

###### 我的页面
![avatar](http://pr30yn96y.bkt.clouddn.com/Fo0ifs36ptJp9NVia_fOJUVt-9FZ?imageView2/2/w/360/h/520/q/100)

  &emsp;此时我们成功进入了我的页面，由于我们的下一步操作是进入登录界面，那么同上我们填入“登录注册”按钮
  的定位方式和元素标识，同样因为点击此按钮才会进入登录界面，操作方法栏填入click方法使代码模拟点击进入登录
  界面

###### 登录页面
![avatar](http://pr30yn96y.bkt.clouddn.com/FqWjBLFugKOHv7fTq3VB7VP5AzoZ?imageView2/2/w/360/h/520/q/100)

  &emsp;进入登录界面后，我们要先点击“手机号和密码登录”按钮才会切换到手机号密码登录，那么我们填入此按钮的
  定位方式和操作方法click，（先跳过选择渠道商这一步），之后我们找到“输入手机号”此元素，将其定位方式和元素
  标识填入到excel里，因为接下来要输入手机号，所以操作方法填send_keys，并在测试数据里填入我们用来测试的手机号
  ，填入密码步骤同填手机号，最后我们找到“登录”按钮并填入定位方式和元素标识以及操作方法click，当我们运行的
  时候我们的appium就会自动完成一个完整的才打开app到登陆操作  
  
### 代码工作流程：

+ 加载excel数据：    拿到我们在excel里填入的所有数据
+ 依次使用excel数据：把excel中的一整行数据作为一个整体使用
+ 查找元素：         根据我们填的定位方式和控件元素在当前页面查找元素
    ```
    element = find_element(driver, operation, location, element_ident)
    ```
+ 操作元素：         根据我们填的操作方法对查找到的元素做对应操作
    ```
        if operation == "send_keys":
            element.send_keys(data) # data是测试数据一栏中我们填的数据
        elif operation == "click":  # 模拟点击
            rs = element.click()
            print(rs)
        elif operation == "clear":  # 清除元素内的输入值
            element.clear()
        elif operation == "submit":  # 模拟按钮提交
            element.submit()
        elif operation == "text":   # 获取控件元素名称
            feedback = element.text
    ```
+ 写入结果：         通过后将PASS写入到excel中

#### 错误快速排查
> 元素未寻找到错误
>> 可首先查看我们填入的定位方式和控件元素标识是不是不正确或者带有空格  

>> 假如此元素和我们查找的上一个元素不在同一个页面，检查上一个元素我们是否填了操作方法，(一般是click点击跳转)  

>> 检查上一个元素的操作是否无法达到此元素的页面  

>> 在appium上按照excel步骤进行，查看appium能否拿到响应

> 不支持的操作类型
>> 操作方法不受支持或不存在