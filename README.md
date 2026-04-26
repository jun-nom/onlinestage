# オンライン会場の構造とMiro URL差し替え方法

# オンライン会場の構造

## 概要

2022年と2023年はオンライ会場参加者にmiroのURLを案内していましたが、2024年はmiroをHTML内に置いて、そのHTMLページへのURL（h[ttps://onlinestage.researchconf.jp/](https://onlinestage.researchconf.jp/)）を案内する形をとりたいと思います。

miroをHTML内に置く理由は、以下のとおりです。

- miro会場で予期せぬ不具合が起きた時のオペレーションを簡単にしたい
- miro会場が落ちた時もブラウザ画面上に案内を出せるようにしたい
- 「Googleアナリティクスを設置する」「スマホからの訪問者はURLを分ける」のようなカスタマイズを可能としたい

詳細については、以下に書いております。

https://miro.com/app/board/uXjVN79z80k=/?moveToWidget=3458764582847257383&cot=14

- さらに細かいメモ：
    - なぜiframeという形をとったか。redirectで良くない？という点について
        - Miroがアクセス過多になった時に、URL差し替えて「リロードしてください」と案内するつもりでいた。が、実際にはMiro URLを差し替えないといけないほどの事態にはならない。同時接続200くらいまでは耐えられそう。（これまでの最大同時接続数は186）
            - なので、redirectの形にしても特に問題はない。

**なお、本ドキュメントで説明する構成にすることは、マストではありません。**

**「こうしておいた方が便利」程度のものですので、この構成を採用せず、Miro会場のURLをそのままオンライン参加者にアナウンスしても特に問題はありません。**

## HTMLデータ設置と公開

githubのレポジトリ（https://github.com/researchconf/onlinestage）にデータを設置します。

github上でプッシュすると、https://onlinestage.researchconf.jp/ というURLで公開されます。

（Netrifyというサービスを使っています。）

# Miro会場の差し替えについて

## Miro会場を差し替えるシチュエーション

主に、「アクセス過多でmiro会場が重い（固まる）」という状況にて、予備のMiro会場へとアクセス先を差し替えることを想定しています。

他、何らかデータが破損する、機能に不具合が生じるといった、予期しない事態が起きる可能性があります。原因や解決策がわかっていたとしても、暫定対策として「miro会場を丸ごと差し替える」を速やかに行えることが望ましいです。

## Miro会場URL差し替え方法

### ざっくり

githubアカウントで[レポジトリ](https://github.com/researchconf/onlinestage)にアクセスして、「[__miroframe.html](https://github.com/researchconf/onlinestage/blob/main/__miroframe.html)」に書かれたURLを修正してプッシュします。

プッシュすると約1分後に、https://onlinestage.researchconf.jp/ に編集内容が反映されます。

### 詳細手順（準備）

1. [githubアカウントを用意](https://docs.github.com/ja/get-started/start-your-journey/creating-an-account-on-github)する（元々持っていればそれを使うでOK）
2. 野村へアカウント情報（github IDと登録メールアドレス）を伝える
3. （野村がアカウント権限付与の対処をし次第、データが編集可能になる）

**※ 注意：**

- MiroのURLはアドレスバーからコピペするのでなく、iframe貼り付け用のURLを使用すること（[参照リンク](https://aslead.nri.co.jp/products/miro/column/miro-use-iframe.html)）

### 詳細手順（編集と確認）

1. [レポジトリ](https://github.com/researchconf/onlinestage)（https://github.com/researchconf/onlinestage）にアクセス
2. 「[__miroframe.html](https://github.com/researchconf/onlinestage/blob/main/__miroframe.html)」をクリック

<img width="1376" height="883" alt="image" src="https://github.com/user-attachments/assets/e7ee46c3-035b-4d35-bf7e-61704bed306a" />


3. 鉛筆アイコンをクリック

<img width="1375" height="877" alt="image" src="https://github.com/user-attachments/assets/de12c24d-200d-4eeb-a9f7-cde8c8df5166" />


4. ファイル内容を編集する画面になりますので、内容のURL部分（src属性の中身）を編集します（書かれているURLを差し替え）

<img width="1379" height="883" alt="image" src="https://github.com/user-attachments/assets/e18f94da-7078-4b34-9c48-942fb2544633" />

5. 「Commit changes…」をクリック

<img width="1377" height="882" alt="image" src="https://github.com/user-attachments/assets/7e947e01-dd36-40d2-8aad-ca89bfb6b5c3" />

6. 「Commit changes」をクリック
    
    （messageとかdescriptionとかは気にしなくていいです）
    
<img width="1371" height="871" alt="image" src="https://github.com/user-attachments/assets/2c668e01-939e-434b-ad4c-1078d91e323a" />


7. Commit changesをしたら更新完了です。（3の画面に戻ります）
8. 1分程度経過後、https://onlinestage.researchconf.jp/ に編集結果が反映されます。

<img width="1033" height="826" alt="image" src="https://github.com/user-attachments/assets/f2fd1975-0cec-40ab-bf6c-1d53a4cfc234" />

5分とか待っても更新されないようなら、何か作業をミスして更新できていない可能性が高いです。

ーーーーー

なお、githubでは更新履歴は全て保存されますので、何か失敗をしてデータを壊してしまっても、野村まで連絡いただければすぐに巻き戻しますので、githubに慣れていなくても気負わず作業していただけると幸いです。
