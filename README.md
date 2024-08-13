# 汉语文本转语音（TTS）数据集

基于语言学本体构建，全面覆盖汉语多音字、音变等现象的高效TTS数据集。

---

## 数据集介绍

汉语TTS数据集是一个基于**语言学本体构建的全面测试集**，专为测试和评估文本到语音（TTS）前端系统的准确性和自然度而设计。数据集涵盖了汉语中的各种语音现象，包括普通话水平测试、汉语多音字、汉语音变、中英混杂文本以及特殊符号和数字的处理。通过这一全面的测试集，TTS前端系统的潜在问题能够被系统性地发现和修正，确保生成的语音既自然又准确。

## 数据集用途

1. **TTS系统评估与优化**：系统性评估和优化TTS前端系统在多种语音现象下的性能，包括发音自然度和鲁棒性，确保高质量的语音输出。

2. **发音准确性验证**：通过对多音字、音变现象的测试，验证并修正TTS系统在复杂发音场景中的准确性，确保上下文敏感的正确发音。

3. **特殊文本处理能力测试**：评估TTS系统在处理中英混杂文本、特殊符号和数字等非标准文本时的表现，确保系统在多语言环境和边缘用例中的广泛适用性。

4. **语言学研究与教育工具开发**：支持语言学研究和教育软件开发，帮助分析汉语发音现象，并为学习者提供正确的发音指导。

5. **语音交互系统测试**：测试语音助手、智能设备和自动化客服系统中的TTS模块，确保其在多样化文本输入场景下的一致性和高质量表现。
   .....


## 文件描述

| 文件名 | 描述 | 大小 |
| ------ | ---- | ---- |
| Chinese Mandarin Proficiency Test.json | 包含普通话水平测试的文本，共计60篇。 | 中 |
| Chinese Phonological Changes.json | 包含汉语音变现象的文本，涵盖变调、轻声、儿化、啊音变等。 | 中 |
| Chinese Polyphonic Characters.json | 包含多音字的文本，基于字频语料库的统计。 | 中 |
| Mixed Chinese and English Text.json | 包含中英混杂文本，基于Google万亿字语料库的n-gram频率分析。 | 中 |
| Special Symbols and Numbers.json | 包含电话号码、度量单位、货币单位、时间日期、数学符号等特殊符号文本。 | 中 |
| TTS_Test.json | 从以上5部分抽取的1万字测试集。 | 小 |
| TTS_Test.txt | 包含TTS_Test.json文件中的文本内容。 | 小 |

## 数据集格式说明

### TTS_Test.json 格式说明
数据包含以下部分：
| 数据部分           | 抽取方式       | 句子数 | 总字数 | 平均句长（字） |
| ------------------ | -------------- | ------ | ------ | -------------- |
| 普通话水平测试     | 分类随机抽取   | 128    | 4000   | 31.25          |
| 汉语音变           | 分类随机抽取   | 148    | 3999   | 27.02          |
| 汉语多音字         | 按字频抽取     | 155    | 3984   | 25.70          |
| 特殊符号及数字     | 分类随机抽取   | 118    | 4000   | 26.67          |
| 中英混杂           | 按词频抽取     | 193    | 3993   | 20.69          |

```markdown
{
  "id": "000039",  # 文本句子text的编号
  "source": "汉语音变_轻声",  # TTS测试集的组成部分，即重点测试的语音方面
  "words": [ "打量 dǎliang", "关系 guānxi" ],  # 词语列表，代表重点关注的发音
  "text": "她用怀疑的眼神打量着他，两人之间的关系似乎变得微妙起来。",  # 测试文本
  "pinyin": "ta1 yong4 huai2 yi2 de yan3 shen2 da3 liang4 zhe ta1 ， liang3 ren2 zhi1 jian1 de guan1 xi4 si4 hu1 bian4 de2 wei1 miao4 qi3 lai2 。"  # 文本对应的拼音，含声调
}
```

### 各部分数据集说明

