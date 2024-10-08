# BadStore.net ユーザーマニュアル

この日本語ユーザーマニュアルはChatGPTを利用して下記を日本語したものです。  
apache2\htdocs\BadStore_net_v1_2_Manual.pdf

翻訳に誤りがあるかどうかなどは確認しておりません。

--- 

バージョン 1.2

2005年2月1日

© 2005 Kurt R. Roemer

## BadStore.net への更新と改善リクエスト

BadStore.netは、定期的に新しい機能を導入し、さらにバグを増やすために更新されます。BadStore.netの最新バージョンに関する情報は、[www.badstore.net](http://www.badstore.net)
で確認できます。

BadStore.netは、以下によって開発され、維持管理されています。  
Kurt R. Roemer, CISSP  

最高セキュリティ責任者（CSO）  
NetContinuum, Inc.  
847-548-5390（オフィス）  
kroemer@netcontinuum.com  
kurt_roemer@yahoo.com

BadStore.netへの改善リクエストを提出するには、件名に"BadStore.net Enhancement Request"
と記入し、改善内容とその有用性を説明してkroemer@netcontinuum.comへメールを送信してください。技術的側面、ユーザビリティ、ドキュメントに関する改善リクエストも歓迎します。

## クレジットと感謝

NetContinuum, Inc.に対し、BadStore.netの開発を支援し、ダウンロードサイトをホスティングしていただいたことに感謝します。また、Trinuxのメンテナンスを続けているMatthew
Franzにも感謝します。

---

## 目次

- [BadStore.net への更新と改善リクエスト](#badstorenet-への更新と改善リクエスト)
- [クレジットと感謝](#クレジットと感謝)
- [1. BadStore.net へようこそ！](#1-badstorenetへようこそ)
    - [1.1 BadStore.net とは？](#11-badstorenetとは)
    - [1.2 BadStore.net を入手する場所](#12-badstorenetの入手方法)
    - [1.3 BadStore.net の目的](#13-badstorenetの目的)
    - [1.4 BadStore.net で提示されている脆弱性](#14-badstorenetで提示される脆弱性)
- [2. インストール](#2-インストール)
    - [2.1 BadStore.net のインストール](#21-badstorenetのインストール方法)
    - [2.2 BadStore.net のシステム要件](#22-badstorenetのシステム要件)
    - [2.3 ネットワーク構成](#23-ネットワーク構成)
    - [2.4 さらなる情報：アプリケーションセキュリティ情報とツールのリンク](#24-その他の情報アプリケーションセキュリティ情報およびツールのリンク)
- [3. 重要な免責事項](#3-重要な免責事項)
- [4. チートシート](#4-チートシート)
- [5. ライセンス](#5-ライセンス)
    - [5.1 GNU 一般公衆利用許諾契約書（GPL）](#51-gnu一般公衆利用許諾契約書gpl)
    - [5.1.1 序文](#511-序文)
    - [5.1.2 条項](#512-コピー配布変更の条件)
    - [5.1.3 修正](#保証の否認)
- [6. BadStore.net の変更履歴](#6-badstorenet-変更履歴)

---

## 1. BadStore.netへようこそ！

### 1.1 BadStore.netとは？

BadStore.netは、デモンストレーション、セキュリティトレーニング、およびテストを目的とした、脆弱性のあるアプリケーションです。BadStore.netは、イントラネット、エクストラネット、およびインターネットに公開されている多くのアプリケーションに存在する一般的な脆弱性を示すために開発されました。  
多くのWebアプリケーションの設計、運用、セキュリティを担当する人々は、これらのアプリケーションを侵害するために利用可能なさまざまな攻撃を見たことがなく、またそれらからアプリケーションを保護する方法を知りません。

BadStore.netは、Trinuxオペレーティングシステム上で動作するブータブルCDとして提供され、Apache Webサーバ、CGI（Common Gateway
Interface）アプリケーション、およびMySQLのフル実装を含んでいます。これは、標準的なコーディング方法を使用した完全な機能を持つアプリケーションであり、シミュレーションではありません。

BadStore.netを実行するには、ホストマシンにBadStore.netのCDを挿入し（インストールとシステム要件のセクションを参照してください）、CDから起動してください。BadStore.netは、Webブラウザからアクセスできるネットワークサーバとして起動します。また、オプションとして、BadStore.netはVMWareのような仮想環境でも使用できます。再起動すると、デフォルトの設定が自動的にリセットされます。ハッキングが成功した後も再構築は不要です。

BadStore.netは、現在、英語版および日本語版で提供されており、GNU General Public Licenseの条件でリリースされています。

### 1.2 BadStore.netの入手方法

BadStore.netの現在のバージョンは、[www.badstore.net](http://www.badstore.net)
のプラットフォームに応じたリンクからダウンロードできます。BadStore.netはISOイメージとして提供されており、CDに焼くことが可能です。

### 1.3 BadStore.netの目的

多くの情報セキュリティ専門家やビジネス関係者は、アプリケーションセキュリティの責任を持ちながら、脆弱性がビジネスに与える影響を実際に「見た」ことがありません。BadStore.netはこれらの脆弱性を示し、攻撃とそのビジネスへの影響を明確に示すことで、セキュリティ意識の向上、脆弱性の発見、セキュリティトレーニング、セキュリティテスト、および是正策の決定を支援します。

### 1.4 BadStore.netで提示される脆弱性

BadStore.netアプリケーションプラットフォームには、アプリケーションや環境を攻撃にさらす危険な脆弱性が含まれています。BadStore.netは、ラボやテスト環境でのみ使用する必要があり、絶対に本番環境にインストールしてはなりません。BadStore.netには、以下のセキュリティ脆弱性が含まれています。

- クロスサイトスクリプティング（XSS）
- SQLインジェクション
- コマンドインジェクション
- クッキー/セッションのポイズニング
- パラメータ/フォームの改ざん
- バッファオーバーフロー
- ディレクトリトラバーサル/強制ブラウジング
- クッキーのスヌーピング
- ログの改ざん
- エラーメッセージの傍受
- サービス拒否（DoS）

これらの脆弱性により、ハッカーはアプリケーション、Webサーバ、SQLデータベース、アプリケーションロジック、オペレーティングシステム、そして機密データを完全に掌握する能力を得る可能性があります。

詳細については、[www.netcontinuum.com/welcome/threats](http://www.netcontinuum.com/welcome/threats)
で「21種類のアプリケーション脅威」に関する情報を参照してください。

---

## 2. インストール

### 2.1 BadStore.netのインストール方法

BadStore.netアプリケーションプラットフォームには、アプリケーションや環境を攻撃にさらす危険な脆弱性が含まれています。BadStore.netはラボやテスト環境でのみ使用する必要があり、絶対に本番環境にインストールしてはなりません。

BadStore.netは、CD-ROMから起動し、Trinux/Apacheサーバとして動作します。インストールは不要であり、PCのハードドライブには何もコピーされません。ただし、BadStore.netの脆弱性により、攻撃者がホストPCのハードドライブにアクセスできる可能性があります。したがって、BadStore.netは非本番環境でのみ使用することを強くお勧めします（詳細は免責事項を参照してください）。

BadStore.netはVMWareでも正常に動作します。

BadStore.netアプリケーションサーバが起動したら、以下のサイトにアクセスしてください。  
`http://serveripaddress/cgi-bin/badstore.cgi`

JavaScriptサポートがない場合は、以下のURLも使用可能です。  
`http://serveripaddress/cgi-bin/badstore.cgi`

また、クライアントの「hosts」ファイルにエントリを追加し、サーバ名でアクセスすることもできます。

### 2.2 BadStore.netのシステム要件

BadStore.netはクライアント/サーバシステムとして動作します。BadStore.netのCDは指定されたサーバシステムで起動し、クライアントシステムがWebブラウザを使用してネットワーク経由でBadStore.netアプリケーションにアクセスします。

以下はシステム要件です：

- Pentium 200MMX w/ 64MB RAM (またはそれ以上) を搭載したホストPC
- CD-ROMドライブ（PCはCDから起動できる必要があります）
- BadStore.netホストのネットワークアダプタがアクティブであること
- BadStore.netサーバとクライアントを接続するネットワーク（またはEthernetクロスオーバーケーブル）
- クライアントシステムにもアクティブなネットワークアダプタとWebブラウザが必要
- クライアントブラウザでクッキーが有効になっていること
- クライアントブラウザでJavaScriptのサポートが有効になっていること

### 2.3 ネットワーク構成

BadStore.netをテスト環境内で安全に保持するためには、クライアントとBadStore.netホスト間にクロスオーバーイーサネットケーブルを使用することをお勧めします。BadStore.netはラボやテスト環境でのみ使用し、絶対に本番環境にはインストールしないでください。

起動時、BadStore.netサーバはホストのネットワークアダプタにIPアドレスをDHCPで割り当てようとします。DHCPサーバが利用できない場合、BadStore.netはIPアドレスを割り当てずに起動します。この場合、以下のように
`ifconfig`を使用してアドレスを手動で割り当てます。

例：クラスC (/24) サブネットで10.10.100.52のアドレスを割り当てる場合：

```
ifconfig eth0 up 10.10.100.52 netmask 255.255.255.0 broadcast 10.10.100.255
```

対応しているEthernetアダプタのリストについては、Trinuxのドキュメントを参照してください。詳細は[http://trinux.sourceforge.net/network.html](http://trinux.sourceforge.net/network.html)
で確認できます。

### 2.4 その他の情報：アプリケーションセキュリティ情報およびツールのリンク

以下は、BadStore.netに関連するセキュリティツールおよび情報のリンクです：

| Class                  | クラス名             | 説明                                | リンク                                                                                                      |
|------------------------|------------------|-----------------------------------|----------------------------------------------------------------------------------------------------------|
| Security Tools         | ActiveState PERL | Windows向けのPERLプログラミング/ランタイム環境     | [http://www.activestate.com](http://www.activestate.com)                                                 |
| Security Tools         | Ethereal         | ネットワークプロトコルアナライザ                  | [http://www.ethereal.com](http://www.ethereal.com)                                                       |
| Security Tools         | HTTrack          | ウェブサイトのコピー                        | [http://www.httrack.com](http://www.httrack.com)                                                         |
| Security Tools         | John the Ripper  | パスワード評価ツール                        | [http://www.openwall.com/john/](http://www.openwall.com/john/)                                           |
| Security Tools         | Kiwi Syslog      | Windows用のSyslogデーモン               | [http://www.kiwisyslog.com](http://www.kiwisyslog.com)                                                   |
| Security Tools         | Knoppix          | セキュリティツール付きのブータブルLinuxディストリビューション | [http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)             |
| Security Tools         | Nessus           | セキュリティスキャナ                        | [http://www.nessus.org](http://www.nessus.org)                                                           |
| Security Tools         | Netcat           | TCP/IP接続ツール                       | [http://netcat.sourceforge.net](http://netcat.sourceforge.net)                                           |
| Security Tools         | Nikto            | Webアプリケーションセキュリティスキャナ             | [http://www.cirt.net](http://www.cirt.net)                                                               |
| Security Tools         | NMAP             | ネットワークマッパーおよび監査ツール                | [http://www.insecure.org](http://www.insecure.org)                                                       |
| Security Tools         | Paros            | Webプロキシ/評価ツール                     | [http://www.parosproxy.org](http://www.parosproxy.org)                                                   |
| Security Tools         | Putty            | Windows向けのTelnet/SSHクライアント        | [http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/) |
| Security Tools         | SSLDump          | SSLv3/TLSネットワークプロトコルアナライザ         | [http://www.rtfm.com/ssldump/](http://www.rtfm.com/ssldump/)                                             |
| Security Tools         | Trinux           | セキュリティツール付きのブータブルLinuxディストリビューション | [http://www.trinux.org](http://www.trinux.org)                                                           |
| Security Organizations | AVDL             | アプリケーション脆弱性記述言語                   | [http://www.avdl.org](http://www.avdl.org)                                                               |
| Recommended Vendors    | NetContinuum     | アプリケーションセキュリティ                    | [http://www.netcontinuum.com](http://www.netcontinuum.com)                                               |

---

## 3. 重要な免責事項

このセクションでは、BadStore.netの使用に関する重要な注意事項を説明します。

**自己責任で使用してください – 救助員は常駐していません！**

BadStore.netは、多くのイントラネット、エクストラネット、インターネットに公開されているアプリケーションに存在する一般的な脆弱性を示すために開発されました。そのため、BadStore.netアプリケーションプラットフォームには、アプリケーションや環境を攻撃にさらす危険な脆弱性が含まれています。

BadStore.netはラボやテスト環境でのみ使用する必要があり、絶対に本番環境にインストールしないでください。ご注意ください！このサイトは、一般的なHTML、CGI（PERL）、およびJavaScriptのコーディング技術を使用して開発されています。既存のフリーまたは商用アプリケーションとの類似点は純粋に偶然のものです。使用しているすべての画像はパブリックドメインであると信じられていますが、問題がある場合はNetContinuum,
Inc.のKurt R. Roemer (kroemer@netcontinuum.com)にご連絡ください。

このアプリケーションの使用に関して、いかなる保証もありません。

## 4. チートシート

このセクションでは、BadStore.netアプリケーションに存在する脆弱性の一部を紹介します。

BadStore.netにおける脆弱性の存在箇所を知りたい場合、以下を参考にしてください。

- `robots.txt`ディレクトリの公開 ([http://localhost/robots.txt](http://localhost/robots.txt))
- Apacheプラットフォーム攻撃
  - NessusやNiktoを実行してください。
- 検索およびログイン機能におけるSQLインジェクション 
  - 例：通常のユーザーとしてログインする際に、`joe' OR 1=1 OR 'mary` を試してください。
- サプライヤーログインにおけるブラインドSQLインジェクション 
  - 例：シングルクォート（`'`）、`OR 1=1`、`OR 1=1--` などのSQLコマンドを試して、失敗する様子を確認してください。  
  適切な組み合わせにヒットするまで続けてください。
- ゲストブック、URL、検索機能におけるクロスサイトスクリプティング（XSS）
  - 例：`<script>alert('これはXSS攻撃です！')</script>` を試してください。
- プロキシ、XSS、ブルートフォースによる資格情報の公開 
  - 例：プロキシを使用してBase-64でエンコードされたSSOIDクッキーをデコードする。
    `<script>alert(document.cookie)</script>`を試し、Brutusを使用してログインを強制する。
- パラメータ改ざんによるコマンドインジェクション
- クッキーおよび隠しフィールド改ざんによる権限昇格 
  - `Role`パラメータは何でしょうか？
- クッキーをデコードして機密情報を表示する能力 
  - プロキシを使用してください。
- URLパラメータによる「秘密の」管理者アクセス 
  - `?action=admin`をURLに追加してみてください。
- サプライヤーポータルへのリファラーヘッダー改ざん、クッキー、SQLインジェクションによるアクセス 
  - プロキシを使用してリファラーヘッダーおよびクッキーを改ざんし、SQLインジェクション技術を使用してフォームにログインすることを試してください。
- アプリケーションおよびプラットフォームに対するサービス拒否（DoS）
- 無料または割引商品を取得する能力 
  - プロキシを使用して`CartID`クッキーを改ざんしてください。
- サイトの改ざん
  - サプライヤーポータルからファイルをアップロードできます 
    - ディレクトリをトラバースできますか？
- MD5でハッシュ化されたパスワード
  - 多くは簡単に解読可能
  - John the Ripperを試してみてください。
- 個人情報クレジットカードを含む）の公開
  - 過去の注文および「秘密の管理者ポータル」において
- 既知のパスワードなしでログインする能力
  - SQLインジェクションおよびブルートフォースを試してください。
- 他のユーザーの注文や情報を閲覧する能力
  - プロキシを使用してクッキーを改ざんしてください。

既知のアカウント： `big@spender.com`  
パスワード： `money`

---

## 5. ライセンス

### 5.1 GNU一般公衆利用許諾契約書（GPL）

バージョン 2、1991年6月

著作権 © 1989、1991 フリーソフトウェア財団, Inc.  
59 Temple Place - Suite 330, ボストン, MA 02111-1307, USA

このライセンス文書の逐語的なコピーを誰でも作成し、配布することが許可されていますが、変更は認められていません。

#### 5.1.1 序文

ほとんどのソフトウェアのライセンスは、ソフトウェアを共有したり変更したりする自由を奪うために設計されています。それに対して、GNU一般公衆利用許諾契約書（GNU
General Public
License、GPL）は、ソフトウェアを共有したり変更したりする自由を保証するために設計されています。この一般公衆利用許諾契約書は、フリーソフトウェア財団のほとんどのソフトウェアおよび、それを使用することを決定したその他のプログラムに適用されます。  
（フリーソフトウェア財団の一部のソフトウェアには、GNUライブラリ一般公衆利用許諾契約書が適用されます。）あなたもこのライセンスを自分のプログラムに適用することができます。

我々が「フリーソフトウェア」と呼ぶとき、それは価格のことではなく、自由のことを指しています。我々の一般公衆利用許諾契約書は、次の自由を保証するために設計されています。

- フリーソフトウェアのコピーを自由に配布できること（このサービスに対して料金を請求することも可能です）。
- ソースコードを受け取るか、必要であれば入手できること。
- ソフトウェアを変更し、それを新しいフリーソフトウェアに使用できること。
- これらのことができるとわかっていること。

これらの権利を守るためには、誰かがこれらの権利を否定したり、放棄させたりすることを禁じる制限を設ける必要があります。これらの制限は、ソフトウェアを配布したり、変更したりする場合に一定の責任を伴います。

例えば、ソフトウェアのコピーを配布する場合（無料でも有料でも）、受取人に対して自分が持っているすべての権利を提供しなければなりません。また、ソースコードを提供するか、受け取れるようにすることが求められます。そして、これらの条件を受取人に示して、その権利を理解させる必要があります。

我々は、次の2つのステップであなたの権利を保護します。

1. ソフトウェアに著作権を設定する。
2. このライセンスを提供して、コピー、配布、および/または修正を合法的に許可する。

また、著者と我々を保護するために、誰もがフリーソフトウェアに対していかなる保証もないことを理解する必要があります。もしソフトウェアが他者によって変更され、配布された場合、受取人が元のソフトウェアでないことを理解することで、他者が引き起こした問題が元の著者の評判に悪影響を与えないようにします。

最終的に、どのフリープログラムも、ソフトウェア特許によって常に脅かされています。再配布者が個別に特許ライセンスを取得することでプログラムを独占的にする危険を回避するため、特許はすべての人が自由に使用できるか、全くライセンスされない必要があることを明確にしています。

### 5.1.2 コピー、配布、変更の条件

0. このライセンスは、著作権者によって「この一般公衆利用許諾契約書の条件で配布される」と表示されたプログラムや他の著作物に適用されます。以下で「プログラム」とは、そのようなプログラムや著作物を指し、「プログラムに基づく作品」とは、著作権法の下で、プログラムまたはその一部を含む著作物（逐語的または修正されたものを含む）を指します。翻訳も、制限なしに「修正」に含まれます。このライセンスの受け取り人は「あなた」とします。

コピー、配布、修正以外の行為は、このライセンスの範囲外です。プログラムを実行する行為は制限されておらず、プログラムの出力がプログラムに基づく作品である場合のみ、その出力はこのライセンスの適用を受けます。それが真実かどうかは、プログラムが行うことによって決まります。

1. あなたは、逐語的なコピーを、受け取ったときのプログラムのソースコードとして、いかなる媒体においても作成し、配布することができます。その場合、適切な著作権表示と保証の免責を含む表示を目立つ形で掲載し、このライセンスに言及するすべての通知を保持し、プログラムと共にこのライセンスのコピーを提供しなければなりません。また、あなたは、コピーを物理的に譲渡する行為に対して料金を請求することができ、さらに保証を提供することもオプションで可能です。

2. あなたは、プログラムのコピーを修正し、これに基づく作品を作成し、セクション1の条件に従ってこれを配布することができます。ただし、以下の条件も満たす必要があります。

a) あなたは、変更を加えたファイルに対して、変更したことと変更日を記載した目立つ通知を追加する必要があります。

b) プログラム全体またはその一部を含むか、プログラムに基づく作品を配布または公開する場合、それ全体を無償で第三者にライセンス供与する必要があります。

c) 修正されたプログラムが通常インタラクティブにコマンドを読み取る場合、通常の方法で起動されたときに、適切な著作権通知、保証がないことを告知する通知、およびこのライセンスのコピーをどのように入手できるかをユーザーに通知するメッセージを表示する必要があります。（例外として、プログラム自体がインタラクティブであっても、そのようなメッセージを通常表示しない場合、あなたのプログラムに基づく作品がそのメッセージを表示する必要はありません。）

これらの要件は、修正された作品全体に適用されます。もし、その作品の識別可能な部分がプログラムに基づいておらず、独立して分離された独自の著作物であると合理的に考えられる場合、これらのセクションの条件は、それらの部分には適用されません。しかし、同じ部分がプログラムに基づく作品の一部として配布される場合、その配布はこのライセンスの条件に従い、他のライセンシーに対しても全体において許可が適用されます。したがって、このセクションの意図は、完全にあなたが書いた作品に対する権利を主張したり、それを争うことではなく、プログラムに基づく派生作品または集合的作品の配布を制御する権利を行使することにあります。

さらに、プログラムに基づかない他の作品を、プログラム（またはプログラムに基づく作品）と一緒にストレージや配布メディアのボリュームに集約するだけでは、その作品をこのライセンスの範囲内に含めることにはなりません。

3. あなたは、セクション1および2の条件に従って、オブジェクトコードまたは実行形式でプログラムをコピーおよび配布することができます。さらに、以下のいずれかの条件を満たす必要があります。

a) それに対応する完全な機械可読のソースコードを提供する。これは、ソフトウェア交換に一般的に使用される媒体で配布され、セクション1および2の条件に従って配布されなければなりません。または、

b) 少なくとも3年間有効な書面によるオファーを提供し、物理的なソースコード配布のコストを超えない料金で、セクション1および2の条件に従って、ソースコードの完全な機械可読コピーを提供することを申し出る。または、

c) 受け取った情報として、対応するソースコードを配布するオファーを提供する。（このオプションは、非商業的な配布の場合のみ許可されます。）

ソースコードとは、作品の修正を行うための好ましい形式を意味します。実行可能な作品のソースコードとは、すべてのモジュールのソースコードに加えて、関連するインターフェース定義ファイルや、実行可能ファイルのコンパイルおよびインストールを制御するスクリプトを含むものです。ただし、特別な例外として、配布されるソースコードには、実行可能ファイルが動作するオペレーティングシステムの主要コンポーネント（コンパイラやカーネルなど）と通常一緒に配布されるものは含まれる必要はありません。

実行形式またはオブジェクトコードの配布が、特定の場所からのコピーを提供することで行われる場合、その場所からソースコードをコピーするための同等のアクセスを提供することも、ソースコードの配布と見なされます。

4. プログラムをコピー、変更、サブライセンス、または配布することは、このライセンスで明示的に許可されている場合を除き、できません。このライセンスに違反して行われたコピー、変更、サブライセンス、または配布は無効となり、あなたの権利は自動的に終了します。しかし、あなたからこのライセンスのもとで権利やコピーを受け取った第三者は、このライセンスの条件を完全に遵守している限り、彼らのライセンスは終了しません。

5. あなたは、このライセンスを受け入れる義務はありません。署名したわけではないからです。しかし、このライセンスが許可しない方法でプログラムを変更または配布する権限は、他にはありません。したがって、プログラム（またはプログラムに基づく作品）を変更または配布することによって、このライセンスを受け入れる意思を示し、そのすべての条件とともに、プログラムまたはその基づく作品のコピー、配布、または修正の権利を持つことになります。

6. プログラムを再配布するたびに、受取人は自動的に元のライセンサーから、プログラムのコピー、配布、または修正のライセンスを受け取ります。あなたは、このライセンスで付与される権利に対して、受取人にさらなる制限を課すことはできません。第三者によるこのライセンスの遵守を強制する責任はありません。

7. 裁判所の判決や特許侵害の申し立てなどにより（特許問題に限らず）、あなたに対してこのライセンスの条件に反する条件が課された場合、それらの条件はこのライセンスの条件からあなたを免除するものではありません。もし、同時にこのライセンスおよび他の関連する義務を満たすことができない場合、その結果として、プログラムを配布することはできません。例えば、特許ライセンスが、あなたを通じてプログラムを受け取るすべての人がロイヤリティフリーでプログラムを再配布することを許可しない場合、このライセンスを満たすためには、プログラムの配布を完全に中止する以外に選択肢はありません。

このセクションの一部が特定の状況下で無効または法的に強制不可能であるとされた場合でも、このセクションの他の部分は引き続き適用されることを意図しています。また、このセクション全体は他の状況でも適用されることを意図しています。

このセクションの目的は、あなたに特許やその他の財産権の侵害をさせたり、これらの権利の有効性を争わせることではなく、パブリックライセンスシステムの整合性を保護することにあります。このシステムを通じて配布される広範なソフトウェアに多くの人々が貢献しており、それに依存しているためです。著者/寄贈者が他のシステムを通じてソフトウェアを配布するかどうかを決定するのは著者/寄贈者次第であり、ライセンシーはその選択を課すことはできません。

このセクションは、このライセンスの他の部分の結果として考えられることを明確にするためのものです。

8. プログラムの配布および/または使用が、特許や著作権で保護されたインターフェースによって特定の国で制限される場合、このライセンスの下でプログラムを配布する著作権者は、その国を除外する明示的な地理的制限を追加することができます。この場合、このライセンスは、その制限を組み込んだものとして適用されます。

9. フリーソフトウェア財団は、一般公衆利用許諾契約書（GPL）の改訂版または新しいバージョンを時折発行することがあります。新しいバージョンは現在のバージョンと同様の精神に基づいていますが、新たな問題や懸念に対処するために詳細が異なる場合があります。各バージョンには識別可能なバージョン番号が付与されます。プログラムがこのライセンスの特定のバージョンに従うことを指定している場合、または「任意の後続バージョン」に従うことを指定している場合、あなたはそのバージョンまたはフリーソフトウェア財団によって公開された任意の後続バージョンの条件に従うオプションがあります。プログラムがこのライセンスのバージョンを指定していない場合、フリーソフトウェア財団によって公開された任意のバージョンを選択することができます。

10. あなたが、異なる配布条件を持つ他のフリーソフトウェアにプログラムの一部を組み込みたい場合、著者に許可を求めてください。フリーソフトウェア財団によって著作権が保護されているソフトウェアに関しては、フリーソフトウェア財団に書面で申請してください。我々は、例外を設ける場合があります。我々の決定は、フリーソフトウェアのすべての派生物のフリーな状態を維持するという目標と、ソフトウェアの共有と再利用を一般的に促進するという目標によって導かれます。

### 保証の否認

11. プログラムは無償でライセンスされています。そのため、適用される法律の範囲内では、プログラムに対していかなる保証もありません。著作権者および/または他の当事者は、プログラムを「現状のまま」提供し、明示または黙示を問わず、いかなる種類の保証も行いません。これには、商品性の黙示保証および特定目的への適合性の保証も含まれますが、これに限定されません。プログラムの品質および性能に関するすべてのリスクは、あなたが負うものとします。プログラムが欠陥を示した場合、そのすべての修理、修正、または訂正にかかる費用をあなたが負担することになります。

12. 適用される法律で必要とされない限り、または書面で同意されない限り、著作権者または本ライセンスに基づいてプログラムを修正および/または再配布することを許可された他の当事者は、いかなる損害に対しても責任を負いません。これには、データの損失、データの不正確さ、あなたまたは第三者が被った損害、またはプログラムが他のプログラムと正常に動作しなかったことによる損害などが含まれますが、これに限定されません。このような損害の可能性について、著作権者や他の当事者に通知されていた場合でも、責任はありません。

---

## 6. BadStore.net 変更履歴

- バージョン 1.0 – 2004年のRSAショーでのオリジナルバージョン
- バージョン 1.1 – 追加項目:
  - より多くのNIC（ネットワークインターフェースカード）をサポート
  - サプライヤーアップロードのリファラーチェック
  - `/cgi-bin/`内の`badstore.old`
  - `/icons/`ディレクトリにアイコンを追加
- バージョン 1.2 – CSI 2004でのバージョン発表
  - MySQLのフル実装
  - `index.html`でのJavaScriptリダイレクト
  - いくつかの主要フィールドでのJavaScript検証
  - マイアカウントサービス、パスワードリセットおよび回復機能
  - 数々の見た目の更新
  - スキャナーを検出する「Scanbot Killer」ディレクトリ構造
  - `favicon.ico`
  - 再起動せずにファイルやデータベースを元の状態にリセットする機能
  - データベース内の日付と時刻を動的に更新
  - 追加の攻撃手法
