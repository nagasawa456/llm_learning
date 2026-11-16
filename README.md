# llm_learning

書籍『つくりながら学ぶ！LLM自作入門』（Sebastian Raschka 著／マイナビ出版）を参考に、
ChatGPT のような大規模言語モデル（LLM）を **PyTorch で一から実装しながら** 仕組みを学んでいるリポジトリです。

AI をブラックボックスとして使うだけでなく、
「文章がどのように数値に変換され、どのように次の単語が予測されるのか」を
自分でコードを書いて確かめることを目的としています。

## 使用技術

- Python
- PyTorch
- Jupyter Notebook
- tiktoken（BPE トークナイザ）

## 進捗

| 章 | 内容 | Notebook | 状態 |
|---|---|---|---|
| テキストデータの処理 | 文章をトークンに分割し、トークン ID に変換する | [tokenizer.ipynb](study_llm/tokenizer.ipynb) | ✓ 完了 |
| 埋め込み | トークン埋め込み・位置埋め込みで、単語と語順をベクトルで表す | - | ✓ 完了 |
| Attention 機構 | Self-Attention、Causal Attention、Multi-Head Attention | - | ✓ 完了 |
| GPT モデルの実装 | Transformer ブロックを組み合わせてモデルを作る | - | ・ 取り組み中 |
| 事前学習 | ラベルのないデータでモデルを学習させる | - | - 予定 |
| ファインチューニング | 分類タスク・指示応答へのファインチューニング | - | - 予定 |

## 学んだこと（抜粋）

- **トークン化**：文章を単語や記号に分け、語彙をもとに ID の列に変換する。未知語には BPE（バイトペア符号化）で対応する
- **埋め込み**：トークン ID をベクトルに変換し、さらに「何番目の単語か」を表す位置埋め込みを足すことで、語順の情報をモデルに渡す
- **Self-Attention**：各単語が文中のほかの単語にどれだけ注目するかをスコアとして計算し、softmax で正規化した重みで情報を集める。クエリ・キー・バリューの重み行列は学習によって調整される
- **Causal Attention**：次の単語を予測するときに未来の単語を見ないよう、マスクをかけて前の単語だけに注目させる
- **Multi-Head Attention**：複数の Attention を並列に計算し、異なる観点から単語どうしの関係をとらえる

## 構成

```
llm_learning/
├── README.md
└── study_llm/
    └── tokenizer.ipynb   # トークナイザの実装
```

## 参考

- Sebastian Raschka 著『つくりながら学ぶ！LLM自作入門』マイナビ出版
- 書籍のサンプルコード：https://github.com/rasbt/LLMs-from-scratch
