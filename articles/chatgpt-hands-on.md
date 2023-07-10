---
title: "LINE アプリで簡単に作れる AI チャットボット！ ChatGPT 連携"
emoji: "🌊"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["openai", "LINE"]
published: true
---

# 1. OpenAI の設定

## 1-1. アカウント作成

「[Create your account](https://platform.openai.com/signup)」画面にアクセスし、OpenAI のアカウントを作成  
![OpenAI 1](/images/chatgpt-hands-on/openai-01.png)

## 1-2. ログイン

「[Create your account](https://platform.openai.com/signup)」画面にアクセス後、「Log in」リンクをクリックし、ログイン画面を表示後、ログインを実施  
![OpenAI 2](/images/chatgpt-hands-on/openai-02.png)

## 1-3. 「API Keys」画面に遷移

右上の「Personal」をクリック後、「View API keys」をクリックし、「API kyes」画面に遷移  
![OpenAI 3](/images/chatgpt-hands-on/openai-03.png)

## 1-4. 「Create new secret key」ダイアログを表示

「+ Create new secret key」をクリックし、「Create new secret key」ダイアログを表示
![OpenAI 4](/images/chatgpt-hands-on/openai-04.png)

## 1-5. secret key の発行

「Name」に「hands-on」と入力し、「Create secret key」ボタンをクリック
![OpenAI 5](/images/chatgpt-hands-on/openai-05.png)

## 1-6. 「secret key」をコピー

「Create new secret key」ダイアログに表示された「コピー」ボタンをクリックし、「secret key」をコピーし、「Done」ボタンをクリック  
※コピーした secret key をテキストエディターにペーストしておいてください  
![OpenAI 6](/images/chatgpt-hands-on/openai-06.png)

# 2. LINE Messaging API の設定

## 2-1. LINE Business ID の作成

以下のリンクにアクセスし、LINE Business ID のアカウントを作成してください  
https://account.line.biz/login  
![LINE 01](/images/chatgpt-hands-on/line-01-01.png)

## 2-2. LINE Developers ID ログイン画面を開く

以下のリンクの「LINE アカウントでログイン」ボタンをクリックし、ログイン画面を開く  
https://account.line.biz/login?redirectUri=https%3A%2F%2Fdevelopers.line.biz%2Fconsole%2F  
![LINE 01](/images/chatgpt-hands-on/line-01-02.png)

## 2-3. ログイン

「LINE アカウントでログイン」をクリック後、「メールアドレス」「パスワード」を入力し、「ログイン」ボタンをクリック  
![LINE 02](/images/chatgpt-hands-on/line-02.png)  
※スマートフォンの LINE アプリ上で画面に表示された認証番号を入力する必要があります。

## 2-4. 「新規プロバイダー作成」ダイアログを表示

プロバイダーの「新規プロバイダー作成」ボタンをクリックし、新規プロバイダー作成ダイアログを開く  
![LINE 03](/images/chatgpt-hands-on/line-03.png)

## 2-5. 新規プロバイダーを作成

「プロバイダー名」に「hands-on」を入力し、「作成」ボタンをクリック  
![LINE 04](/images/chatgpt-hands-on/line-04.png)

## 2-6. 新規チャネル作成画面を開く

「Messaging API」をクリック  
![LINE 05](/images/chatgpt-hands-on/line-05.png)

## 2-7. 新規チャネルを作成

必須項目を入力して「作成」ボタンをクリックし、確認ダイアログを表示し、「OK」ボタンをクリック  
※確認ダイアログが 2 回表示されますが、中身を読んだ上で「確認」ボタンをクリック  
![LINE 06](/images/chatgpt-hands-on/line-06.png)
|入力項目|入力値|
|----|----|
|会社・事業者の所在国・地域|日本|
|チャネル名|hands-on|
|チャネル説明|ChatGPT hands-on|
|大業種|飲食店・レストラン|
|小業種|カフェ・喫茶店|
|メールアドレス|（個人のメールアドレスを入力してください）|
|LINE 公式アカウント利用規約 の内容に同意します|チェックボックス On|
|LINE 公式アカウント API 利用規約 の内容に同意します|チェックボックス On|

## 2-8. チャネル作成完了

チャネルの作成が完了  
![LINE 07](/images/chatgpt-hands-on/line-07.png)

## 2-9. 友達追加

「Messaging API 設定」タブをクリックし、QR コードを表示し、スマホの LINE アプリで友達追加をしておいてください  
![LINE 08](/images/chatgpt-hands-on/line-08.png)

## 2-10. 「応答設定」画面を開く

「LINE 公式アカウント機能 > 応答メッセージ > 編集」リンクをクリックし、「応答設定」画面を開く  
![LINE 09](/images/chatgpt-hands-on/line-09.png)

## 2-11. 「応答設定」

応答設定を実施後、画面を閉じてください  
![LINE 10](/images/chatgpt-hands-on/line-10.png)
|入力項目|入力値|
|----|----|
|チャット|Off|
|あいさつメッセージ|Off|
|Webhook|On|
|応答メッセージ|Off|

## 2-12. 「チャネルアクセストークン」の発行

「LINE Developers」画面の「Messaging API 設定」タブを開き、「チャネルアクセストークン > 発行」ボタンをクリック  
![LINE 11](/images/chatgpt-hands-on/line-11.png)

## 2-13. 「チャネルアクセストークン」のコピー

発行された「チャネルアクセストークン」をコピーして、テキストに貼り付けておいてください  
![LINE 12](/images/chatgpt-hands-on/line-12.png)

# 3. make の設定

## 3-1. make アカウントの作成

以下のリンクにアクセスし、make のアカウントを作成してください  
https://www.make.com/en/register  
![make 01](/images/chatgpt-hands-on/make-01.png)

## 3-2. make にログイン

以下のリンクにアクセス後、「Email」「Password」を入力し、「Sign in」ボタンをクリック  
https://www.make.com/en/login  
![make 02](/images/chatgpt-hands-on/make-02.png)

## 3-3. scenario の作成

「Create a new scenario」ボタンをクリックし、 「New scenario」画面を開く  
![make 03](/images/chatgpt-hands-on/make-03.png)

## 3-4. LINE application の追加

「+」ボタンクリック後、検索フォームに「LINE」を入力し、「LINE」を選択  
![make 04](/images/chatgpt-hands-on/make-04.png)

## 3-5. 「Watch Events」 の追加

「Watch Events」をクリック  
![make 05](/images/chatgpt-hands-on/make-05.png)

## 3-6. 「Webhook」 の追加

「Webhook」ダイアログの「Add」ボタンをクリック  
![make 06](/images/chatgpt-hands-on/make-06.png)

## 3-7. 「Webhook」 の作成

「Create a webhook」ダイアログの「Webhoook name」に「hands-on」と入力し、「Connection」の「Add」ボタンをクリック  
![make 07](/images/chatgpt-hands-on/make-07.png)

## 3-8. 「connection」 の作成

「Create a connection」ダイアログの「Connection name」に「hands-on」と入力し、「Channel Access Token」に【「チャンネルアクセストークン」のコピー】でコピーしたチャネルアクセストークンを貼り付けて「Save」ボタンをクリック  
![make 08](/images/chatgpt-hands-on/make-08.png)

## 3-9. 「webhook」 の作成

「Create a webhook」ダイアログで「Connection」に「hands-on」が設定されているのを確認し、「Save」ボタンをクリック  
![make 09](/images/chatgpt-hands-on/make-09.png)

## 3-10. 「Webhook address」のコピー

「LINE」ダイアログの「Copy address to clipboard」ボタンをクリックし、「address」をコピーし、テキストに貼り付けておいてください。貼り付けが終わったら「OK」ボタンをクリックして「LINE」ダイアログを閉じてください  
![make 10](/images/chatgpt-hands-on/make-10.png)

## 3-11. 「make」を一時保存

「Save」ボタンをクリックし、make を一時保存  
![make 11](/images/chatgpt-hands-on/make-11.png)

# 4. LINE から make の連携設定

## 4-1. Webhook 設定

「LINE Developers」画面の「Messaging API 設定」タブの「Webhook 設定 > 編集」ボタンをクリック後、入力欄に【「Webhook address」のコピー】でコピーしたアドレスを貼り付けて「更新ボタン」をクリック  
![make-line 01](/images/chatgpt-hands-on/make-line-01.png)

## 4-2. Webhook 検証

「make」画面で「Run Once」ボタンクリック後、「LINE Developers」画面に戻り「Messaging API 設定」タブの「Webhook 設定 > 検証」ボタンをクリックし、「成功」ダイアログが表示されることを確認  
「make」画面に戻り、LINE アイコンの右上に「1」が表示されることを確認  
「LINE Developers」画面に戻り「Messaging API 設定」タブの「Webhook 設定 > webhook の利用」ボタンを On に変更  
![make-line 02](/images/chatgpt-hands-on/make-line-02.png)
![make-line 03](/images/chatgpt-hands-on/make-line-03.png)
![make-line 04](/images/chatgpt-hands-on/make-line-04.png)
![make-line 05](/images/chatgpt-hands-on/make-line-05.png)

## 4-3. LINE よりメッセージ送信

「make」画面で再度「Run Once」ボタンクリック後、【友達追加】で追加したチャットボットアカウントに LINE でメッセージを送信し、「make」画面で LINE アイコンの右上に「1」が表示されることを確認  
![make-line 06](/images/chatgpt-hands-on/make-line-06.png)

# 5. make から openai の連携設定

## 5-1. module 追加

「make」画面で「LINE」アイコン横にカーソルを移し、表示された「+ Add another module」ボタンをクリック  
![make-openai 01](/images/chatgpt-hands-on/make-openai-01.png)

## 5-2. HTTP モジュール選択

検索フォームに「http」と入力し、「HTTP」モジュールを選択  
![make-openai 02](/images/chatgpt-hands-on/make-openai-02.png)

## 5-3. Make a request モジュール選択

ACTIONS より「Make a request」モジュールを選択  
![make-openai 03](/images/chatgpt-hands-on/make-openai-03.png)

## 5-4. HTTP モジュールの設定（その 1）

以下の値を入力  
![make-openai 04](/images/chatgpt-hands-on/make-openai-04.png)
|入力項目|入力値|
|----|----|
|URL|https://api.openai.com/v1/chat/completions|
|Method|POST|

## 5-5. HTTP モジュールの設定（その 2）

以下の値を入力  
![make-openai 05](/images/chatgpt-hands-on/make-openai-05.png)
|入力項目|入力値|
|----|----|
|Headers > item1 > Name|Content-Type|
|Headers > item1 > Value|application/json|
|Headers > item2 > Name|Authorization|
|Headers > item2 > Value|Bearer {OpenAI で発行した API キー}|

## 5-6. HTTP モジュールの設定（その 3）

以下の値を入力し、「OK」ボタンをクリック  
![make-openai 06](/images/chatgpt-hands-on/make-openai-06.png)
|入力項目|入力値|
|----|----|
|Body type|Raw|
|Content type|JSON (application/json)|
|Request content|{"model": "gpt-3.5-turbo","messages" : [{"role": "system","content": "あなたは大阪府箕面市森町中にある喫茶店「森のひととき」の店長です。常に明るく元気に丁寧に返信してください。お店の営業時間は AM9:00〜PM18:00。休業日は水曜日。受信メッセージに `SHINMACHI` が含まれる場合は返信内容に「クーポンをお知らせします！12345」を文末または文頭に含めてください。"},{"role": "user","content": "{{1.events[].message.text}}"}]}|
|Parse response|Yes|

## 5-7. openai へのメッセージ送信検証

「make」画面で「Run Once」ボタンクリック後、LINE からメッセージを送信し、「LINE」アイコン、「HTTP」アイコンの右上に「1」が表示されることを確認  
![make-openai 07](/images/chatgpt-hands-on/make-openai-07.png)

# 6. make から LINE の連携設定

## 6-1. module 追加

「make」画面で「LINE」アイコン横にカーソルを移し、表示された「+ Add another module」ボタンをクリック  
![make-line 10](/images/chatgpt-hands-on/make-line-10.png)

## 6-2. 「LINE > Send a Reply Message」の選択

「LINE > Send a Reply Message」を選択  
![make-line 11](/images/chatgpt-hands-on/make-line-11.png)

## 6-3. 「Send a Reply Message」の設定

以下の値を入力し、「OK」ボタンをクリック  
![make-line 12](/images/chatgpt-hands-on/make-line-12.png)
|入力項目|入力値|
|----|----|
|Connection|hands-on (hands-on)|
|Reply Token|{{1.events[].replyToken}}|
|Messages > item1 > Type|Text|
|Messages > item1 > Text|{{2.data.choices[].message.content}}|

## 6-4. openai アプリの送信検証

「make」画面で「Run Once」ボタンクリック後、LINE からメッセージを送信し、応答が LINE で返ってくることを確認
