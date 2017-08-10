1. text1.concordance("aaa") will display 20 sentences including "aaa"
2. text1.similar("aaa") will display some related words
3. len(text1)：返回总字数
4. set(text1)：返回文本的所有词集合
5. len(set(text4))：返回文本总词数
6. text4.count("is")：返回“is”这个词出现的总次数
7. FreqDist(text1)：统计文章的词频并按从大到小排序存到一个列表里
8. fdist1 = FreqDist(text1);fdist1.plot(50, cumulative=True)：统计词频，并输出累计图像

9. ### 语料库的通用接口    

        fileids()：返回语料库中的文件

        categories()：返回语料库中的分类

        raw()：返回语料库的原始内容

        words()：返回语料库中的词汇

        sents()：返回语料库句子

        abspath()：指定文件在磁盘上的位置

        open()：打开语料库的文件流
        
10. ### 词干提取器
    
        >>> import nltk
        >>> porter = nltk.PorterStemmer()
        >>> porter.stem('lying')
        
11. ### 词性标注器

        >>> import nltk
        >>> text = nltk.word_tokenize("And now for something completely different")
        >>> nltk.pos_tag(text)
        [('And', 'CC'), ('now', 'RB'), ('for', 'IN'), ('something', 'NN'), ('completely', 'RB'), ('different', 'JJ')]
        其中CC是连接词，RB是副词，IN是介词，NN是名次，JJ是形容词
        
12. 
