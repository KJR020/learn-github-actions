# 学んだ事

## GitHub Actionsとは?
### Workflows
ワークフローは、一つ以上のジョブからなる処理プロセス

### イベント
ワークフローのトリガとなるイベント
リポジトリ内のアクティビィティ\
リポジトリにpull requestが作成された時、コミットがpushされた時、issueが開かれた時、\
また、スケジュールや REST API経由などのトリガを設定する

### ジョブ
処理の一まとまり。同一ランナー上で実行される\
ジョブは並列に実行される（非同期処理）\
ジョブの優先順位も付けらられる\
ジョブは、データを共有する

### アクション
リポジトリ上で実行される。複雑で頻繁に繰り返されるもの。\
自動化して標準化される需要や価値があるもの。(ライブラリのようなもの)\
ワークフローファイルに記載するコード量を減らせる


### ワークフローファイル
- name : GitHubのリポジトリに表示されるワークフロー名
- run-name : 
- on :　ワークフローのタイミング
- check-bats-version : jobの名前
- runs-on : ランナー,実行環境
- steps : 

```
name: learn-github-actions
run-name: ${{ github.actor }} is learning GitHub Actions
on : [push]
jobs:
    check-bats-version:
        runs-on: ubuntu-latest
        steps:
            - uses: actions/checkout@v4
            - uses: actions/setup-node@v3
              with:
                node-version: '20'
            - run: npm install -g bats
            - run: bats -v
```


bats : Bash Automated Testing System. Bashスクリプトのテスティングフレームワーク.
Bashスクリプトの動作を自動化してテストできる