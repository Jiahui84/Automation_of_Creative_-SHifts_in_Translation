# Automation_of_Creative_-SHifts_in_Translation
# Codes for the project "Creativity in Translation" supervised by Dr. Ana Guerberof Arenas and Dr. Antonio Toral

In this project, we explored if we can use the cosine distance of bilingual word pairs to automate if there are creative shifts happend, and the higher the cosine ditance is, the more deviation between the word pair is, so the more creativity during the transaltion is.  

The codes should be combined with other tools, files and models, and the steps are listed below:
1. Sentence-aligned Source Text and Target Text (Source language vs. Target language)
2. Pre-tokenize both texts according to the input format of the word alignment tool. In this study, we used awesome-align (link of the tool: https://github.com/neulab/awesome-align), so the input format should be like below (example link: https://github.com/neulab/awesome-align/blob/master/examples/zhen.src-tgt):
   科学家 一直 猜想 土卫六 上 存在 着 由 液态 甲烷 构成 的 海洋 。 ||| scientists have long conjectured that oceans of liquid methane exist on titan .
   So in order to get this format:
    1) I pre tokenize the Chinese text with Jieba (see the codes: (step1)Add_space_TT.ipynb; link of the tool: https://github.com/fxsjy/jieba)
    2) And pre tokenize the English text with mosestokenizer (see the codes: (step2)Add_space_ST.ipynb; link: of the tool: https://github.com/moses-smt/mosesdecoder/blob/master/scripts/tokenizer/detokenizer.perl)
    3) And then use the codes "(Step3)Combine_ST_and_TT_for_alignment.ipynb" to the get right input format for awesome_align
3. Prepare word embedding models. In our study, we use the pre-trained word vecctors of fasttext (link for the model: https://fasttext.cc/docs/en/crawl-vectors.html)
4. With the word vectors model, we can use "(step4)GET_EMBEDDING.ipynb" to get the word vectors of every token in the text and append the results in a txt file.
5. Then we need to map the bilingual word vectors. In our study, we use the tool vecmap (link of the tool: https://github.com/artetxem/vecmap) to do the bilingual mapping:
    1) As the input format for vecmap is EMB file, so I use the codes "(step5)turn_txt_to_EMB.ipynb" to get the EMB files
    2) But there are requirements for the input files of turning to EMB files. We need to add "'Number of tokens' 'dimensions'" at the first line of the txt file, and to get the number of tokens, we can use the codes "(step6)count_token.ipynb".
6. Then we use "(step7)Query_dtstance.ipynb" to get the cosine distance between the aligned words, and visualize them as boxplot.
