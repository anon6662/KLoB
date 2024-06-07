# KLoB
Data for KLoB: a Benchmark for Assessing Knowledge Locating Methods in Language Models.

## Examples
### KLoB-c
  {"prompts": ["The native language of Norman Rockwell is _", "The mother tongue of Norman Rockwell is _", "The language Norman Rockwell speaks at hometown is _"], "knowledge": ["Norman Rockwell", "native_(P103)", "English"]}

### KLoB-r
  {"single_knowledge": ["Ann Druyan", "spouse_(P26)", "Carl Sagan"], "knowledge_chain": ["Ann Druyan", "spouse_(P26)", "Carl Sagan", "employer_(P108)", "Cornell University"], "single_knowlege_prompts": ["Ann Druyan is married to _", "The spouse of Ann Druyan is none other than _", "In matrimony, Ann Druyan is bound to _"], "knowlege_chain_prompt": "the employer of the spouse of Ann Druyan is _"}

### KLoB-u
  "extirpation sensa subiodide conquedle spikebill drabbish unvalidating becuiba _"


## Book_Cleaner
### 描述

`Book_Cleaner` 是一个用于处理电子书的模块，主要功能是从电子书文件（epub, mobi, azw）中提取文本内容，并且删除一些不需要的部分（目录，页眉页脚，图片标注等 ）。

### 环境配置

