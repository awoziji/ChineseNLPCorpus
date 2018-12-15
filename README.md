# ChineseNLPcorpus
An collection of Chinese nlp corpus including basic Chinese syntactic wordset, semantic wordset, historic corpus and evaluate corpus. 中文自然语言处理的语料集合，包括语义词、领域共时、历时语料库、评测语料库等。本项目简单谈谈自己对语言资源的感想以及目前自己进行语言资源构建的现状。  

# 介绍 
&emsp;&emsp;语言资源，本身是一个宽泛的概念，即语言+资源，语言指的是资源的限定域，资源=资+源，是资料的来源或者汇总，加在一起，也就形成了这样一种界定：任何语言单位形成的集合，都可以称为语言资源。语言资源是自然语言处理任务中的一个必不可少的组成部分，一方面语言资源是相关语言处理任务的支撑，为语言处理任务提供先验知识进行辅助，另一方面，语言处理任务也为语言资源提出了需求，并能够对语言资源的搭建、扩充起到技术性的支持作用。因此，随着自然语言处理技术的不断发展，自然语言处理需求在各个领域的不断扩张、应用，相关语言资源的构建占据了越来越为重要的地位。作者硕士期间所在的研究机构为国家语言资源监测与研究平面媒体中心，深受导师所传授的语言资源观熏陶，并在实际的学习、工作过程中，动手实践，形成了自己的一些浅薄的语言资源认识，现在写出来，供大家一起讨论，主要介绍一些自己对语言资源的搜索，搭建过程中的一些心得以及自己目前在语言资源建设上的一些工作。  
# 语言资源的分类
&emsp;&emsp;介绍中说到，任何语言单位的集合都可以称为语言资源，比如我有一个个人的口头禅集合，这个就可以称为一个语言资源库，在你实际生活中进行言语活动时，你其实就在使用这个语言资源库。再比如说，一个班级中的学生名单，其实也可以当作是一种语言资源，这个语言资源在进行班级学生点名、考核的时候也大有帮助。当然，此处所讨论的语言资源是从自然语言处理应用的角度上出发的。总的来说，我把它归为以下两种类型：  
1、领域语料库  
&emsp;&emsp;领域语料库，是从语料的这个角度来讲的，这里的语料，界定成文本级别（以自然语句为基础级别形成的文本集合，即可以是句子、段落、篇章等）。领域语料库，可以根据不同的划分规则而形成不同的语料类别：  
&emsp;&emsp;1）根据所属领域，可以进一步细化成不同领域的语料库。包括金融领域语料、医药领域语料、教育领域语料、文学领域语料等等。  
&emsp;&emsp;2）根据所属目的，可以进一步细化为：评测语料（为自然语言处理技术pk而人工构造的一些评测语料，如ACE,MUC等国际评测中所出现的如semeval2014,snli等）；工具语料（指供自然语言处理技术提供资源支撑的语料）  
&emsp;&emsp;3）根据语料加工程度的不同，可进一步分为：熟语料（指在自然语言单位上添加人工的标签标注，如经过分词、词性标注、命名实体识别、依存句法标注形成的语料），生语料（指直接收集而未经加工形成的语言资源集，如常见的微博语料，新闻语料等）  
&emsp;&emsp;4）根据语料语种的不同，可进一步分为：单语语料和多语语料，多语语料指的是平行语料，常见于机器翻译任务中的双语对齐语料（汉-阿平行语料库，汉-英平行语料库）等。  
&emsp;&emsp;5）根据语料规模的不同，可以进一步分为：小型语料库，中型语料库，大型语料库。至于小型、中型、大型的界定，可根据实际领域语料的规模而动态调整  
2、领域词库  
&emsp;&emsp;领域词库，指以句级以下语言单位形成的语言资源库，这个层级的语言单位可以是笔画、偏旁部首、字、词、短语等。同样的，领域词库也可以进一步细分。  
&emsp;&emsp;1）领域特征词库。这里所说的领域特征词库，指的是与领域强相关，具有领域区别能力形成的词语集合，如体育领域中常见的“篮球”、“足球”等词，文学领域常见的“令狐冲”、“鲁迅”等词，又如敏感词库等，这些词常常可作为分类特征而存在。  
&emsp;&emsp;2）语法语义词库。语义词库的侧重点在与语言的语法层面和语义层面：  
&emsp;&emsp;a）语法词库：北大的语法信息词典，北大的实体概念词典、Hownet语义词典这三类词典，这几个语法词库，在对词的语法功能上都做了不同的工作，对词的内部结构信息进行了详细的标注，如北大的语法信息词典，以词类为划分标准讲汉语的常用词进行了划分，并对词性、搭配（前接成分和后接成分）进行了详细的标注；Hownet语义词典从义项的角度对词的义元进行了分解和注释。    
&emsp;&emsp;b）语义词库：这类语义词点，侧重点不在词语的内部语法结构，而在词语的整体语义上。这类词库，常见的词库有哈工大发布的同义词词林扩展版，这个词库将同义词按照语义的相近程度进行了不同层次的聚类，可以作为同义词扩展提供帮助。另一个是情感分析任务中常用的情感词典，这类词典主要公开的词典包括大连理工大学信息检索实验室公开的情感本体词库、hownet、香港中文大学、台湾清华大学公开的情感词库（具体包括情感词库、否定词库、强度词库）等。另外，工业界，有boson公开的微博情感词库（词的规模比较大，但标注信息不是很精准）。还有的，则是中文的反义词库等，这个可以参考我的github项目，里面对这些词库也有一些涉及。  
# 语言资源的搭建策略
&emsp;&emsp;语言资源的搭建，指的是语言资源的整个搭建过程。其实是要解决四个问题，一个是语言资源的收集问题；二是语言资源的融合标准化问题；三是语言资源的动态更新问题；四是语言资源的共享与联盟问题。下面就这四点展开阐述：  
&emsp;&emsp;1、语言资源收集的问题。上一节中说到的语言资源搜索策略中，讲述了语言资源搜索过程中的三步走策略，在这个步骤完成之后，会得到一系列的词库。这些词库可能初期不会特别完善，往往还需要人工使用启发式规则进行人工去噪的工作。  
&emsp;&emsp;2，语言资源的融合标准化问题。通过不同方式收集起来的语言资源，往往会存在一个格式不对称的问题，这有点像知识图谱中的知识融合问题。因此，为了解决这个问题，我们通常需要制定一个标准化的语言资源格式，例如，在构建情感词表的过程当中，有的情感词表没有强度标记，有的强度值范围不一样，有的情感词表的标记不一，这个时候往往需要标准化，给定一个标准化的样式，再将不同来源的情感词按照这个标记做相应的调整。我在实际的工作过程中，常常把这种问题类别成知识图谱构建过程中的schema搭建问题，信息抽取过程中的slot-definition问题。先把规范和标准搭好，再去统一标准化。  
&emsp;&emsp;3，语言资源的动态更新问题。知识和信息的价值，在很大程度上都在于它的一种实时性，语言资源作为一种常识性知识库，能够保证自身的一种与时俱进，将能够最大限度地发挥自身的价值。而从实践的角度上来说，语言资源的动态更新，可以靠人工去维持，去动态及时更新，也可以建立一种动态监测和更新机制，让机器自动地去更新。这类其实可以参考知识图谱更新的相关工作。  
&emsp;&emsp;4，语言资源的共享与联盟问题。语言资源是否共享，其实是一个与业务敏感以及开源意识想结合的一种决策，有的资源因为某种业务敏感或者开源意识不够open而无法共享，当然还有其他因素成分在，不过，语言资源最好是需要共享的，这样能够最大力度的发挥语言资源在各个领域的应用。语言资源的联盟问题，更像是对开源语言资源的一种链接与互联。这类问题是对当前的资源零散、碎片化问题的一个思考，前面也说到，目前情感分析的词表有很多个，语法和语义词库也有很多个，但每个人在构建时的出发点不同，构建者也分布在不同的高校或机构当中，这些资源虽然在个数上会有增长，但随着时间的推移，这种零散化的现象将会越来越严重。

