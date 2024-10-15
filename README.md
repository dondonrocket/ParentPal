# ParentPal+
## **・アプリ概要**<br>
"ParentPal+"は子育てに悩む親が、同じ悩みを抱えた他の親達の経験や解決方法を知ることができるWebアプリ。（Laravel, Reactを使用）<br><br>
## **・アプリの目的**<br>
親の子どもに対する悩みを軽減し、子育ての質を向上させること。<br>
子どもに対する具体的な悩みを持つ親が、専門的なアドバイスや解決策を手軽に得られる環境を提供すること。<br>
子どもがどのような性格や行動パターンを持つのかを理解する手助けをし、親が子どもをより良く理解できるようにすること。<br>
<br>
## **1. 機能要件**<br><br>
### **1.1 悩み入力機能**<br>
機能概要:<br>
親が、たけのこちゃんとの対話を通じて、子どもに関する悩みを入力するインターフェース。<br>
親しみやすいキャラクター（たけのこちゃん）がガイドする。
自由記述のテキスト入力フィールド。
chatgptのAPIを使って、入力された子どものパターンを識別し、”子どもの姿”、”その時の特徴”、”子どもの思い”、”対応方法”、”他の保護者の悩み”を表示していく。<br>
詳細要件:
たけのこちゃんが柔らかい口調で質問を投げかける（複数のシナリオに対応）。
悩みの種類に応じた質問のパターン化（事前に用意された質問リスト）。
例: 「最近どんなことに困っているの？」「どんな行動が目立つかな？」
1.2 悩みの解析と質問生成機能
機能概要:
ChatGPTが親の入力した悩みを解析し、追加質問を生成する機能。

ChatGPTが入力テキストを解析して、より詳細な質問を自動生成。
質問例: 「その行動はいつから始まりましたか？」「どういう状況でその行動が目立ちますか？」
詳細要件:
ChatGPT APIを用いて、入力された悩みを解析し、適切なフォローアップ質問を生成。
質問の選定ロジック: 悩みの内容に応じて、行動の頻度、期間、試した対策などをヒアリングする。
1.3 子どものパターン生成機能
機能概要:
ChatGPTが親の悩みを基に、子どもの性格や行動のパターンを生成し、解決策を提案。

生成されたパターンは、親が抱えている悩みに基づいてカスタマイズされる。
解決策は子どものパターンに合わせて提供される。
詳細要件:
ChatGPT APIを用いて、入力された情報に基づく子どもの行動パターンを生成。
生成されたパターンには、親しみやすい説明と、実用的な解決策が含まれる。
例: 「この行動は、自己主張が強い子どもに見られる傾向があります。」
1.4 対話履歴管理機能
機能概要:
親とたけのこちゃん、ChatGPTとの対話の履歴を保存し、後から参照できるようにする。

対話内容はすべて保存され、必要に応じて履歴を確認できる。
詳細要件:
対話ログを自動保存し、親が過去のやり取りを振り返ることができる。
対話ログは時系列に整理され、重要なポイントにはマーカーがつく。
1.5 子どものパターンページ生成機能
機能概要:
対話の結果に基づき、個別の子どものパターンページが自動生成される。

生成されたページには、子どもの行動パターンの説明、解決策、関連投稿などが表示される。
詳細要件:
ChatGPTの解析結果から、自動的に子どものパターンページを生成。
パターンページには以下の要素が含まれる:
子どもの行動パターンの説明
解決策・アドバイス
関連する投稿（親同士の経験シェア）
2. 非機能要件
2.1 パフォーマンス要件
ChatGPT APIを活用するため、リアルタイムの応答速度を維持する。
ユーザーが快適に操作できるUI/UX設計を考慮し、遅延を最小限に抑える。
2.2 可用性
24時間稼働できるシステムとし、親がいつでも悩みを相談できる環境を提供。
サーバーの冗長化やバックアップを考慮して、システム障害時にも迅速な復旧が可能な体制を整える。
2.3 セキュリティ要件
ユーザーの悩みや対話の内容はすべて個人情報として取り扱い、データの暗号化を行う。
プライバシーポリシーを明確にし、ユーザーのデータが適切に管理されることを保証する。
2.4 スケーラビリティ
ユーザー数の増加に伴い、ChatGPT APIのリクエスト負荷を考慮してスケールアップ可能なインフラを設計する。
将来的な新機能追加にも対応できるよう、拡張性のあるシステム設計を行う。
3. 技術要件
3.1 開発言語およびフレームワーク
フロントエンド: React (TypeScript)
バックエンド: Laravel (PHP)
データベース: MySQL/PostgreSQL
インフラ: Dockerを使用したコンテナ化
3.2 APIの使用
ChatGPT APIを使用して、対話解析、質問生成、パターン生成を実装。
APIリクエストの頻度制御を行い、コスト管理も含めたAPI呼び出しを最適化。
3.3 データ保存
対話履歴やユーザー情報はデータベースに安全に保存される。
データの取り扱いにはGDPRや日本のプライバシー保護法に準拠したセキュリティ対策を講じる。
4. ユーザーインターフェース要件
4.1 UI/UX
たけのこちゃんは、親しみやすいイラストやアイコンで表示される。
シンプルで直感的に操作できる対話形式のインターフェースを提供。
悩み入力後、すぐにChatGPTによる応答が開始され、タイムリーな対話が可能。
4.2 アクセシビリティ
色覚に配慮した配色、読みやすいフォントサイズ、音声入力対応を検討。
モバイルデバイスでもスムーズに利用できるレスポンシブデザイン。
5. 運用・保守要件
5.1 保守体制
ChatGPT APIのバージョンアップやメンテナンスに対応するための定期的なシステムチェックを実施。
バグ修正や機能改善のため、継続的なフィードバック体制を整える。
5.2 ユーザーサポート
FAQやヘルプページを用意し、親が使い方をすぐに理解できるようにする。
フォームやチャットサポートで問い合わせ対応が可能な仕組みを整備。
