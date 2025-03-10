# アノテーションリプライ

アノテーションリプライ機能は、手動編集されたアノテーションを通じて、アプリケーションにカスタマイズされた高品質なQ&Aリプライ能力を提供します。

適用シーン：

* **特定分野のカスタマイズ回答：** 企業や政府などのカスタマーサービスやナレッジベースQ&Aのシーンで、特定の問題に対してシステムが明確な結果を提供することを望む場合、特定の問題についてカスタマイズされた出力結果が必要です。例えば、特定の問題に対する「標準回答」や、特定の問題に対する「回答不可」の設定などが挙げられます。
* **POCやデモ製品の迅速なチューニング：** プロトタイプ製品を迅速に構築する際に、アノテーションリプライを通じて実現されたカスタマイズ回答は、Q&Aの生成結果の予期を効率的に向上させ、顧客満足度を高めることができます。

アノテーションリプライ機能は、LLM (大規模言語モデル) の生成プロセスをスキップし、RAG (Retrieval-Augmented Generation) の生成幻覚問題を回避するための別の検索強化システムを提供するものです。

### 使用プロセス

1. アノテーションリプライ機能を有効にすると、LLMの対話リプライ内容に対してアノテーションを行うことができます。LLMがリプライした高品質な回答を直接アノテーションとして追加することもできますし、必要に応じて高品質な回答を手動で編集することもできます。これらの編集されたアノテーション内容は永続化保存されます。
2. ユーザーが再度類似の質問をした場合、その質問をベクトル化し、類似するアノテーションをクエリします。
3. マッチング項目が見つかった場合、そのアノテーションに対応する回答を直接返し、LLMやRAGのプロセスを経由せずにリプライします。
4. マッチング項目が見つからなかった場合、質問は通常プロセスを継続します（LLMやRAGに渡されます）。
5. アノテーションリプライ機能をオフにすると、システムはアノテーションからのマッチングリプライを継続して行いません。

<figure><img src="https://assets-docs.dify.ai/dify-enterprise-mintlify/jp/guides/annotation/7bebcf85d52f65d5649956f47ed33d43.png" alt="" width="563"><figcaption><p>アノテーションリプライの流れ</p></figcaption></figure>

### 提示詞編成でアノテーションリプライを有効にする

「アプリケーション構築->機能追加」からアノテーションリプライのスイッチを有効にします：

<figure><img src="https://assets-docs.dify.ai/dify-enterprise-mintlify/jp/guides/annotation/b467da1fbaa9beb22cfb2a987f51f653.png" alt=""><figcaption><p>提示詞編成でアノテーションリプライを有効にする</p></figcaption></figure>

有効にする際には、まずアノテーションリプライのパラメータを設定する必要があります。設定可能なパラメータには次のものがあります：スコア閾値と埋め込みモデル

**スコア閾値**：アノテーションリプライのマッチング類似度閾値を設定するために使用されます。閾値スコアを超えるアノテーションのみがリコールされます。

**埋め込みモデル**：アノテーションテキストをベクトル化するために使用され、モデルの切り替え時には再度埋め込みが生成されます。

保存して有効にすると、この設定は直ちに有効となり、システムはすべての保存されたアノテーションに対して埋め込みモデルを利用して埋め込みを生成し保存します。

<figure><img src="https://assets-docs.dify.ai/dify-enterprise-mintlify/jp/guides/annotation/a2c7b82a4f25a96fcdf68c807fb96812.png" alt=""><figcaption><p>アノテーションリプライのパラメータ設定</p></figcaption></figure>

### 会話デバッグページでアノテーションを追加する

デバッグおよびプレビューページでモデルのリプライ情報に直接アノテーションを追加または編集できます。

<figure><img src="https://assets-docs.dify.ai/dify-enterprise-mintlify/jp/guides/annotation/e064e3dcca3f04e16f5269b169820d2d.png" alt=""><figcaption><p>アノテーションリプライを追加する</p></figcaption></figure>

必要な高品質リプライに編集して保存します。

<figure><img src="https://assets-docs.dify.ai/dify-enterprise-mintlify/jp/guides/annotation/b79aabe6e9b336e26ca409a49526501e.png" alt=""><figcaption><p>アノテーションリプライを編集する</p></figcaption></figure>

同じユーザー質問を再度入力すると、システムは既に保存されたアノテーションを使用してユーザー質問に直接リプライします。

<figure><img src="https://assets-docs.dify.ai/dify-enterprise-mintlify/jp/guides/annotation/810f640d184227f4918ee197ff906203.png" alt=""><figcaption><p>保存されたアノテーションを通じてユーザー質問にリプライする</p></figcaption></figure>

### ログとアノテーションでアノテーションリプライを有効にする

「アプリケーション構築->ログとアノテーション->アノテーション」からアノテーションリプライのスイッチを有効にします：

<figure><img src="https://assets-docs.dify.ai/dify-enterprise-mintlify/jp/guides/annotation/c74951765f078392924da901008eb815.png" alt=""><figcaption><p>ログとアノテーションでアノテーションリプライを有効にする</p></figcaption></figure>

### アノテーションバックエンドでアノテーションリプライのパラメータを設定する

アノテーションリプライで設定可能なパラメータには次のものがあります：スコア閾値と埋め込みモデル

**スコア閾値**：アノテーションリプライのマッチング類似度閾値を設定するために使用されます。閾値スコアを超えるアノテーションのみがリコールされます。

**埋め込みモデル**：アノテーションテキストをベクトル化するために使用され、モデルの切り替え時には再度埋め込みが生成されます。

<figure><img src="https://assets-docs.dify.ai/dify-enterprise-mintlify/jp/guides/annotation/5bbd94402452e3f4ecc29eb398591585.png" alt=""><figcaption><p>アノテーションリプライのパラメータを設定する</p></figcaption></figure>

### アノテーションQ&Aペアを一括インポートする

一括インポート機能内で、アノテーションインポートテンプレートをダウンロードし、テンプレート形式に従ってアノテーションQ&Aペアを編集します。編集が完了したら、一括インポートします。

<figure><img src="https://assets-docs.dify.ai/dify-enterprise-mintlify/jp/guides/annotation/ad6497dbe8c93fe9988cf76775434a7c.png" alt=""><figcaption><p>アノテーションQ&Aペアを一括インポートする</p></figcaption></figure>

### アノテーションQ&Aペアを一括エクスポートする

アノテーション一括エクスポート機能を通じて、システム内に保存されたすべてのアノテーションQ&Aペアを一度にエクスポートできます。

<figure><img src="https://assets-docs.dify.ai/dify-enterprise-mintlify/jp/guides/annotation/4d80d0a9b8056711a2dcdf664c19e840.png" alt=""><figcaption><p>アノテーションQ&Aペアを一括エクスポートする</p></figcaption></figure>

### アノテーションリプライのヒット履歴を確認する

アノテーションヒット履歴機能内で、すべてのヒットしたアノテーションの編集履歴、ヒットしたユーザー質問、リプライ回答、ヒットソース、マッチング類似度スコア、ヒット時間などの情報を確認できます。これらのシステム情報に基づいて、アノテーション内容を継続的に改善することができます。

<figure><img src="https://assets-docs.dify.ai/dify-enterprise-mintlify/jp/guides/annotation/26b6c37dcff225201ea5b4fb712b2d4d.png" alt=""><figcaption><p>アノテーションリプライのヒット履歴を確認する</p></figcaption></figure>