# 语言资源的实践
   作者在学习和工作之余，根据语言资源搭建策略，构建起了语义词库、领域词库、领域语料库、评测语料库。种类约31种，具体如下：

# 语义知识库

|类型| 名称| 介绍|
|:--- | :--- | :--- |
|语义词库| 语法信息词典| 北大计算所研制，汉语词语的语法功能分类、词语的语法属性描述|
|语义词库| Hownet义原词典| 董振东老师研制，汉语词语义原分类|
|语义词库| 程度副词词典| 表示程度的词|
|语义词库| 现代汉语词典| 现代汉语词典, txt版本|
|语义词库| 否定词词典| 对意义进行反转的词典|
|语义词库| 同义词词林词典| 哈工大同义词词典|
|语义词库| 反义词词典| 反义词词表，1.5W对|
|语义词库| 同义词词典| 同义词词典，5.5W对|
|语义词库| schema概念词典| 互动百科概念体系，百度百科概念体系|
|语义词库| 停用词| 自然语言处理用停用词词表|

# 领域词库

|类型| 名称| 介绍|
|:--- | :--- | :--- |
|领域词库| 搜狗输入法领域词库| 超过1W个领域的搜狗输入法词库，txt版本|
|领域词库| 职位词典| 基于百万级拉钩JD网抽取形成的职位词典|
|领域词库| 敏感词词词库| 敏感词词库，包括政治、反动等词|

