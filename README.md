> https://blog.csdn.net/qq_37248504/article/details/109085445
# 文档说明


## 1 结构说明：

├─ common.py 存储全局变量  
├─ autoGUI.py 开始函数  
├─ trail 训练文件夹  
├─ operation 图像文字操作文件夹  
&emsp;&emsp;└─ assertOperation 判断操作  
&emsp;&emsp;└─ imgOperation  图像操作  
&emsp;&emsp;└─ textOperation 文字操作  
&emsp;&emsp;└─ mapOperation 地图操作  
├─ components 存放各组件文件夹  
&emsp;&emsp;└─ componentsName.xlsx 记录存放截图的信息  
&emsp;&emsp;└─ 2K 存放2K屏幕截图文件夹  
&emsp;&emsp;└─ 1080 存放1920X1080屏幕截图文件夹  
&emsp;&emsp;└─ component 存放python/java组件文件夹  
&emsp;&emsp;&emsp;&emsp;└─ supermap-iobjectspy-11.1.1 python的包  
&emsp;&emsp;&emsp;&emsp;└─ supermap-iobjectsjava-11.1.1-win64-all-Bin java包的bin文件夹  
├─ readme.md 说明文件

## 2 依赖说明
> pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple  换国内源清华大学
>
> pip install jpype1
python		3.7  
pytest      6.1.1
numpy		1.21.6  
Pillow		9.5.0  
PyAutoGUI	0.9.54  
PyGetWindow	0.0.9  
airtest		1.3.2  
opencv-python	4.8.1.78  
tesserocr		2.6.2  
pip		20.1.1     23.3.2  
pandas		1.3.5  
cnocr		2.2.3.2  
cnstd		1.2.3.5  
paddocr		2.6.0.0  
paddlepaddle	2.5.2  
iobjectspy		10.2.0  
Jpype1      1.5.0      

## 3 技术选型
- Selenium：用于自动化网页测试，可以通过模拟浏览器来实现自动化测试。【舍弃】
- UIAutomation:曾经的王者，如今被WinAppDriver和UIA3代替（Inspect->Accessibility Insights）【舍弃】：iDesktopx封装原生，无法识别按钮名称定位有问题
- Airtest：网易自主研发无代码自动测试器，适合做手机测试和简单的点击测试。舍弃不适合变动对比度的idesktopX【舍弃】
- Appium for Desktop： Appium2.2(npm install -g appium)+ opencv4  
  node版本需要18以上，node -v :https://nodejs.cn/download/   配置环境变量  
  npm版本需要10以上,npm-v:npm cache clean -f清除缓存    npm install -g n -f
  管理员身份运行PowerShell:npm i --location=global appium    启动：appium正常  
  安装驱动：appium driver install uiautomator2  
  pip install Appium-Python-Client  
  windows10的SDK环境：https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk/  
  主要负责安卓和Ios的测试，对windows的支持度较低，只能简单自动化【舍弃】
- Pywinauto：试用于Windows标准图形界面开发的软件，产品复杂且重写原生组件的不适用。【舍弃】
- AutoIt：不能对大型项目起作用，【舍弃】
- SikuliX：和airTEst一样，还差一些【舍弃】

- tensorflow+Keras: 图像识别训练ai：舍弃，训练ai基本用于识别，匹配度较低，需要多做研究【待定】  
  pip install --upgrade pip  3.8以上才能使用tensorflow2.11  
  pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple  
  pip config set global.index-url https://mirrors.aliyun.com/pypi/simple/  
  pip config set global.index-url https://pypi.org/simple  
  pip install --upgrade tensorflow  
  修复pip: easy_install pip  
  python -m pip install "tensorflow<2.11" #windows必须小于2.11  
  python -m pip install "pyopencv <20.1.1"
- PyAutoGUI： pyqt-pyqtgraph+PyAutoGUI+opencv+cnocr+Pywinauto，模板匹配和文字匹配【采用】

#### 图像识别：
2K文件夹、1080文件夹、componentsName表格

#### 文字识别：
- （1）tessoract识别  
components->tesseract-ocr-w64-setup-v5.3.0.20221214.exe识别文字的OCR安装包
环境配置（源码更改: tesseract_cmd = 'tesseract'-》tesseract_cmd = r'E:\zhangpl\pypro\OCR\tesseract.exe'） (OCR安装路径为E:\zhangpl\pypro\OCR\)
- （2）cnocr识别  
  ocr = CnOcr(det_model_name='ch_PP-OCRv3_det', rec_model_name='ch_PP-OCRv3', det_more_configs={'use_angle_clf': False})
> components->densenet_lite_136-fc-onnx.zip 文字的识别模型  
  移入文件夹->C:\Users\admin\AppData\Roaming\cnocr\2.2\  
> components->ch_PP-OCRv3_det_infer-onnx.zip 中文的检测模型  
  移入文件夹->C:\Users\admin\AppData\Roaming\cnstd\1.2\  
> components->ch_PP-OCRv3_rec_infer-onnx.zip 中文的识别模型  
  移入文件夹->C:\Users\admin\AppData\Roaming\cnocr\2.2\  

- （3）paddle识别(选用)  
python3 -m pip install paddlepaddle -i https://mirror.baidu.com/pypi/simple
pip install "paddleocr>=2.0.1" # 推荐使用2.0.1+版本

#### 地图功能：
supermap-iobjectspy-11.1.1 python使用组件的包  
supermap-iobjectsjava-11.1.1-win64-all-Bin java使用组件的bin包


***
#### [1] supermap-iobjectspy-11.1.1配置
> https://iobjectspy.supermap.io/html_zh/install.html

1. 命令行进入含有setup.py的文件夹中输入以下命令
2. 下载安装iobjectspy  
```python setup.py install ```
3. 控制台输入```python```进入python窗口
4. python窗口输入以下配置(输入路径需要双斜杠转义)  
```import iobjectspy```
```iobjectspy.set_iobjects_java_path('E:\zhangpl\pypro\pythonProject\components\component\supermap-iobjectsjava-11.1.1-win64-all-Bin\Bin')```
5. 输入结果如下，表示配置成功  
```copy com.supermap.analyst.addressmatching.jar, OK```  
```copy com.supermap.analyst.navigation.jar, OK```  
```copy com.supermap.analyst.networkanalyst.jar, OK```  
```copy com.supermap.analyst.spatialanalyst.jar, OK```  
```copy com.supermap.analyst.spatialstatistics.jar, OK```

#### [2] supermap使用
> https://blog.csdn.net/nan620403/article/details/133859809  



***