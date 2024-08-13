# 汉语TTS测试集

汉语TTS测试集 - 构建全面的测试集，确保文本到语音系统的准确性和自然度。

---

## 数据集介绍

汉语TTS测试集专为测试和评估文本到语音（TTS）系统的准确性和自然度而设计，涵盖了汉语中的各种语音现象，包括普通话水平测试、汉语多音字、汉语音变、中英混杂文本、以及特殊符号和数字的处理。通过构建全面的测试集，TTS系统的各种可能问题得以系统性地暴露和修正，确保最终生成的语音既自然又准确。

## 数据集用途

1. **TTS系统评估与优化**：该数据集主要用于评估和优化文本到语音（TTS）系统的性能，确保生成的语音在各种语音现象下都能保持高质量和自然度。

2. **发音准确性验证**：通过对多音字、音变现象的全面测试，验证TTS系统在处理复杂发音场景中的准确性，发现并修正系统中的潜在错误。

3. **特殊文本处理能力测试**：评估TTS系统在处理中英混杂文本、特殊符号和数字等非标准文本时的表现，确保系统在实际应用中的广泛适用性。

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

### TTS_Test.json/txt 格式说明

```json
{
  "id": "000039",  # 文本句子text的编号
  "source": "汉语音变_轻声",  # TTS测试集的组成部分，即重点测试的语音方面
  "words": [ "打量 dǎliang", "关系 guānxi" ],  # 词语列表，代表重点关注的发音
  "text": "她用怀疑的眼神打量着他，两人之间的关系似乎变得微妙起来。",  # 测试文本
  "pinyin": "ta1 yong4 huai2 yi2 de yan3 shen2 da3 liang4 zhe ta1 ， liang3 ren2 zhi1 jian1 de guan1 xi4 si4 hu1 bian4 de2 wei1 miao4 qi3 lai2 。"  # 文本对应的拼音，含声调
}
```

### 各部分数据集格式说明

| 文件名 | 数据集部分 | 内容 | 来源 | 目的 |
| --- | --- | --- | --- | --- |
| **Chinese Mandarin Proficiency Test.json** | 汉语普通话水平测试 | 包括来自普通话朗读作品的文本，共计60篇。 | 普通话学习网 | 综合检测TTS系统在标准普通话中的表现，包括发音准确性、语调自然度、节奏韵律等。通过这一部分，可以发现系统在处理标准普通话时可能存在的发音问题或不自然的语调问题。 |
| **Chinese Polyphonic Characters.json** | 汉语多音字 | 涵盖每百万字出现10次以上的多音字，基于字频语料库（25亿字）。 | 现汉汉语词典所有多音字统计，基于25亿字字频排序；进一步用于【大语言模型数据生成】 | 评估TTS系统在处理多音字时的准确性。多音字在汉语中非常常见，错误的发音会严重影响语音的自然度和可理解性。通过测试多音字，可以发现系统在上下文判断和发音预测方面的不足。 |
| **Chinese Phonological Changes.json** | 汉语音变 | 包括变调、轻声、儿化、啊音变等，覆盖汉语绝大多数音变情况。 | 多个版本的现代汉语教材音变归纳总结；进一步用于【大语言模型数据生成】 | 测试TTS系统在处理语流音变现象时的表现。汉语中的音变现象复杂多样，正确处理这些音变对于生成自然流畅的语音至关重要。这部分测试有助于发现系统在音变处理上的不足，并加以改进。 |
| **Mixed Chinese and English Text.json** | 中英混杂 | 根据单词频率确定的中英混杂文本，基于Google万亿字语料库的n-gram频率分析。 | 中英混杂语料ASRU（基于Google万亿字语料库的单词词频进行排序） | 评估TTS系统在处理中英混杂文本时的表现。现代汉语中常常混杂使用英文单词，系统需要能够准确处理和发音这些混杂的文本，确保在不同语言之间的切换自然流畅。 |
| **Special Symbols and Numbers.json** | 特殊符号及数字 | 包括电话号码、度量单位、货币单位、时间日期、数学符号、其他等。 | GitHub开源语料；进一步用于【大语言模型数据生成】 | 检测TTS系统在处理特殊符号和数字时的准确性和自然度。特别是对于应用场景中经常出现的数字和符号，系统需要能够正确识别和发音。这部分测试可以帮助发现和纠正系统在处理非文本内容时的潜在问题。 |


## 数据集优势

1. **基于语言学本体的全面覆盖**：数据集从语言学本体角度出发，涵盖了汉语中的多音字、音变现象、中英混杂文本、特殊符号和数字，确保TTS系统在不同发音场景下具备全面的覆盖和测试精度。

2. **高效发现与修正问题**：数据集设计时平均句长小于30字，能更快发现问题（短句子更容易突出TTS系统的问题），更精准的定位问题（如一句话中就包含了多个多音字发音情况），提高测试效率（短句子生成的音频更短），达到更全面的测试覆盖率（用较少的文本覆盖多个测试方面）。

3. **适应实际应用场景**：数据集专注于汉语的关键发音和文本处理场景，包括标准普通话、多音字、音变现象、中英混杂文本以及特殊符号和数字的处理，确保TTS系统在广泛的实际应用中表现优异。

4. **均衡的数据分布**：数据集在构建过程中采用随机、分类和频率等逻辑筛选，确保数据分布均衡且全面，最大化测试覆盖率。

## 数据集构建流程


- **普通话学习网**: 提供了普通话水平测试的文本内容。
- **字频语料库（25亿字）**: 用于多音字的字频统计和文本生成。
- **现代汉语教材**: 提供了汉语音变现象的文本内容。
- **Google万亿字语料库**: 提供了中英混杂文本的n-gram频率分析。
- **Github开源语料**: 提供了特殊符号及数字文本内容。

## 许可证和引用声明

**许可证**

本数据集使用 [CC BY-NC 4.0 许可证](https://creativecommons.org/licenses/by-nc/4.0/)进行分发。您可以自由使用和分享数据集，但需注明出处，并且仅限于非商业用途。

**引用声明**

如果您在研究或其他项目中使用了“汉语TTS测试集”，请注明数据集的来源，并使用以下引用格式：

```markdown
汉语TTS测试集 | Chinese TTS Test Set:  
https://github.com/danielwei0214/Mandarin-Chinese-Syllable-Dataset
```
通过适当的引用，您帮助我们提升数据集的影响力并支持进一步的研究与开发。

## 致谢

在制作“汉语TTS测试集”的过程中，我们使用了以下资源和工具：

- [普通话学习网](http://www.pthxx.com/b_audio/01_langdu_1/index_2.html) 提供的普通话水平测试内容。
- [字频语料库（25亿字）](https://faculty.blcu.edu.cn/xinghb/zh_CN/article/167473/content/1437.htm) 提供的多音字统计数据。
- 各种现代汉语教材，包括《现代汉语》、《普通话水平测试指导用书》等。
- [Google万亿字语料库](https://github.com/first20hours/google-10000-english) 提供的中英混杂文本数据。
- [Github开源语料](https://github.com/wenet-e2e/WeTextProcessing) 提供的特殊符号及数字数据。

我们对这些资源的贡献者表示衷心的感谢。