| 文件名 | 数据集部分 | 内容 | 来源 | 目的 | 总句子数 | 总字数 | 平均句长（字） |
| --- | --- | --- | --- | --- | --- | --- | --- |
| **Chinese Mandarin Proficiency Test.json** | 汉语普通话水平测试 | 包括来自普通话朗读作品的文本，共计60篇。 | 普通话学习网 | 综合检测TTS系统在标准普通话中的表现，包括发音准确性、语调自然度、节奏韵律等。通过这一部分，可以发现系统在处理标准普通话时可能存在的发音问题或不自然的语调问题。 | 1013 | 31899 | 31.49 |
| **Chinese Polyphonic Characters.json** | 汉语多音字 | 涵盖每百万字出现10次以上的多音字，基于字频语料库（25亿字）。 | 现汉汉语第7版词典所有多音字统计，基于25亿字字频排序；进一步用于【大语言模型数据生成】 | 评估TTS系统在处理多音字时的准确性。多音字在汉语中非常常见，错误的发音会严重影响语音的自然度和可理解性。通过测试多音字，可以发现系统在上下文判断和发音预测方面的不足。 | 402 | 10435 | 25.96 |
| **Chinese Phonological Changes.json** | 汉语音变 | 包括变调、轻声、儿化、啊音变等，覆盖汉语绝大多数音变情况。 | 多个版本的现代汉语教材音变归纳总结；进一步用于【大语言模型数据生成】 | 测试TTS系统在处理语流音变现象时的表现。汉语中的音变现象复杂多样，正确处理这些音变对于生成自然流畅的语音至关重要。这部分测试有助于发现系统在音变处理上的不足，并加以改进。 | 683 | 17645 | 25.83 |
| **Mixed Chinese and English Text.json** | 中英混杂 | 根据单词频率确定的中英混杂文本，基于Google万亿字语料库的n-gram频率分析。 | 中英混杂语料ASRU测试集（基于Google万亿字语料库的单词词频进行排序） | 评估TTS系统在处理中英混杂文本时的表现。现代汉语中常常混杂使用英文单词，系统需要能够准确处理和发音这些混杂的文本，确保在不同语言之间的切换自然流畅。 | 3696 | 70717 | 19.13 |
| **Special Symbols and Numbers.json** | 特殊符号及数字 | 包括电话号码、度量单位、货币单位、时间日期、数学符号、其他等。 | GitHub开源语料；进一步用于【大语言模型数据生成】 | 检测TTS系统在处理特殊符号和数字时的准确性和自然度。特别是对于应用场景中经常出现的数字和符号，系统需要能够正确识别和发音。这部分测试可以帮助发现和纠正系统在处理非文本内容时的潜在问题。 | 281 | 7308 | 26.01 |

## 数据集优势

1. **基于语言学本体的全面覆盖**：数据集从语言学本体角度出发，涵盖了汉语中的多音字、音变现象、中英混杂文本、特殊符号和数字，确保TTS系统在不同发音场景下具备全面的覆盖和测试精度。

2. **高效发现与修正问题**：数据集设计时平均句长小于30字，能更快发现问题（短句子更容易突出TTS系统的问题），更精准的定位问题（如一句话中就包含了多个多音字发音情况），提高测试效率（短句子生成的音频更短），达到更全面的测试覆盖率（用较少的文本覆盖多个测试方面）。

3. **适应实际应用场景**：数据集专注于汉语的关键发音和文本处理场景，包括标准普通话、多音字、音变现象、中英混杂文本以及特殊符号和数字的处理，确保TTS系统在广泛的实际应用中表现优异。

4. **均衡的数据分布**：数据集在构建过程中采用随机、分类和频率等逻辑筛选，确保数据分布均衡且全面，最大化测试覆盖率。

