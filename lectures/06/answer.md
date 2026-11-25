# 第6回 解答

## 演習

<!-- [tool call] の行は、表示された行をそのまま貼り付けてください。終わらなかった STEP は、空欄のままでかまいません。 -->

- STEP 1 のツールの名前： `glossary_search_glossary`

- STEP 2 の [tool call]：
    ```
    [tool call]   glossary_search_glossary({'query': '3レベル'})
    ```

- STEP 3 の [tool call]：
    ```
    [tool call]   fetch_fetch({'url': 'https://modelcontextprotocol.io/'})
    ```

- STEP 4 の [tool call]：
    ```
    [tool call]   aws_aws___search_documentation({'search_phrase': 'Amazon S3 バージョニング 概要', 'topics': ['general']})
    ```

- 気づき・疑問：
    - さまざまな外部ツールやサービスに簡単に連携できることがわかった

## 宿題

<!-- 基礎・実装・発展のどれか1つに取り組めば完了です。 -->

- 取り組んだレベル：基礎

- やったこと：`mcp_server.py` に `get_lecture_summary` ツールを追加した
- 結果：
    - ツールを追加できたことを確認した
        ```
        [glossary_get_lecture_summary]
        指定した回（1始まりの整数）の講義の要点を返す。
        
        「第3回では何を学ぶ？」のように、回の内容や関係を聞かれたときに使う。
        引数: {"lecture": {"title": "Lecture", "type": "integer"}}
        ```

    - 質問から新たに追加したツールが呼び出され出力されることを確認した
        ```
        --- trace ---
        [tool call]   glossary_get_lecture_summary({'lecture': 2})
        [tool return] glossary_get_lecture_summary -> # 第2回 ファインチューニングとLoRA

        ## この回のねらい

        - 事前学習とファインチューニングの違い、ファインチューニングが向く場面と向かない場面を理解する
        - LoRAの考え方を理解し、Google Colab上で小さなモデルを…
        [usage] 入力 5,942 tokens / 出力 312 tokens / モデル応答 2 回
        ```

- 気づき・疑問：
    - 入力内容に応じて異なるツールが使い分けられている点が面白いと思った