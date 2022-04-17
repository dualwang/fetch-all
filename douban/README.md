# QuickAdd 宏：获取豆瓣读书、电影、音乐等信息至Obsidian

使用QuickAdd的宏命令（Macro Choice）功能，实现豆瓣读书、电影、音乐等信息的搜索及获取。  
实现思路及部分代码来自[DoubanAllInOne](https://github.com/LumosLovegood/myScripts/tree/main/DoubanAllInOne)、豆瓣JS解密代码来自[Spider-Crack-JS](https://github.com/SergioJune/Spider-Crack-JS)，感谢以上作者。

## I. 功能说明
<img src="https://raw.githubusercontent.com/laowdev/fetch-all/master/douban/images/function-select.png" width="200px" />

### 功能1：搜索豆瓣内容并生成笔记  
输入关键字进行搜索
![](https://raw.githubusercontent.com/laowdev/fetch-all/master/douban/images/common-search-input.png)
选择搜索结果
![](https://raw.githubusercontent.com/laowdev/fetch-all/master/douban/images/search-result.png)
生成笔记
![](https://raw.githubusercontent.com/laowdev/fetch-all/master/douban/images/movie-note.png)

### 功能2：输入豆瓣链接并生成笔记  
直接输入豆瓣链接，然后生成笔记
![](https://raw.githubusercontent.com/laowdev/fetch-all/master/douban/images/url-import.png)

## II. 使用说明
### 0. 使用前：安装QuickAdd插件
进入Obsidian第三方插件商店，搜索并安装QuickAdd插件。  
![](https://raw.githubusercontent.com/laowdev/fetch-all/master/douban/images/plugin.png)
![](https://raw.githubusercontent.com/laowdev/fetch-all/master/douban/images/quickadd-plugin.png)

### 1. 导入模版文件、脚本文件
**模版文件**  
将下列模版文件导入Obsidian库中：  
BookTemplate.md  
MovieTemplate.md  
MusicTemplate.md  
模板文件一般放置在Obsidian设定的模版文件夹中。模版内容可以根据个人需要进行调整，可以精简条目，也可以配置的更美观更复杂。  

**脚本文件**  
将脚本文件fetch-douban.js导入Obsidian库中（库中的任意位置即可）。  
注意：Obsidian需要将“检测所有类型文件”的设置打开才能看到JS文件，但JS文件是否可见并不影响宏命令的配置。
### 2. 创建模版命令（Template Choice）
打开QuickAdd设置，选择Template类型，在输入框中输入以下命令名，点击Add Choice按钮创建模版命令  
CreateBookNote  
CreateMovieNote  
CreateMusicNote  
![](https://raw.githubusercontent.com/laowdev/fetch-all/master/douban/images/add-template-choice.png)
创建成功后，点击模版命令的设置按钮进行设置。  
除模版文件路径（Template Path）为必须设置项，其他的配置可以按需进行配置。  

下面是配置建议，仅供参考：  
笔记名格式（File Name Format）  
笔记所在文件夹（Create in folder）  
重命名之后自动累加（Increment file name）  
新建后自动打开笔记（Open）  
![](https://raw.githubusercontent.com/laowdev/fetch-all/master/douban/images/template-settings.png)

### 3. 创建宏命令（Macro Choice）
打开QuickAdd设置，点击Manage Macros按钮添加宏
![](https://raw.githubusercontent.com/laowdev/fetch-all/master/douban/images/add-macro.png)
宏创建成功后，点击Configure按钮，新增自定义脚本（User Scripts）fetch-douban.js
![](https://raw.githubusercontent.com/laowdev/fetch-all/master/douban/images/add-script.png)

回到QuickAdd设置页，选择Macro类型，在输入框中输入命令名（可自定义名称），点击Add Choice按钮创建宏命令
![](https://raw.githubusercontent.com/laowdev/fetch-all/master/douban/images/add-macro-choice.png)
点击宏命令的设置按钮，选择宏，并点亮闪电图标
![](https://raw.githubusercontent.com/laowdev/fetch-all/master/douban/images/macro-select.png)
![](https://raw.githubusercontent.com/laowdev/fetch-all/master/douban/images/complete.png)
### 4. 执行宏命令
打开Obsidian命令面板（MacOS快捷键：Command + P；Windows快捷键：Ctrl + P），选择刚刚创建的宏命令即可执行
![](https://raw.githubusercontent.com/laowdev/fetch-all/master/douban/images/command-douban.png)
如果命令无法生效，请重启Obsidian。

## III. 其他操作
### 修改模版命令的名称
一般不建议修改模版命令名称，使用默认即可。如果修改，则需要同步修改脚本的配置。
![](https://raw.githubusercontent.com/laowdev/fetch-all/master/douban/images/macro-settings.png)
![](https://raw.githubusercontent.com/laowdev/fetch-all/master/douban/images/script-settings.png)

## IV. 附1：字段说明
### 书籍
| 字段名称  | 字段说明 | 字段示例 |
| ------------ | -------- | -------- |
| title        | 书名     |   万历十五年（增订本）       |
|subtitle      |副标题|    |
| author       | 作者     |     [美] 黄仁宇     |
| translator  | 译者     |          |
| coverUrl     | 封面图   | https://img2.doubanio.com/view/subject/l/public/s3670063.jpg   |
| originalTitle | 原作名   |          |
| pageNum      | 页数     |   286       |
| publisher    | 出版社   |    中华书局      |
| intro        |   简介    |   《万历十五年》是一部改变中国人阅读方式的经典。。。 |
| isbn         | ISBN     |  9787101054491        |
| rating       | 评分     |      9.1    |
| ratingNum    | 评价人数 |    22562      |
| ratingDetail | 评分分布 | ["60.5%", "33.9%", "5.3%", "0.3%", "0.1%"]   |
| authorIntro  | 作者介绍 |黄仁宇（1918-2000），湖南长沙人，美籍历史学家。。。          |
| quote1       |  摘录1        |          |
| quote2       |      摘录2    |          |
| tags         | 标签     |          |
| relatedBooks | 相关书籍 |          |
| linkUrl         | 豆瓣链接 |https://book.douban.com/subject/1981042/  |
| publishDate  | 出版日期 |   2007-1       |
| catalog      | 目录     |          |
|series     |丛书|    |
|binding|装帧|  平装   |
|price|定价|  18.00元  |
|rank|豆瓣榜单|豆瓣热门历史图书TOP10 (No.9)|

### 电影
| 字段名称 | 字段说明  | 字段示例  |
| ------------ | ------------- | ------------------------------------- |
| title        | 片名          | 星际穿越                        |
| fullTitle    | 全名（包含原名） | 星际穿越 Interstellar       |
| director     | 导演          | 克里斯托弗·诺兰   |
|editor       |编辑          |乔纳森·诺兰 / 克里斯托弗·诺兰|
| coverUrl     | 封面图        | https://img1.doubanio.com/view/photo/s_ratio_poster/public/p2614988097.webp |
| summary      | 简介          | 近未来的地球黄沙遍野。。。               |
| genre        | 类型          | 剧情 / 科幻 / 冒险                      |
| rating       | 评分          | 9.4                             |
| ratingNum    | 评价人数      | 1558242                       |
| ratingDetail | 评价分布      | ["73.4%", "22.0%", "4.0%", "0.4%", "0.2%"] |
| releaseDate  | 上映日期      | 2014-11-12(中国大陆) / 2014-11-07(美国)          |
| language     | 语言          | 英语                               |
| imdbId       | IMDb          | tt0816692                                 |
| country      | 制片国家/地区 | 美国 / 英国 / 加拿大             |
| runningTime  | 片长          | 169分钟                        |
| starring     | 主演          | 马修·麦康纳 / 安妮·海瑟薇                     |
| award        | 获奖情况      | 第87届奥斯卡金像奖 最佳视觉效果               | 
| top250       | 豆瓣Top250    | No.11                                   |
| linkUrl      | 豆瓣链接      | https://movie.douban.com/subject/1889243    |
| episodeNum   | 集数    |    |

### 音乐
| 字段名称 | 字段说明 | 字段示例 |
| ------------ | ----------- | ------------------------------------------------------------ |
| title        | 歌名/专辑名 | 范特西                                                       |
| linkUrl      | 豆瓣链接    | https://music.douban.com/subject/1403307/                    |
| coverUrl     | 封面图      | https://img2.doubanio.com/view/subject/m/public/s3750422.jpg |
| musican      | 表演者      | 周杰伦                                                       |
| otherTitles  | 又名        | Fantasy                                                      |
| genre        | 流派        | 流行                                                         |
| albumType    | 专辑类型    | 专辑                                                         |
| medium       | 介质        | CD                                                           |
| releaseDate  | 发行时间    | 2001-09-14                                                   |
| publisher    | 出版者      | BMG                                                          |
| albumNum     | 唱片数      | 1                                                            |
| barCode      | 条形码      | 9787799602868                                                |
| isrc         | ISRC        | CNA260150200                                                 |
| rating       | 评分        | 9.2                                                          |
| ratingNum    | 评价人数    | 164193                                                       |
| ratingDetail | 评价分布    | ['76.3%', '20.1%', '3.3%', '0.1%', '0.2%']                   |
| summary      | 简介        | 周杰伦的出现，让人们相信台湾创造本土R&B的可能性。。。        |
| trackList    | 曲目        | 1. 爱在西元前。。。                                          | 

## V. 附2：相关地址
[Obsidian官网](https://obsidian.md/)  
[QuickAdd API](https://github.com/chhoumann/quickadd/blob/master/docs/QuickAddAPI.md)
