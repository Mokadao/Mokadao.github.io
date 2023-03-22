
## 工具

### [[🥝StableDiffusion]]

### Midjourney 
- 原来是Discord开发的，直接在discord频道用

### NovelAI 二次元
资料
- NovelAI 本地部署配置教程（附优化） AI画二次元美少女|･ω･｀) - 范滇东的文章 - 知乎 https://zhuanlan.zhihu.com/p/571731191
- 二次元AI作画网站NovelAI使用教程 - 靠谱的赳晨的文章 - 知乎 https://zhuanlan.zhihu.com/p/571196055
- AI发展感觉对绘圈冲击太大了怎么办? - moerabpit的回答 - 知乎 https://www.zhihu.com/question/557600073/answer/2706431565
- [AI绘画 【Stable Diffusion】 NovelAI 整合包 解压即用_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1aN4y1A7j1/?spm_id_from=333.999.0.0&vd_source=453933dd6891757733da4e4288779255)

### Waifu2 在线放大低像素图片
[waifu2x (udp.jp)](http://waifu2x.udp.jp/)



## 文件类型
.ckpt  .pt .safetesors


## 模型种类

checkpoint trained 训练模型
checkpoint merge 融合模型
lora
- dreambooth训练画风模型
Textual Inversion

vae


## Prompt Tag语法

加权`{{1girl}}`

大括号{}，增加{}内的tag优先权重，可以{}套{}，默认所有tag优先度为1，{}优先度为1.05

减权 `[[1girl]]`

括号内部的TAG数量以及嵌套没有限制，非常基本但有必要说一下，将tag复制几份也可以起到加权的效果，权重越大的tag，生成时就越容易出现该元素。

### 基础语法

#### 分隔
分隔：不同的关键词tag之间，需要使用英文逗号,分隔，逗号前后有空格或者换行是不碍事的
ex：1girl,loli,long hair,low twintails（1个女孩，loli，长发，低双马尾）

#### 混合
混合：WebUi 使用 | 分隔多个关键词，实现混合多个要素，注意混合是同等比例混合，同时混。  
ex: 1girl,red|blue hair, long hair（1个女孩，红色与蓝色头发混合，长发）

#### 增强&减弱
有两种写法

第一种 (提示词:权重数值)：数值从0.1~100，默认状态是1,低于1就是减弱，大于1就是加强
ex: ,(loli:1.21),(one girl:1.21),(cat ears:1.1),(flower hairpin:0.9)

第二种 (((提示词)))，每套一层()括号增强1.1倍,每套一层[]减弱1.1倍。也就是套两层是1.1*1.1=1.21倍，套三层是1.331倍，套4层是1.4641倍。

ex: ((loli)),((one girl)),(cat ears),[flower hairpin]和第一种写法等价

所以还是建议使用第一种方式，因为清晰而准确。

#### 渐变
比较简单的理解时，先按某种关键词生成，然后再此基础上向某个方向变化。  

[关键词1:关键词2:数字]，数字大于1理解为第X步前为关键词1，第X步后变成关键词2，数字小于1理解为总步数的百分之X前为关键词1，之后变成关键词2

    ex：a girl with very long [white:yellow:16] hair 等价为
    开始 a girl with very long white hair
    16步之后a girl with very long yellow hair
    ex：a girl with very long [white:yellow:0.5] hair 等价为
    开始 a girl with very long white hair
    50%步之后a girl with very long yellow hair

#### 交替

`[cow|horse] in a field`比如这就是个牛马的混合物，如果你写的更长比如`[cow|horse|cat|dog] in a field`就是先朝着像牛努力，再朝着像马努力，再向着猫努力，再向着狗努力，再向着马努力

### 书写要点

- 关键词控制在75(100)以内。
- 越关键的词，越往前放。
- 相似的同类，放在一起。
- 只写必要的关键词。

### 书写顺序

- 画质词>>这个一般比较固定，无非是，杰作，最高画质，分辨率超级大之类的

- 风格词艺术风格词>>比如是照片还是插画还是动画

- 图片的主题>>比如这个画的主体是一个女孩，还是一只猫，是儿童还是萝莉还是少女，是猫娘还是犬娘还是福瑞，是白领还是学生

- 他们的外表>>  
	- 注意整体和细节都是从上到下描述，比如  
	- 发型（呆毛，耳后有头发，盖住眼睛的刘海，低双马尾，大波浪卷发），  
	- 发色（顶发金色，末端挑染彩色），  
	- 衣服（长裙，蕾丝边，低胸，半透明，内穿蓝色胸罩，蓝色内裤，半长袖，过膝袜，室内鞋），  
	- 头部（猫耳,红色眼睛），  
	- 颈部（项链），  
	- 手臂（露肩），  
	- 胸部（贫乳），  
	- 腹部（可看到肚脐），  
	- 屁股（骆驼耻），  
	- 腿部（长腿），  
	- 脚步（裸足）

- 他们的情绪>>  表述表情

- 他们的姿势>>  
	- 基础动作（站，坐，跑，走，蹲，趴，跪），  
	- 头动作（歪头，仰头，低头），  
	- 手动作（手在拢头发，放在胸前 ，举手），  
	- 腰动作（弯腰，跨坐，鸭子坐，鞠躬），  
	- 腿动作（交叉站，二郎腿，M形开腿，盘腿，跪坐），  
	- 复合动作（战斗姿态，JOJO立，背对背站，脱衣服）

- 图片的背景>>  室内，室外，树林，沙滩，星空下，太阳下，天气如何

- 杂项>>  比如NSFW，眼睛描绘详细

- 举例：

    (masterpiece:1.331), best quality,
    illustration,
    (1girl),
    (deep pink hair:1.331), (wavy hair:1.21),(disheveled hair:1.331), messy hair, long bangs, hairs between eyes,(white hair:1.331), multicolored hair,(white bloomers:1.46),(open clothes),
    beautiful detailed eyes,purple|red eyes),
    expressionless,
    sitting,
    dark background, moonlight, ,flower_petals,city,full_moon,

### 反向提示词 Negative prompt

用文字描述你不想在图像中出现的东西

AI大致做法就是
1. 对图片进行去噪处理，使其看起来更像你的提示词。
2. 对图片进行去噪处理，使其看起来更像你的反向提示词（无条件条件）。
3. 观察这两者之间的差异，并利用它来产生一组对噪声图片的改变
4. 尝试将最终结果移向前者而远离后者
5. 一个相对比较通用的负面提示词设置

    lowres,bad anatomy,bad hands,text,error,missing fingers,
    extra digit,fewer digits,cropped,worst quality,
    low quality,normal quality,jpeg artifacts,signature,
    watermark,username,blurry,missing arms,long neck,
    Humpbacked,missing limb,too many fingers,
    mutated,poorly drawn,out of frame,bad hands,
    owres,unclear eyes,poorly drawn,cloned face,bad face