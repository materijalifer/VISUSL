
	Macintoshでspwaveを使う場合の注意点について

音飛び
------

バージョン0.6.5までのspwaveをMac OS 9以下のMacで動作させた場合には，仮想メモリ
がオンになっていると，音飛びが顕著に発生することがありました．0.6.6以降では，
少し改善されたと思いますが，それでも発生する場合は，オーディオバッファーの
サイズを大きくするか，仮想メモリをオフにするかして下さい．オーディオバッファー
のサイズは，設定ダイアログの「サウンド」タブの「オーディオバッファー」の数値
で変更できます．また，再生時にカーソルの描画を行わないようにすることも効果が
ある場合があります．設定ダイアログの「サウンド」タブの「再生中にカーソルを
描画」をオフにして下さい．なお，音飛びが発生するからといってメモリー割り当て
を増やしても効果はないと思います．

また，現在のバージョンでは，メニューを表示したりウィンドウを移動したりすると
音声の再生が停止してしまうという問題点があります．ただし，Mac OS Xでは，一応，
この問題を解決することができます．Mac OS Xに関する下の説明をお読み下さい．


メモリー割り当て
----------------

Mac OS 9以下で，spwaveに割り当てられたメモリーが足りない場合は，ビープ音と
ともに終了してしまいます．特に，サンプリング周波数の変換などの処理で大量に
メモリーを消費しますので，注意して下さい．


Mac OS X
--------

Mac OS Xでは，Mac OS 9などと異なり，プリエンプティブスレッドが動作するように
なったため，メニューを表示させたりウィンドウを移動させても処理が停止しない
ようにすることができます．ただし，ときどき不安定になることがありますので
(OSの問題もあるように思います)，現在のバージョンについては，初期設定では
プリエンプティブレベルスレッドを使わないようになっています．

設定方法は，メニューバーから「編集」-->「設定...」を選択し，ダイアログが開いたら
「サウンド」タブをクリックし，下の方にある「低レベルスレッドを使用」をチェック
します．これでspwaveを再起動すればプリエンプティブスレッドを使うことができます．
なお，この設定項目は，Mac OS 9以下では現れません．

この場合，次のような問題が発生することがあります．まず，再生後や編集後に選択
できるはずのボタンが選択できなったり，表示が乱れたりすることがあります．特に，
ショートカットキーで操作を行った場合によく起こるようです．この場合は，他の
アプリケーションをアクティブにして，もう一度spwaveに戻ったり，メニューから
操作したりすると戻ることがあります．また，プリエンプティブスレッドを使用して
いる場合，再生中にウィンドウやダイアログを開いたりすると不安定になることが
まれにありますので，注意して下さい．


その他の注意点
--------------

- MP3のID3タグはバージョン1のみの対応となります．そのため，iTunesなどで作られる
  ID3タグのバージョン2のみを含むファイルでは情報が表示されません．

- Mac OS 9以下において，Ogg Vorbisの書き込みは，現時点ではクラッシュしてしまう
  ためパッケージに含めていません．

- Mac OS 8.Xにおいて，Lameを用いたMP3の書き込みは，クラッシュしてしまうため
  動作しないようにしてあります．


坂野秀樹（Banno Hideki）
E-mail: banno@itakura.nuee.nagoya-u.ac.jp
