# llm_competition

EDAをしているコード コサイン類似度の計算などNLPの典型的な手法について学べる。今後も何回か見直す。

https://www.kaggle.com/code/ddlc19/ai-or-not-ai-delving-into-essays-with-eda/edit

https://www.kaggle.com/code/ddlc19/detectai-transformers-baseline/edit 

とりあえずこのnotebookを理解する

Transformersの理解不足を感じたので、とりあえずBERTによる自然言語処理入門の4~7章を読む。

Transformersの仕様がよく分かってない
```
compute_metrics関数内で使用されているlabelsは、通常はTrainerによる評価の際に、提供されたデータセット（ここではeval_dataset）に含まれる各サンプルの真のラベルです。評価時にモデルがデータセット内のサンプルを予測し、その予測結果と真のラベルを比較するためにlabelsが必要となります。

具体的には、Trainerが評価を行う際、eval_datasetに含まれる各サンプルがモデルによって予測され、その予測結果がcompute_metrics関数の引数として渡されます。その際、eval_predには (logits, labels) のタプルが渡されます。ここで、logitsはモデルの出力であり、labelsは真のラベルです。

python
Copy code
def compute_metrics(eval_pred):
    logits, labels = eval_pred
    # 以下略
したがって、ユーザーがTrainerを使ってモデルを評価するときには、eval_datasetに含まれる各サンプルには元々真のラベルが含まれている必要があります。通常、データセットの各サンプルには"label"というキーでアクセスでき、その値が真のラベルです。例えば、データセット内の各サンプルが以下のような形式を持っていると仮定します：

python
Copy code
{'input_ids': ..., 'attention_mask': ..., 'label': 1}
この場合、compute_metrics関数では labels は各サンプルの 'label' キーにアクセスすることで得られます。
```

この説明だと、キーを'label'に設定しておけばその列が真のラベルに対応していることになるということでよい?

Trainerの挙動の説明
https://qiita.com/nipo/items/44ce3aaf6acd4e2649d1

この記事だけだと疑問は解決できないけど、実装する際に参考になる。

取り組み方はこの記事を参考にする
https://note.com/currypurin/n/n6a3c2bfd27c0#9LXvD




参考
過去のLLMコンペの解法まとめ
https://zenn.dev/yume_neko/articles/7347ba6b081e93