## 数据集构建流程
![Chinese TTS Test Set (Polyphonic Characters) Construction Process](https://github.com/danielwei0214/Chinese-TTS-Dataset/blob/main/Chinese%20TTS%20Test%20Set%20(Polyphonic%20Characters)%20Construction%20Process.png)


### 大模型数据生成prompt

#### 汉语多音字&汉语音变
```markdown
prompt = f"""
你是一个中文语言学家和高级造句专家，擅长用词造句，直到达到最高的中文语言水平。
首先了解每个词语的语义和拼音，（括号内为其语义提示），思考其可能出现的上下文语境；
其次找到词语的最佳使用语境及联系（显示或隐含联系，如词性，主题，场景等），达到语义语用相统一；
最后参考示例，根据语义读音及提示，逐步思考使用词语造句；确保符合中文表达习惯，避免用词不当，没有语法错误，表达自然流畅。
要求必须包含列表中的词语，每个词语仅使用一次，不要重复使用，长度要求不超过50汉字字符。
示例：{{"words": ["搬起石头砸自己的脚 bānqǐshítouzázìjǐdejiǎo", "的确 díquè", "众矢之的 zhòngshǐzhīdì"],"text": "他这么做，的确是搬起石头砸自己的脚，成了众矢之的。"}}

词语：```{prompt_words}``` 

注意：只能输出json格式内容，包含words和text键值，words值为列表，不能输出其他无关内容。必须包含列表中的词语。
"""
```

#### 特殊符号及数字
```markdown
prompt = f"""
你是一个中文语言学家和高级造句专家，擅长用特殊符号及数字造句，直到达到最高的中文语言水平。
首先了解每个特殊符号/数字的语义，（括号内为其汉字读法，text输出不能包含括号及其内容），思考其可能出现的上下文语境；
其次找到特殊符号/数字的最佳使用语境及联系（显示或隐含联系，如词性，主题，场景等），达到语义语用相统一；
最后参考示例，根据语义及汉字读法，逐步思考使用其进行造句；确保符合中文表达习惯，避免用词不当，没有语法错误，表达自然流畅。
要求必须包含列表中的特殊符号或数字，每个仅使用一次，不要重复使用，长度要求不超过50汉字字符。
示例：
{{"words": ["℃  (摄氏度)"],"text": "今天的气温高达30℃，太热了！"}}
{{ "words": ["给12315打个电话  (给幺二三幺五打个电话)"], "text": "如果遇到消费纠纷，不妨给12315打个电话寻求帮助。"}}

词语：```{prompt_words}``` 

注意：只能输出json格式内容，包含words和text键值，words值为列表。输出的words需保留其源编码格式，要求必须包含列表中的特殊符号或数字

不能输出其他无关内容。
"""
```

## 许可证和引用声明

**许可证**

本数据集使用 [CC BY-NC 4.0 许可证](https://creativecommons.org/licenses/by-nc/4.0/)进行分发。您可以自由使用和分享数据集，但需注明出处，并且仅限于非商业用途。

**引用声明**
如果您在研究或其他项目中使用了“汉语TTS测试集”，请注明数据集的来源，并使用以下引用格式：

```markdown
汉语文本转语音（TTS）数据集| Chinese TTS Dataset:  
[https://github.com/danielwei0214/Chinese-TTS-Dataset]
```
通过适当的引用，您帮助我们提升数据集的影响力并支持进一步的研究与开发。

## 致谢

在制作“汉语文本转语音（TTS）数据集”的过程中，我们使用了以下资源或工具：

- [普通话学习网](http://www.pthxx.com/b_audio/01_langdu_1/index_2.html) 提供的普通话水平测试内容。
- [字频语料库（25亿字）](https://faculty.blcu.edu.cn/xinghb/zh_CN/article/167473/content/1437.htm) 提供的汉语字频统计数据。
- [中英混杂语料ASRU测试集](https://www.datatang.com/competition) 提供的中英混杂文本数据。
- [Google万亿字语料库](https://github.com/first20hours/google-10000-english) 提供的n-gram频率分析数据。
- [GitHub特殊符号语料](https://github.com/wenet-e2e/WeTextProcessing) 提供的特殊符号及数字数据。
- [《现代汉语词典》第7版数据](https://github.com/CNMan/XDHYCD7th) 提供的现代汉语词汇数据。
- 多个版本的现代汉语教材，包括《现代汉语》（邢福义版）、《普通话水平测试指导用书》（江苏版）、《普通话测试与培训教程》（科学出版社）、《普通话水平测试教程》（原子能出版社）。

在此，我们对相关数据的贡献者表示衷心的感谢。

---

# Chinese Text-to-Speech (TTS) Dataset

An efficient TTS dataset constructed based on linguistic ontology, covering various phenomena in Chinese, such as polyphonic characters and phonological changes.

---

## Dataset Overview

The Chinese TTS dataset is a **comprehensive test set built on linguistic ontology**, designed for testing and evaluating the accuracy and naturalness of text-to-speech (TTS) frontend systems. It covers various phonetic phenomena in Chinese, including Mandarin proficiency tests, polyphonic characters, phonological changes, mixed Chinese-English text, and the handling of special symbols and numbers. This comprehensive test set allows for the systematic identification and correction of potential issues in TTS frontend systems, ensuring natural and accurate speech output.

## Dataset Uses

1. **TTS System Evaluation and Optimization**: Systematically evaluate and optimize TTS frontend systems' performance across various phonetic phenomena, including pronunciation naturalness and robustness, to ensure high-quality speech output.

2. **Pronunciation Accuracy Verification**: Test and refine TTS systems' accuracy in complex pronunciation scenarios involving polyphonic characters and phonological changes, ensuring context-sensitive correct pronunciation.

3. **Special Text Handling Capability Testing**: Assess TTS systems' performance in processing mixed Chinese-English texts, special symbols, and numbers, ensuring broad applicability in multilingual environments and edge cases.

4. **Linguistic Research and Educational Tool Development**: Support linguistic research and educational software development by analyzing Chinese pronunciation phenomena and providing correct pronunciation guidance for learners.

5. **Voice Interaction System Testing**: Test TTS modules in voice assistants, smart devices, and automated customer service systems, ensuring consistency and high-quality performance across diverse text input scenarios.

## File Descriptions

| Filename                           | Description                                       | Size |
| --------------------------------- | ------------------------------------------------- | ---- |
| Chinese Mandarin Proficiency Test.json | Texts from Mandarin proficiency tests, 60 pieces. | Medium |
| Chinese Phonological Changes.json | Texts covering phonological changes, including tone changes, light tones, retroflex endings, and "ah" tone changes. | Medium |
| Chinese Polyphonic Characters.json | Texts with polyphonic characters, based on frequency statistics. | Medium |
| Mixed Chinese and English Text.json | Texts with mixed Chinese and English, based on Google trillion-word corpus n-gram frequency analysis. | Medium |
| Special Symbols and Numbers.json | Texts with special symbols, including phone numbers, measurement units, currency units, dates, times, and mathematical symbols. | Medium |
| TTS_Test.json                     | A 10,000-character test set extracted from the above 5 parts. | Small |
| TTS_Test.txt                      | Text content from TTS_Test.json file.             | Small |

## Dataset Format

### TTS_Test.json Format

The data includes the following parts:

| Data Part               | Extraction Method | Sentence Count | Total Characters | Average Sentence Length (Characters) |
| ---------------------- | ------------------ | -------------- | ---------------- | ----------------------------------- |
| Mandarin Proficiency Test | Random Sampling    | 128            | 4000             | 31.25                               |
| Phonological Changes   | Random Sampling    | 148            | 3999             | 27.02                               |
| Polyphonic Characters  | Frequency-based    | 155            | 3984             | 25.70                               |
| Special Symbols and Numbers | Random Sampling    | 118            | 4000             | 26.67                               |
| Mixed Chinese and English | Frequency-based    | 193            | 3993             | 20.69                               |

```markdown
{
  "id": "000039",  # Sentence ID
  "source": "Chinese Phonological Changes_Light Tone",  # Test set component
  "words": [ "打量 dǎliang", "关系 guānxi" ],  # Key pronunciation words
  "text": "她用怀疑的眼神打量着他，两人之间的关系似乎变得微妙起来。",  # Test text
  "pinyin": "ta1 yong4 huai2 yi2 de yan3 shen2 da3 liang4 zhe ta1 ， liang3 ren2 zhi1 jian1 de guan1 xi4 si4 hu1 bian4 de2 wei1 miao4 qi3 lai2 。"  # Pinyin with tones
}
```

### Dataset Part Descriptions

| Filename                          | Dataset Part                   | Content | Source | Purpose | Total Sentences | Total Characters | Average Sentence Length (Characters) |
| -------------------------------- | ------------------------------ | ------- | ------ | ------- | ---------------- | ---------------- | ----------------------------------- |
| **Chinese Mandarin Proficiency Test.json** | Mandarin Proficiency Test      | Texts from Mandarin reading materials, 60 pieces. | Mandarin Learning Network | Comprehensive testing of TTS system performance in standard Mandarin, including pronunciation accuracy, intonation naturalness, rhythm, and prosody. Identifies issues in standard Mandarin processing. | 1013 | 31899 | 31.49 |
| **Chinese Polyphonic Characters.json** | Polyphonic Characters          | Covers polyphonic characters appearing more than 10 times per million characters, based on a 2.5 billion character frequency corpus. | Modern Chinese Dictionary 7th Edition | Evaluates TTS system accuracy in handling polyphonic characters. Errors in polyphonic characters significantly affect naturalness and comprehensibility. Identifies issues in context judgment and pronunciation prediction. | 402 | 10435 | 25.96 |
| **Chinese Phonological Changes.json** | Phonological Changes           | Includes tone changes, light tones, retroflex endings, and "ah" tone changes, covering most phonological changes in Chinese. | Modern Chinese textbooks summarization | Tests TTS system performance in handling phonological changes. Proper handling is crucial for generating natural, fluent speech. Identifies issues in phonological change processing. | 683 | 17645 | 25.83 |
| **Mixed Chinese and English Text.json** | Mixed Chinese-English Text     | Texts based on word frequency analysis from Google trillion-word corpus. | Mixed Chinese-English Corpus ASRU Test Set | Evaluates TTS system performance in processing mixed Chinese-English text. Systems need to handle and pronounce mixed texts accurately for smooth language switching. | 3696 | 70717 | 19.13 |
| **Special Symbols and Numbers.json** | Special Symbols and Numbers    | Includes phone numbers, measurement units, currency units, dates, times, mathematical symbols, etc. | GitHub Open Source Corpus | Tests TTS system accuracy and naturalness in handling special symbols and numbers. Accurate recognition and pronunciation are crucial for frequent symbols and numbers. | 281 | 7308 | 26.01 |

## Dataset Advantages

1. **Comprehensive Coverage Based on Linguistic Ontology**: The dataset covers polyphonic characters, phonological changes, mixed Chinese-English texts, special symbols, and numbers, ensuring thorough testing across various pronunciation scenarios.

2. **Efficient Problem Detection and Correction**: With an average sentence length of less than 30 characters, issues are detected more quickly and accurately. Short sentences highlight TTS system issues and provide a comprehensive test coverage with less text.

3. **Real-world Application Scenarios**: Focuses on key pronunciation and text processing scenarios in Chinese, including standard Mandarin, polyphonic characters, phonological changes, mixed texts, and special symbols, ensuring excellent performance in practical applications.

4. **Balanced Data Distribution**: Data is selected using random, categorical, and frequency-based methods to ensure a balanced and comprehensive distribution, maximizing test coverage.

## Dataset Construction Process
![Chinese TTS Test Set (Polyphonic Characters) Construction Process](https://github.com/danielwei0214/Chinese-TTS-Dataset/blob/main/Chinese%20TTS%20Test%20Set%20(Polyphonic%20Characters)%20Construction%20Process.png)

### Large Model Data Generation Prompts

#### Chinese Polyphonic Characters & Phonological Changes
```markdown
prompt = f"""
你是一个中文语言学家和高级造句专家，擅长用词造句，直到达到最高的中文语言水平。
首先了解每个词语的语义和拼音，（括号内为其语义提示），思考其可能出现的上下文语境；
其次找到词语的最佳使用语境及联系（显示或隐含联系，如词性，主题，场景等），达到语义语用相统一；
最后参考示例，根据语义读音及提示，逐步思考使用词语造句；确保符合中文表达习惯，避免用词不当，没有语法错误，表达自然流畅。
要求必须包含列表中的词语，每个词语仅使用一次，不要重复使用，长度要求不超过50汉字字符。
示例：{{"words": ["搬起石头砸自己的脚 bānqǐshítouzázìjǐdejiǎo", "的确 díquè", "众矢之的 zhòngshǐzhīdì"],"text": "他这么做，的确是搬起石头砸自己的脚，成了众矢之的。"}}

词语：```{prompt_words}``` 

注意：只能输出json格式内容，包含words和text键值，words值为列表，不能输出其他无关内容。必须包含列表中的词语。
"""
```

#### Special Symbols and Numbers
```markdown
prompt = f"""
你是一个中文语言学家和高级造句专家，擅长用特殊符号及数字造句，直到达到最高的中文语言水平。
首先了解每个特殊符号/数字的语义，（括号内为其汉字读法，text输出不能包含括号及其内容），思考其可能出现的上下文语境；
其次找到特殊符号/数字的最佳使用语境及联系（显示或隐含联系，如词性，主题，场景等），达到语义语用相统一；
最后参考示例，根据语义及汉字读法，逐步思考使用其进行造句；确保符合中文表达习惯，避免用词不当，没有语法错误，表达自然流畅。
要求必须包含列表中的特殊符号或数字，每个仅使用一次，不要重复使用，长度要求不超过50汉字字符。
示例：
{{"words": ["℃  (摄氏度)"],"text": "今天的气温高达30℃，太热了！"}}
{{ "words": ["给12315打个电话  (给幺二三幺五打个电话)"], "text": "如果遇到消费纠纷，不妨给12315打个电话寻求帮助。"}}

词语：```{prompt_words}``` 

注意：只能输出json格式内容，包含words和text键值，words值为列表。输出的words需保留其源编码格式，要求必须包含列表中的特殊符号或数字

不能输出其他无关内容。
"""
```
## License and Citation

**License**

This dataset is distributed under the [CC BY-NC 4.0 License](https://creativecommons.org/licenses/by-nc/4.0/). You are free to use and share the dataset with proper attribution, for non-commercial purposes only.

**Citation**

If you use the "Chinese TTS Dataset" in research or other projects, please acknowledge the source and use the following citation format:

```markdown
Chinese Text-to-Speech (TTS) Dataset:  
[https://github.com/danielwei0214/Chinese-TTS-Dataset]
```

Appropriate citation helps enhance the dataset's impact and supports further research and development.

## Acknowledgments

The following resources and tools were used in creating the "Chinese Text-to-Speech (TTS) Dataset":

- [Mandarin Learning Network](http://www.pthxx.com/b_audio/01_langdu_1/index_2.html) for Mandarin proficiency test content.
- [2.5 Billion Character Frequency Corpus](https://faculty.blcu.edu.cn/xinghb/zh_CN/article/167473/content/1437.htm) for Chinese character frequency statistics.
- [Mixed Chinese-English Corpus ASRU Test Set](https://www.datatang.com/competition) for mixed text data.
- [Google Trillion Word Corpus](https://github.com/first20hours/google-10000-english) for n-gram frequency analysis data.
- [GitHub Special Symbols Corpus](https://github.com/wenet-e2e/WeTextProcessing) for special symbols and numbers data.
- [7th Edition of Modern Chinese Dictionary](https://github.com/CNMan/XDHYCD7th) for modern Chinese vocabulary data.
- Various editions of Modern Chinese textbooks, including "Modern Chinese" (Xing Fuyi Edition), "Mandarin Proficiency Test Guide" (Jiangsu Edition), "Mandarin Test and Training Tutorial" (Science Press), and "Mandarin Proficiency Test Tutorial" (Atomic Energy Press).

We extend our sincere thanks to contributors of related data.
