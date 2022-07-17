# 极简数控T12
&emsp;&emsp;本项目开发了一套以国产STC单片机为核心的数显电烙铁，能够快速更换烙铁芯，支持PD快充协议进行供电，可以使用能够输出20v以上的手机充电器/充电宝进行供电(功率要求55w以上)，通过显示模块和按键进行人机交互，具有自动休眠功能。在保证实现所有功能的前提下，尽量的控制了成本，全套零件材料成本可以控制在30元以下，如果能够进一步优化并量产，成本还可以有所降低！  
&emsp;&emsp;本项目会提供以下文件，以便于自行购买材料组装：硬件原理图，PCB打板文件，bom清单，系统固件（源代码暂不开源）。上述文件将存放于project文件夹中，同时在本文档中会提供全套硬件的组装与调试方法。  
## 极简数控T12安装与调试指导
### 1.主板与按键板焊接  
结合PCB板上的丝印或project文件夹下的bom文件焊接主控板和按键板上的贴片元件。按键板最下方的的黑色小按键用于切换屏幕显示方向，不建议焊接，在需要切换方向时用镊子短接左右两个触点2秒左右即可。

![Image 主控板焊接](https://github.com/liweinan1/simple_t12/blob/main/pictures/%E4%B8%BB%E6%8E%A7%E6%9D%BF.jpg)
![Image 按键板焊接](https://github.com/liweinan1/simple_t12/blob/main/pictures/%E6%8C%89%E9%94%AE%E6%9D%BF.jpg)  
### 2.烙铁芯限位焊接  
2.	将两个小圆环焊接到主控板上，务必使其居中，否则可能影响后面烙铁芯的正常插拔。另外上下两面都要用锡固定， 避免操作不当损坏！

![Image ](https://github.com/liweinan1/simple_t12/blob/main/pictures/%E5%9C%86%E7%8E%AF%E7%84%8A%E6%8E%A5.jpg)  
### 3.固件烧录

### 4.屏幕焊接与测试
将屏幕插入到主控板的FPC接口上，通电测试屏幕是否成功点亮，第一次开机温度显示-1℃，若屏幕无法正常点亮，检查78L05的输入输出电压，判断是否供电正常，正常输出电压为5V左右。若无输出电压，请检查typec接口、FS312芯片是否有虚焊或连锡短路的情况。
![Image ](https://github.com/liweinan1/simple_t12/blob/main/pictures/%E5%B1%8F%E5%B9%95%E6%B5%8B%E8%AF%95.jpg)


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
> 第二行引用文字    -->