# 领域语料库

|类型| 名称| 介绍|
|:--- | :--- | :--- |
|领域语料库| 人民日报标注语料| 1998年人民日报分词语料库|
|领域语料库| 8k20类小说文本集合| 20个领域(武侠、恐怖等)小说文本集合，5000+小说文本,txt版本|
|领域语料库| 字幕网70W字幕文本语料| 基于字幕网字幕文件解析形成，70W字幕文本语料|
|领域语料库| 内涵段子50W等语料| 基于内涵段子采集，50W短文本|
|领域语料库| 歌词14W语料| 基于公开歌词网采集，14W首歌曲歌词|
|领域语料库| 人民日报历时语料库1946-2003| 基于公开国内新闻的人民日报采集，1946-2003，150W规模|
|领域语料库| 参考消息历时语料库1957-2002| 基于公开国际新闻的参考消息采集，1957-2002，50W规模|
|领域语料库| 腾讯滚动新闻历时语料库2009-2016| 腾讯历时滚动新闻(国内、国外、教育、财经、社会、体、科技、汽车、游戏、汽车等板块)|

# 评测语料库
|类型| 名称| 介绍|
|:--- | :--- | :--- |
|评测语料库| 问句匹配| 英文question相似问句6.5W对，中文微众银行问句集1000对|
|评测语料库| 中文命名实体识别| 中文电子病历命名实体识别|
|评测语料库| 情感分析| 斯坦福sentibank、中文酒店电影评论|
|评测语料库| 实体关系抽取| 中文人物关系数据集、英文ACE SEMEVAL2008评测数据集(NYT,NYTfilter)|
|评测语料库| 文本蕴含| 英文snli,multinli数据集116W，中文文本蕴含数据集100W|
|评测语料库| 音乐问句解析| 音乐问句解析数据集1.2W|
|评测语料库| 幽默计算| 中文幽默计算数据集(包括幽默类型识别、幽默等级识别、隐喻类型识别、隐喻等级分类)|
|评测语料库| 阅读理解| squad数据集|
|评测语料库| 知识图谱补全| 知识图谱链接数据集(FB15K, FB40K, Freebase, WN18,WordNet)|
|评测语料库| 中文实体链接| 基于中文百科知识的实体链接数据集1.3K|
|评测语料库| 中文自动问答| 中文智能问答数据集，两个任务(问句意图分类，航空、酒店、火车客服问答)|


# 总结 
1、本项目阐述了语言资源的相关感想，并给出了目前语言资源的构建现状，目前为止收集了四个大类共31哥小类的语言资源数据集。    
2、本项目中所涉及到的报告内容均来源于网上公开资源，对此免责声明。  
3、如果有需要用到以上作者收集到的这些语料库，可以联系作者获取。  
4、自然语言处理，是人工智能皇冠上的一颗明珠，懂语言者得天下，语言资源在自然语言处理中扮演着举足轻重的作用，懂语言资源者，分得天下。目前开放的网络环境，对语言资源的大繁荣提供了很大的契机。语言资源构建是一门学问，也是一种手段，现在自然语言处理技术也对语言资源的构建提供了技术上的支持，如何把握语言资源搜索策略，搭建策略，重点解决语言资源的动态更新、共享与联盟问题，将是语言资源建设未来需要解决的问题。  

如有自然语言处理、知识图谱、事理图谱、社会计算、语言资源建设等问题或合作，可联系我：    
1、我的github项目介绍：https://liuhuanyong.github.io  
2、我的csdn博客：https://blog.csdn.net/lhy2014  
3、about me:刘焕勇，中国科学院软件研究所，lhy_in_blcu@126.com 
