# RIME

在 Windows 环境下，RIME 输入法的中文名是「小狼毫」。

（在 Mac、Linux 平台上的名字都不一样，也许，是为了大家搜索不同平台下的定制方法的时候，能够不被其他平台不一样的设置方法所干扰，如果真是这样，那这开发团队实在是太厉害了，是怎么想出这样的方法？）

（从前经历过一个反例，图形化制作编程语言 Processing，由于名字的本身就是常规的英文 processing，即「程序」的意思，如果没有一定的搜索技巧，那么在 G 搜索引擎里面搜索到的内容，会有很多不相干的普通内容……）





## 目录

- 好处
- 困难
- 定制化参考





## 好处

### 最大的好处

> 本地运行

因为是本地运行的程序，没有通常意义上的云端记录，所以：

- 没有个人内容的云端记录
- 但，也没有丰富的云词库等可以使用

当认识到，输入法存在「隐私安全」和「方便输入」两个方面的矛盾，后面就看自己更加看重哪个了。我选择了前者。在搜索了相关介绍、自己的亲身使用体验，不那么信任流行的几个输入法；即使他们没有像网络上说的那样随意分析输入信息的数据，也不放心把对自己来说很重要的个人信息放在大公司的云端上。诱惑在面前，切身相关的自己也很多时候会意志投降，摆在毫无瓜葛的他人面前，他人/公司会保证多大的克制就需要好好琢磨一下了。



### 其他的好处

和第一个好处比起来，其他的好处就无足轻重了。

但，慢慢地发现，多方面的可定制化一点点调整好，就是输入的一把利器，秒杀之前用过的所有输入法，再也回不去了。

比如「按键功能任意设置」、「自定义短语」、「代码自建个性化输入功能」……





## 困难

困难也是上述好处所带来的，毕竟有好就有坏，有权利就有义务，世界上所有美好的事情都是经过汗水和努力才能够被少数人获得的，不是么？不可能每个人都是百万富翁。



### 时间积累

这个输入法是完全本地的状态、**没有联网**进行词库的联想，所以，刚开始上手，第一眼会觉得这个输入法很愚蠢、有上个世纪「智能ABC」输入法展现出来的表达匮乏，有非常强烈的冲动放弃它、回归到原来的大厂输入法怀抱中……

But 当自己慢慢花时间培养它，把自己的输入习惯跟他「说」一遍，那么，后面就会越来越顺手。

注意，从另外一个角度说，它又是那么**聪明**，只要你跟它说过一遍，它就会记住你的个性化词语，即使是说错成奇怪的词语，它也会完完全全记住。（虽然也可以删除，但操作方法还是相对费劲的）。用过的其他输入法，印象中是需要输入多遍之后才可以固定到首位，这点就有些不明白了……个性化词汇对自己来说肯定是更加重要的，不然就用一般的词表了嘛。

随着时间的推移，你会感觉 ta 越来越懂你，就好像是你手指头上的探针，每次都知道你想要什么文字，就像恋爱的感觉，时间越久，互相越理解，彼此更加难以割舍。



### 代码能力

需要代码的基础理解、调整能力，才能把这个输入法调整到符合自己个人习惯的状态。

But 不需要完全从头搭建代码，网络上可以搜索到很多个性化的代码内容，所以，只需要根据自己的需求对分享出来的代码进行自己的调整即可。

调整需要用到的整体代码框架的理解：

- 补丁 patch。原始的代码文件不进行改动，在 custom 类的文件进行打补丁，从而达到个别功能的个性化定制
- 关联引用。功能的代码是一个文件，进行代码的搭建；配置文件的补丁位置，对前面的代码进行引用，从而达到打补丁的效果
- 词库码表。词库码表是相对独立的第三种文件，可以进行自己的个性化名词的创建。



### 词库问题

因为没有云端这个概念，所以没有云端的词库可以使用，需要自己进行一次手动的创建，创建完毕之后，只需要良好的备份习惯不丢失，以后就会很方便。