`Book_Cleaner`使用calibre库 ([[https://calibre-ebook.com/](https://calibre-ebook.com/)]) 对电子书进行解析。

`calibre`安装：

`sudo -v && wget -nv -O- https://download.calibre-ebook.com/linux-installer.sh | sudo sh /dev/stdin`

### 用法
`Book_Cleaner` 的初始化需要以下三个参数：

1. `config_path`: JSON文件路径，该文件包含了一系列的关键词信息。这些关键词用于指导文本的清洗过程。用户可以编辑这个文件，添加自定义的关键词以适应特定的清洗需求。

2. `workspace`: 一个文件夹路径，用于存储处理电子书过程中生成的临时文件。(**注意**: `Book_Cleaner`初始化时会在`workspace`中建立一个名为`book_temp_dir`的文件夹，每次调用`clean`函数时会删除`book_temp_dir `里面的所有文件, 若初始化之前已经有名为`book_temp_dir`的文件夹，则会报错。)

3. `target_path`: JSON文件路径，处理后内容将被保存在`target_path`中。

通过调用 `Book_Cleaner`的`clean`函数可以实现对电子书的处理，以下是一个简单的使用示例：

```python
# 配置文件路径
config_path = 'path/to/config.json'
# 临时文件路径
workspace = 'path/to/workspace'
# 目标路径
target_path = 'path/to/target'

# 初始化
cleaner = Book_Cleaner(config_path, workspace, target_path)

# 执行清洗处理
cleaner.process_books()
```

### 效果对比
#### 1. 去除封皮，版权页，目录等元信息
***
>~~*First published in 2015*~~
> 
>~~*Allen & Unwin*~~
> 
>~~*83 Alexander Street*~~
> 
>~~*Crows Nest NSW 2065*~~
> 
>~~*Australia*~~
> 
>~~*Phone: (61 2) 8425 0100*~~
> 
>~~*Cataloguing-in-Publication details are available from the National Library of Australia*~~
> 
>~~*ISBN 978 1 74331 9208*~~
> 
>~~*eISBN 978 1 74343 637 0*~~
> 
>~~*Internal design by Christabella Designs*~~
> 
>~~*Typeset by Post Pre-press Group, Australia*~~
> 
>~~*Extracts from The Kite Runner by Khaled Hosseini © Bloomsbury Publishing UK*~~
> 
>~~*CONTENTS*~~
> 
>~~*ZARA*~~
> 
>~~*LILI*~~
> 
>~~*EVE*~~
> 
>...
> 
>*Zara*
> 
>*She was standing at the end of the hall in the late afternoon light, her back arched against the wall, between two landscape paintings. Closing her eyes, she ran her hands up and down the red dress clinging to her curves. The dress had been designed by a genius. Its neckline was low enough to be provocative, but the hemline was below knee-length—too long for Leo, the husband of our hostess, to …*
***
#### 2. 去除图片注释
***
>*No disease has ever been so instantly recognized or so widely known and feared. …*
>
>~~*Figure 1. Smallpox Deities. Sopona (left) was the smallpox god among the Yorubas of western Africa. Sitala Mata (right), the Hindu goddess of smallpox, shown astride a donkey, was widely worshipped in temples throughout the Indian countryside.*~~
>
>*Dr. Nick Ward, one of my senior staff, accompanied me on the ward rounds. A veteran of medical service in Africa, he had cared for patients with the worst of tropical diseases. As we left the hospital, he placed his hands on the railing of a balcony, leaned over as he looked at the ground and said, “I don’t think I can ever again walk through a ward like that. It is unimaginable.”*
***

#### 3. 去除广告
***
>*A small hum of excitement rose inside her. She’d been traveling since the morning, and this trip was twice the distance of the longest journey she’d ever taken alone. But she’d done it. Exhausted but quietly exhilarated, she turned the radio up loud. This was a time for celebration. She clenched her hand in the air in a solitary fist-bump.*
>*A wooden sign on the left-hand side of the road read: BLEATH Population 3,667*
>
>~~*Good book recommendation: www.iloveebook.com !*~~
>
>*A small town was going to be a culture shock after New York City—the only place she’d ever known. She’d lived in a three-bedroom apartment with her parents and brother since she was three. And now she was heading off by herself for an entire month, to conduct research for her final year thesis at college.*
***
#### 4. 去除页数编号
***
***

# TextCleaner

## Description

FlagData TextCleaner offers a fast and extensible text data cleaning tool. It provides commonly used text cleaning modules. For additional text cleaning features, users can refer to the Operators section.

## Installation

```
Python >= 3.9
pip install flagdata
```

## Data Format

We support input data in jsonl. As to jsonl format, each line contains a json with key-value pairs.

```

input format:
{
	"id": "bc8a8f4640b153ddaddf154a605fb461",

	"text": "实际软件工程中是否真的需要100%代码覆盖率（code coverage）？\n 实际项目中，项目经理和架构师往往也是不错的测试员，一些严重bug，经常是他们先发现，比测试员还快一点。 项目中有很多的function, 但function之间的重要性是不同的，也就是说，是不均匀的，有的重要，有的没那么重要，同样是80%的覆盖率，一个覆盖到最重要的function，另一个没有，最后的结果也是天差地别的。 和覆盖率相比，更重要的是测试的顺序，确保最常用，最重要，最核心的功能先测试到，有bug，先发现，先解决，这样测试才高效，团队也会越测越有信心。 这也需要测试员对项目和需求有更深入的理解。 覆盖率高，当然好，但工程类的东西往往需要妥协和平衡，时间不够时，先测什么，后测什么，"
}
output format:
{
	"id": "bc8a8f4640b153ddaddf154a605fb461","text": "实际软件工程中是否真的需要100%代码覆盖率（code coverage）？\n 实际项目中，项目经理和架构师往往也是不错的测试员，一些严重bug，经常是他们先发现，比测试员还快一点。 项目中有很多的function, 但function之间的重要性是不同的，也就是说，是不均匀的，有的重要，有的没那么重要，同样是80%的覆盖率，一个覆盖到最重要的function，另一个没有，最后的结果也是天差地别的。 和覆盖率相比，更重要的是测试的顺序，确保最常用，最重要，最核心的功能先测试到，有bug，先发现，先解决，这样测试才高效，团队也会越测越有信心。 这也需要测试员对项目和需求有更深入的理解。 覆盖率高，当然好，但工程类的东西往往需要妥协和平衡，时间不够时，先测什么，后测什么，", "clean_text": "实际软件工程中是否真的需要100%代码覆盖率（code coverage）？\n 实际项目中，项目经理和架构师往往也是不错的测试员，一些严重bug，经常是他们先发现，比测试员还快一点。 项目中有很多的function, 但function之间的重要性是不同的，也就是说，是不均匀的，有的重要，有的没那么重要，同样是80%的覆盖率，一个覆盖到最重要的function，另一个没有，最后的结果也是天差地别的。 和覆盖率相比，更重要的是测试的顺序，确保最常用，最重要，最核心的功能先测试到，有bug，先发现，先解决，这样测试才高效，团队也会越测越有信心。 这也需要测试员对项目和需求有更深入的理解。"
}
```

## Default Processors

We provide several useful filters by default. For more data cleaning methods, users can refer to the Operators section to add them.

The default filters will do the following cleaning procedures:

​	1. Remove documents where the proportion of line break characters exceeds 0.25 of the total number of characters.

​	2. Remove sentences containing specific content.

​	3. Remove documents where the ratio of numerical characters is greater than 0.5.

​	4. Replace \xa0 and \u3000 with standard spaces and remove other invisible characters.

​	5. Remove multiple line spaces.

## Quick start

from flagdata.cleaner.text_cleaner import DataCleaner
```
# safe importing of main module in multi-processing

if __name__ == "__main__": 
    # you need to specify your own configuration file path
    cleaner = DataCleaner("config.yaml")
    cleaner.clean()
```


