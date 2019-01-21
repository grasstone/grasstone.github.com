---
layout: post
title:  "用beautifulsoap 4 抓取網上資源"
date:   2019-01-09 18:44:52 +0800
categories: Python
---

現時網上提拱抓取的方案，主要是安裝Extension，如**Data Scraper**，或**Agenty** 。 這些雖然功能大，但都需要付費，倒不如自己寫一個。

事前準備：
1. Python
2. 安裝以下package:
   1.  用作呼叫網絡資源
       > pip install requests
   2.  用作提取HTML Element Library
       > pip install beautifulsoup4
   3.  把提取的內容整理，以CSV輸出
       > pip install pandas
3.  我這次作為了提取以下網站的生詞庫而寫的Script，它有總共17頁。
     * [examword ielts 4000 academic words page 1](https://www.examword.com/ielts-list/4000-academic-word-1?la=en)
4. 再來就是Show me the codes! 不想看文字的可直接看code.

<br>
5. 當中最重要的要點是知道你想提取的HTML Element是用什麼方式提取。以我為例，以css class來提取想要的內容(需要使用view element來看)。
<br>
```
soup.find_all("span", class_="listWordWord")
```
<br>
6. 而你不是想要HTML Element，而是內容，所以就用
```
tag.get_text()
```
<br>
7. 最後把data 轉做 dataframe，再把17頁dataframe，合成為一輸出為CSV。
```
    page_df = pd.DataFrame({"word" : words,
                            "type" : word_types,
                            "explanation" : word_explans

    })

    result = pd.concat(frames)

    result.to_csv('/Users/yourfilepath/Documents/data/ielts_words.csv')
```
<br>
以上內容均為原創，引用請加上連接鍵，謝謝。