## 定制化参考

大部分的基础修改，比如排列方式、样式、输入方案等等，基本都可以比较方便所搜到。

但其实**最好的**方法，还是直接照着 [官方给的文档](https://github.com/rime/home/wiki/CustomizationGuide) ，搜索自己需要的关键字，然后按照步骤、复制代码、理解之后作自己的修改，这样的步骤才是最快的。

PS：之前有一个忘记了具体内容的调整，按照搜索到的第三方分享教程，无论怎么配置都不成功，最后搜索回到官方文档，就成功了……原来是代码逻辑做了一点点升级调整，而网上搜索到的全部是失效版本的方法。



### 显示托盘图标

- 作用
  - 方便打开配置

- 步骤

  - 开始菜单栏里面，进入「用户文件夹」

  <img src="https://github.com/sxuya/windows-computer-literacy/blob/main/images/rime-1.jpg?raw=true" style="zoom:40%;" />

  - 打开「weasel.custom.yaml」文件，增加到如下内容，关键是第 12 行的内容：

  - ```yaml
    customization:  # 默认的
      distribution_code_name: Weasel
      distribution_version: 0.14.3
      generator: "Weasel::UIStyleSettings"
      modified_time: "Tue Sep 28 11:08:23 2021"
      rime_version: 1.5.3
    patch:
      "style/color_scheme": dark_temple # 选择的样式
      "style/font_point": 30  # 候选字大小
      "style/font_face": "方正兰亭刊黑简体" # 候选字字体，需要系统里面已经安装的字体；名字要和系统安装的字体名字一致
      # "style/horizontal": true # 候选字是横向排列还是竖向排列
      "style/display_tray_icon": true # 显示托盘图标
    ```

  - <img src="https://github.com/sxuya/windows-computer-literacy/blob/main/images/rime-2.png?raw=true" style="zoom:67%;" />

  - 开始菜单里面点击「重新部署」，变动才会生效。



### 生效定制化配置

每次定制化设置之后，需要手动点击「重新部署」才能生效。

因为我们第一步已经将图标放在了托盘区域，所以直接：托盘图标右键 - 「重新部署」，即可。

后续所有的定制化内容，修改完成后，**都需要**进行这一步操作。



### 更改简体字、样式等

- 组合按键 ```Ctrl + ` ``` 打开方案选择 - 方向键选择输入方案 - enter 键进入子菜单 - 更改「简体繁体」、「全角半角」等
- 托盘图标右键 - 「输入法设定」 - 选择合适方案 - 点击「中」 - 进入子菜单栏 - 选择合适样式主题 - 点击「中」



### 安装新方案

因为一些好奇心，我现在使用的输入方案不是大部分使用的全拼，而是「双拼」（好比有人使用的输入方案是「五笔」）。因此，我需要额外添加默认方案里面没有的双拼方案。

- 不成功方法
  - 托盘图标右键 - 「输入法设定」 - 「获取更多输入方案」 - 进入命令行交互界面 - 输入需要的方案名字，以双拼为例 - ```double-pinyin``` 
  - 但不知什么原因，搭上梯子，也是下载不成功的提示
- 成功方法
  - 在 [这个地址](https://github.com/rime/rime-double-pinyin) 以 zip 包下载 - 拖入到上述的命令行交互界面 - 即可
  - 然后在：托盘右键 - 「输入法设定」 - 勾选目标方案 - 即可
  - 以后也可以使用 ```Ctrl +` ``` 进行输入方案更换



### 自定义短语

将自己常用的短语进行预设，可以大大提高自己的输入速度、准确性，我对以下内容进行录入：

- 经常重复输入的文字
- 邮箱地址
- 邮寄地址
- 工作用到的格式模板
- ……

配置方法：

- 托盘图标右键 - 「用户文件夹」

- 以 UTF-8 格式新建「custom_phrase.txt」

- 以「希望得到的目标输入内容 + tab 的缩进符号 + 输入的触发字符 + tab 的缩进字符 + 第几个展示的数字」进行每一行的编写

- 比如：```∴	soyi	1``` ，当我输入「soyi」，就会有「∴」的候选字出现在列表里面，如下图

- <img src="https://github.com/sxuya/windows-computer-literacy/blob/main/images/rime-3.png?raw=true" style="zoom:50%;" />

- 新建输入方案的配置文件的 custom 个性化补丁文件。（比如，我的输入方案的配置文件是```double_pinyin_flypy.schema.yaml```，那么就新建一个```double_pinyin_flypy.custom.yaml```）

- 编写如下内容

- ```yaml
  patch:
    engine/translators:
      - punct_translator
      - reverse_lookup_translator
      - script_translator
      - table_translator@custom_phrase # 增加这句
      - table_translator
      - lua_translator@time_translator
    custom_phrase:
      dictionary: ""
      user_dict: custom_phrase
      db_class: stabledb
      enable_completion: false
      enable_sentence: false
      initial_quality: 1
  ```

- 重新部署



### 代码实现功能

以快速输入当前时间为例：

- 参考资料：[参考内容1](https://tieba.baidu.com/p/1923873073#) 、[参考内容2](https://www.zhihu.com/question/268770492) 。

- 托盘图标右键 - 「用户文件夹」

- 新建文件 ```rime.lua```

- 编辑如下内容进行保存：

- ```lua
  function time_translator(input, seg)
     if (input == "rq" or input == "sj") then
        local cand = Candidate("date", seg.start, seg._end, os.date("%Y年%m月%d日 %H:%M:%S"), "")
        cand.quality = 1
        yield(cand)
     end
     if (input == "rq" or input == "sj") then
        local cand = Candidate("date", seg.start, seg._end, os.date("%H:%M:%S"), "")
        cand.quality = 2
        yield(cand)
     end
     if (input == "rq" or input == "sj") then
        local cand = Candidate("date", seg.start, seg._end, os.date("%Y-%m-%d"), "")
        cand.quality = 3
        yield(cand)
     end
     if (input == "rq" or input == "sj") then
        local cand = Candidate("date", seg.start, seg._end, os.date("%Y/%m/%d"), "")
        cand.quality = 4
        yield(cand)
     end
     if (input == "rq" or input == "sj") then
        local cand = Candidate("date", seg.start, seg._end, os.date("%Y/%m/%d %H:%M:%S"), "")
        cand.quality = 5
        yield(cand)
     end
     if (input == "rq" or input == "sj") then
        local cand = Candidate("date", seg.start, seg._end, os.date("%Y年%m月%d日"), "")
        cand.quality = 6
        yield(cand)
     end
  end
  ```

- 同上一个「自定义短语」里面的 custom 文件，增加如下一句调用代码：

- ```yaml
  patch:
    engine/translators:
      - punct_translator
      - reverse_lookup_translator
      - script_translator
      - table_translator@custom_phrase
      - table_translator
      - lua_translator@time_translator # 这一句，函数名字要对应
    custom_phrase:
      dictionary: ""
      user_dict: custom_phrase
      db_class: stabledb
      enable_completion: false
      enable_sentence: false
      initial_quality: 1
  ```

- 重新部署

- 当输入「sj」或「rq」就会有多种日期格式作为候选词出现 ，效果如下：

- <img src="https://github.com/sxuya/windows-computer-literacy/blob/main/images/rime-4.png?raw=true" style="zoom:40%;" />



### 词库扩充

目前还没有这方面太多的需求，只是以「自定义短语」和「自学习」两个功能进行词库的积累，其他的基本内容（比如成语等）也集成在输入法本身里面。

如有需要，可以自行检索。（貌似需要使用一个转化器进行编译转化）。



写了好几天，就先这样。

2021年11月22日 11:44:29

