# 代码核心功能说明
1.get_words() 函数：
def get_words(filename):
    words = []
    with open(filename, 'r', encoding='utf-8') as fr:
        for line in fr:
            line = line.strip()
            line = re.sub(r'[.【】0-9、——。，！~\*]', '', line)
            line = cut(line)
            line = filter(lambda word: len(word) > 1, line)
            words.extend(line)
    return words
all_words = []
该函数从一个文本文件中读取文本并进行处理
读取文本：通过 open() 打开文件并按行读取。
去除无效字符：使用正则表达式 re.sub() 来去除常见的无效字符（如数字、标点符号等）。
分词：利用 jieba.cut() 对每一行文本进行分词处理。
过滤长度为1的词：通过 filter() 过滤掉长度为1的词，这些词对分类任务没有太大作用。
返回分词结果：将处理后的词汇（即词列表）返回
