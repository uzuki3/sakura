Introduction  
------------

<details open><summary>Policy</summary>
<ul>
<li>v2.3.2.0をベースに修正、機能追加を行っています
<li>他のエディタを参考にまねっこ
<li>使っていて気になった点をとりあえず修正してみる
</details>
    
<details open><summary>修正は以下の開発環境を基準に快適に動かせる範囲で行っています</summary>
<ul>
<li>Machine: Celeron 3215U 1.7GHz / Memory 8GB / Windows10 Home 1803
<li>Compiler: Visual Studio 2017 (v15.7.5)
</details>

<br>

Download  
--------
- v2.74 (2018/07/25) | [32-bit](http://nekomimix.jp/r/sakura-fix_2.74.zip) | [64-bit](http://nekomimix.jp/r/sakura-fix_2.74_64.zip)  
    - Merge sakura-editor/sakura, pull request #263 from m-tmatma/feature/share-mode-not-exclusive
    - Merge sakura-editor/sakura, pull request #267 from m-tmatma/feature/no-wrap-text-default
    - <del>Minor fixes  

<details><summary>Merge sakura-editor/sakura</summary>
<ul>
<li>pull request #263 from m-tmatma/feature/share-mode-not-exclusive
<li>pull request #267 from m-tmatma/feature/no-wrap-text-default
<li>pull request #137 from berryzplus/bugfix/fix_of_typeprop_import
<li>pull request #211 from beru/no_hwndProgress_when_bGrepRunning
<li>pull request #232 from m-tmatma/feature/copyright-2018
<li>pull request #125 from beru/file_loading_speed_up
<li>pull request #236 from yoshinrt/fixup_dogrep_localvar_init
<li>pull request #77 from beru/grep_speed_up
</details>

---

- sakura.keywordset.csv  
    [sakura.keywordset.csv](Publish/sakura.keywordset.csv) は強調キーワードに keyword フォルダのファイルを使用する定義ファイルです.  
    「sakura」の部分は実行ファイルと同じ名前で同じ場所に配置してください.  
    - このキーワードセットを使用した場合は 'sakura.ini' には書き出されなくなり, iniファイルの肥大化抑制にもなります.  
    - 使用しない場合はいつも通りの動作です (sakura.iniに書き込まれる)  

- keyword_pack.zip (2017/06/16)  
    キーワードセット集 patchunicode:#720 対応 [Download](Publish/keyword_pack.zip)  

※ 変更履歴はコミットログ([Link](https://github.com/niki/sakura/commits/master))を, ソースレベルで気になる人は my_config.h([Link](sakura_core/my_config.h)) を見てね.  


<br>

Changed  
-------

<details open><summary>ファイル/設定/機能</summary>
<ul>
<li>強調キーワードのセットファイル sakura.keywordset.csv の使用
<li>履歴を別ファイル ('sakura.recent')に出力
<li>起動時に存在しないファイル・フォルダ履歴を削除する
<li>多重オープンの許可 (Shiftを押しながらファイルのドロップ)
<li>タイプ別設定一覧の「追加」から任意のタイプを追加できるようにする
<li>デフォルト文字コードを UTF8にする
<li>カラー設定のインポートはカラー情報だけを適用させる
<li>履歴 (検索, 置換, Grep)の最大値を変更
</details>

<details open><summary>表示/編集</summary>
<ul>
<li>スクロールバーに検索結果とブックマーク, カーソル位置を表示:star:
<li>垂直, 水平スクロールの挙動をメモ帳の挙動と同じにする (縦:端でスクロール, 横画面端で半角16文字スクロール)
<li>行番号の表示切り替えマクロ追加 ('S_SwitchDispLineNumber()'):star:
<li>検索時に表示域が切り替わる場合カーソル行を中央に表示 (見やすくするため)
<li>タブ入力文字の切り替え機能 ('S_ChangeTabWidth()' マクロを修正, 負の値を設定で入力文字をタブと空白で相互に切り替え)
<li>行を中央揃えにする (行の間隔を上下に配分):star:
<li>半角スペースを '･' で表示 (Sublime Textみたいな)
<li>NBSPも半角スペースとして '×' で表示
<li>タブ文字を線のみで描画 (Sublime Textみたいな)
<li>キャレットの高さを行の高さにする (カーソル行アンダーライン非表示時のみ)
<li><del>キャレットの幅を入力タイプで変更する (半角:1px, 全角:2px)
<li>ブックマークを行番号左に縦線で表示する (背景色使用)
<li>変更行を行番号右に縦線で表示する (背景色使用)
<li>アンドゥ,リドゥの高速化
<li>EOFのみの行 (起動時とか)にも行番号を表示
<li>コメント行の背景カラーを改行以降もその色で描画
<li>空白, タブ, 改行, EOF, ノート線のカラーは現在のテキストカラーから自動で色付け
<li>数値の色付け判定を正規表現で行う
<li>選択範囲カラーは元のテキストカラーはそのまま使用し、背景カラーのみ使用する
<li>カーソル行アンダーラインを行番号から引っ張る
<li>偶数行背景はEOF以降は適用しない
<li>ノート線はEOF以降は適用しない
</details>

<details open><summary>UI</summary>
<ul>
<li>検索ダイアログを VisualStudio のような挙動にする:star:
<li>Grep フォルダの指定BOXを３つに増やし, 除外フォルダを別ボックスで指定できるようにする:star:
<li>タブをダブルクリックで閉じられるようにする:star:
<li>タブ選択のアクティブ化をマウス押下時に行いレスポンス向上
<li>モード取り消し時にダイアログ(検索やGrep,アウトライン解析など)にフォーカスがなくても閉じる
<li>Grep パターン変数を使用できるようにする (レジストリ 'HKEY_CURRENT_USER\Software\sakura-niki' への追加が必要です)
<li>Grep 条件テキストボックスのフォントを少し大きくする
<li>メインメニューは常にデフォルトを使用する (項目喪失回避, カスタマイズの需要がなさそうなため)
<li>置換ダイアログの置換後テキストに置換前テキストを設定
<li>正規表現検索のときに正規表現記号をクォート ('^abc$' を検索する場合 '\^abc\$' にする)
<li>ステータスバーのカスタマイズ (左クリックでメニュー表示、タイプ名表示など)
<li>タグファイル作成時にフォルダの初期値を 'tags', 'ctags.cnf' ファイルがあるところまで辿る
<li><del>「タブを閉じる」ボタンをグラフィカルにする
<li>リソース (ダイアログ)のフォントを 'MS Shell Dlg' へ変更
<li>変更, キーマクロ記録中のタブ名のカラーを変更
<li>フォルダ選択ダイアログを今風にする
<li>最近使ったファイル/フォルダ名が長い場合は短縮表示にする
<li>最近使ったファイル/フォルダ名にアクセラレータ文字を表示しない
<li>最近使ったファイルにファイルサイズを表示する
<li>タグジャンプ一覧の表示カラムを選別
<li>アウトライン解析ダイアログのドッキング時はコントロールカラーのままにする
<li>各種ダイアログを編集ウィンドウの中央に配置
</details>

<details open><summary>バグ:bug:(またはバグに近いモノ)の修正</summary>
<ul>
<li>検索マーク切り替え, インクリメンタルサーチの際に検索ダイアログの「正規表現」が影響を受けてしまうのを修正
<li>Grep「現在編集中のファイルから検索」をチェックした時の状態がほかに影響を与えてしまうので修正
<li>折り返しモードをトグルで切り替えたときに「折り返さない」が処理されていないのを修正
<li>太字装飾の文字列を選択したときに選択範囲カラーの装飾の影響を受けないように修正
<li>タブ表示, 間に選択タブがあると右側のエッヂがないバグを修正
<li>行番号が非表示でブックマークが表示のときブックマークは線で描画するように修正 (表示されていなかった)
<li>アウトライン解析ダイアログのツリーをダブルクリックで展開/縮小できるように修正
<li>ルールファイルを設定してアウトライン解析をするとデフォルトが逆順になっているのを修正
<li>行番号背景描画が行番号縦線をはみ出しているバグを修正
</details>

<details open><summary>その他</summary>
<ul>
<li>スクロールバーの更新頻度を少なくする
<li>ExtTextOutによる塗りつぶしをPatBltに変更
<li>WM_ERASEBKGNDの抑制
</details>

**<a name="patchunicode">マージ済みパッチ**  

- [patchunicode:#1047](https://sourceforge.net/p/sakura-editor/patchunicode/1047/) プロポーショナル版で変更された単語単位移動を戻す
- [patchunicode:#1006](https://sourceforge.net/p/sakura-editor/patchunicode/1006/) 改行文字部分とそれより後ろのキャレット移動に関して
- [patchunicode:#830](https://sourceforge.net/p/sakura-editor/patchunicode/830/) マクロの文字列コピーを減らす
- [patchunicode:#720](https://sourceforge.net/p/sakura-editor/patchunicode/720/) タイプ別設定の追加と強調キーワードの外部化


<br>
<br>

<img src="https://raw.github.com/wiki/niki/sakura/images/sakura_201707130016.png" width="75%" alt="検索マーク/検索ダイアログ">
<img src="https://raw.github.com/wiki/niki/sakura/images/sakura_201706041815.png" width="50%" alt="Grep">


<br>


Cregit  
------
+ サクラエディタ公式 https://sakura-editor.github.io/

---
(C) 2017,2018 Niki.
