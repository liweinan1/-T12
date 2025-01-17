# 极简数控T12

&emsp;&emsp;本项目开发了一套以**国产单片机STC8G1K08A**为核心的数显电烙铁，**支持快速更换烙铁芯，支持PD快充协议进行供电，支持多按键控制，适配三种显示模块，具有自动休眠功能**。在保证实现所有功能的前提下，尽量的控制了成本，全套零件材料成本可以控制在30元以下，其中主控芯片stc8g1k08a售价不足1元，二手T12烙铁芯甚至可以在3元左右买到，如果能够进一步优化并量产，成本还可以有所降低！  

&emsp;&emsp;本项目会提供以下文件，以便于自行购买材料组装：**硬件原理图，PCB打板文件，bom清单，系统固件**。上述文件将存放于project文件夹中，同时在本文档中会提供全套硬件的组装与调试方法。  

## 提供一个简单的测试视频如下:
[![Watch the video](https://github.com/liweinan1/simple_t12/blob/main/videos/%E8%A7%86%E9%A2%91%E5%B0%81%E9%9D%A2.jpg)](https://github.com/liweinan1/simple_t12/blob/main/videos/%E6%B5%8B%E8%AF%95%E8%A7%86%E9%A2%91.mp4)
<!-- https://github.com/liweinan1/simple_t12/blob/main/pictures/%E6%B5%8B%E8%AF%95%E8%A7%86%E9%A2%91.mp4 -->
由于github显示图片和视频不太方便，**将三种显示模块的测试视频上传到了哔哩哔哩：**[bilibili链接](https://space.bilibili.com/284525970/channel/seriesdetail?sid=2531601)

## 主要零件集合图
<div align=center>
<img src="https://github.com/liweinan1/simple_t12/blob/main/pictures/%E5%85%A8%E5%A5%97%E6%95%A3%E4%BB%B6.jpg" width="700">
</div>

## 原理图  
<div align=center>
<img src="https://github.com/liweinan1/simple_t12/blob/main/pictures/%E6%95%B0%E6%8E%A7T12%E5%BC%80%E6%BA%90%E5%8E%9F%E7%90%86%E5%9B%BE.png" width="700" >
</div>

## PCB图  
<div align=center>
<img src="https://github.com/liweinan1/simple_t12/blob/main/pictures/3D%E8%A7%86%E5%9B%BE.png" width="700">
</div>

## 极简数控T12安装与调试指导
### 1.主板与按键板焊接  
结合PCB板上的**丝印**或project文件夹下的**ibom文件**焊接主控板和按键板上的贴片元件。 
<div align=center>
<img src="https://github.com/liweinan1/simple_t12/blob/main/pictures/%E4%B8%BB%E6%8E%A7%E6%9D%BF.jpg" width="500">
</div>  

按键板最下方的的黑色小按键用于切换屏幕显示方向，不建议焊接，在需要切换方向时用镊子短接左右两个触点2秒左右即可。  
<div align=center>
<img src="https://github.com/liweinan1/simple_t12/blob/main/pictures/%E6%8C%89%E9%94%AE%E6%9D%BF%E7%84%8A%E6%8E%A5.jpg" width="300">
</div>

### 2.烙铁芯限位焊接  
将两个小圆环焊接到主控板上，务必使其居中，否则可能影响后面烙铁芯的正常插拔。另外上下两面都要用锡固定， 避免操作不当损坏！
<div align=center>
<img src="https://github.com/liweinan1/simple_t12/blob/main/pictures/%E5%9C%86%E7%8E%AF%E7%84%8A%E6%8E%A5.jpg" width="700">
</div>  

### 3.固件烧录
使用stc-isp软件，加载文件夹下提供的**simple_t12.hex文件**下载到主控板即可。  
<div align=center>
<img src="https://github.com/liweinan1/simple_t12/blob/main/pictures/stc-isp.jpg" width="700">
</div>  
具体连线方式参考下图，使用USB_to_ttl下载器，其中VCC与GND分别连接下载器的5V和GND，由于单片机的串口下载引脚被用作IIC引脚驱动屏幕，所以PCB中将TX与RX引脚分别命名为SDA与SCL，因此这里使用PCB上的SCL连接下载器的TXD，SDA连接下载器的RXD即可。
<div align=center>
<img src="https://github.com/liweinan1/simple_t12/blob/main/pictures/%E7%A8%8B%E5%BA%8F%E7%83%A7%E5%BD%95%E6%8E%A5%E7%BA%BF.png" width="350">
</div>  

### 4.屏幕焊接与测试
将屏幕插入到主控板的FPC接口上，通电测试屏幕是否成功点亮，第一次开机温度**显示-1℃**，若屏幕无法正常点亮，检查78L05的输入输出电压，判断是否供电正常，正常输出电压为5V左右。若无输出电压，请检查typec接口、FS312芯片是否有虚焊或连锡短路的情况。  
<div align=center>
<img src="https://github.com/liweinan1/simple_t12/blob/main/pictures/%E5%B1%8F%E5%B9%95%E6%B5%8B%E8%AF%95.jpg" width="700">
</div>  

### 5.限位排针焊接  
将按键板焊接到主控板上，务必使二者紧密接触，减小触点间的间隙，正反两面的焊盘都要焊接，使其固定的比较牢固，避免出现后续安装时掉焊盘的情况。  
<div align=center>
<img src="https://github.com/liweinan1/simple_t12/blob/main/pictures/%E6%8E%92%E9%92%88%E7%84%8A%E6%8E%A5.jpg" width="300">
</div>  

### 6.按键板组装  
将按键板焊接到主控板上，务必使二者紧密接触，减小触点间的间隙，正反两面的焊盘都要焊接，使其固定的比较牢固，避免出现后续安装时掉焊盘的情况。 
<div align=center>
<img src="https://github.com/liweinan1/simple_t12/blob/main/pictures/%E6%8C%89%E9%94%AE%E6%9D%BF%E7%BB%84%E8%A3%85.jpg" width="300">
</div>  


### 7.烙铁芯弹片焊接  
将烙铁芯插入主控板，将弹片焊接到主控板上，因个人焊接水平差异，可能需要调整弹片角度，使其既能夹紧烙铁芯，又不会使烙铁芯插拔困难。  
<div align=center>
<img src="https://github.com/liweinan1/simple_t12/blob/main/pictures/%E7%84%8A%E6%8E%A5%E5%BC%B9%E7%89%87.jpg" width="700">
</div>  

### 8.功能测试  
再次通电测试烙铁芯发热是否正常，若不发热，请检查P-MOS的第一个引脚是否有24V的电压，若无电压则检查焊接；若烙铁芯存在持续加热烧红的情况，不要慌张，断电后拔下烙铁芯，检查三极管电路及LM358运放电路是否有虚焊或者连锡，排除故障后再次测试；若以上工作正常，检查按键功能是否正常，若存在某个按键持续触发的情况，则检查是否连锡，若某个按键无法触发则检查是否虚焊。  
<div align=center>
<img src="https://github.com/liweinan1/simple_t12/blob/main/pictures/%E5%8A%A0%E7%83%AD%E6%95%85%E9%9A%9C.jpg" width="500">
</div>  

### 9.外壳安装
将主控板插入清理干净的透明外壳中（外壳会有切割后的碎屑，可以用烙铁芯加纸巾进行清理），为了结构的稳定，主控孔板和外壳的间隙很小，PCB边沿处会在外壳上留下痕迹，所以不要反复插拔，如果一定要插拔，可以沿着上次插拔时留下的痕迹插入，避免在外壳上留下过多的划痕，影响美观。  
<div align=center>
<img src="https://github.com/liweinan1/simple_t12/blob/main/pictures/%E5%A4%96%E5%A3%B3%E5%AE%89%E8%A3%85.jpg" width="700">
</div>  

### 10.安装完成  
将顶部挡板安装到外壳顶部，使其紧密配合，排针的角度注意调整，否则可能造成所有外壳损坏。  
<div align=center>
<img src="https://github.com/liweinan1/simple_t12/blob/main/pictures/%E6%9C%80%E7%BB%88%E6%88%90%E5%93%81.jpg" width="700">
</div>  

### 11.注意事项  
因为在结构设计上依靠摩擦力连接前后挡板，所以反复拆装时可能会造成外壳破裂等问题，务必注意。此外，若用户认为配合不够紧密，可以自行探索使用胶水等放方法进行加固！
特别注意：如果因为各种原因需要将主控板拔出，务必不要直接将力施加在按键或者圆环形的档板上面，可以先用钳子或其他工具将type-c那一头的PCB向下推出一节，在捏住按键板那一头的主控板两侧支架拔出！















<!-- markdown使用语法：  
一、标题写法：  
第一种方法：  
1、在文本下面加上 等于号 = ，那么上方的文本就变成了大标题。等于号的个数无限制，但一定要大于0个哦。  
2、在文本下面加上 下划线 - ，那么上方的文本就变成了中标题，同样的 下划线个数无限制。  
3、要想输入=号，上面有文本而不让其转化为大标题，则需要在两者之间加一个空行。  
另一种方法：等级表示法，分为六个等级，显示的文本大小依次减小。不同等级之间是以井号  #  的个数来标识的。一级标题有一个 #，二级标题有两个# ，以此类推。  
例如：

大标题
=
中标题
_

# 一级标题  
## 二级标题  
### 三级标题  
#### 四级标题  
##### 五级标题  
###### 六级标题 

二、编辑基本语法  
1、字体格式强调
 我们可以使用下面的方式给我们的文本添加强调的效果
*强调*  (示例：斜体)  
 _强调_  (示例：斜体)  
**加重强调**  (示例：粗体)  
 __加重强调__ (示例：粗体)  
***特别强调*** (示例：粗斜体)  
___特别强调___  (示例：粗斜体)  
2、代码  
`<hello world>`  
3、代码块高亮  
```
@Override
protected void onDestroy() {
    EventBus.getDefault().unregister(this);
    super.onDestroy();
}
```  
4、表格 （建议在表格前空一行，否则可能影响表格无法显示）
 
 表头  | 表头  | 表头
 ---- | ----- | ------  
 单元格内容  | 单元格内容 | 单元格内容 
 单元格内容  | 单元格内容 | 单元格内容  
 
5、其他引用
图片  
![图片名称](https://www.baidu.com/img/bd_logo1.png)  
链接  
[链接名称](https://www.baidu.com/)    
6、列表 
1. 项目1  
2. 项目2  
3. 项目3  
   * 项目1 （一个*号会显示为一个黑点，注意: 有空格，否则直接显示为*项目1） 
   * 项目2   
 
7、换行（建议直接在前一行后面补两个空格）
直接回车不能换行，  
可以在上一行文本后面补两个空格，  
这样下一行的文本就换行了。
或者就是在两行文本直接加一个空行。 
也能实现换行效果，不过这个行间距有点大。   
 
8、引用
> 第一行引用文字  
> 第二行引用文字
    
9、视频插入  
[![Watch the video](封面.png)](视频地址)  
--> 
