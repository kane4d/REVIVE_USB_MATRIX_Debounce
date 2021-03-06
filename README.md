# REVIVE USB MATRIX チャタリング対策版（PID004B）
[REVIVE USB チャタリング対策版（PID004A）](https://github.com/ushui/REVIVE_USB_Debounce)のマトリクス入力対応版です。
## 使い方
基盤の組み立て方や配線などは下記を参考にしてください。  
URL: <http://a-desk.jp/modules/forum_module/index.php?cat_id=3> 

1. 上記URLからファームウェア書き込みソフト「HIDBootLoader.exe」をダウンロードする。  

2. このリポジトリから「[REVIVE_USB_MATRIX_Debounce_latest.zip](https://github.com/ushui/REVIVE_USB_MATRIX_Debounce/raw/master/REVIVE_USB_MATRIX_Debounce_latest.zip)」をダウンロードし、解凍する。  
「readme.txt」「REVIVE_USB_MATRIX_Debounce_CT.exe」「REVIVE_USB_MATRIX_Debounce_FW.hex」の3つのファイルが解凍される。  

3. 手持ちのREVIVE USBのショートピンをBOOTにしてPCへ接続する。  

4. 「HIDBootLoader.exe」を起動して「Open Hex File」ボタンから「REVIVE_USB_MATRIX_Debounce_FW.hex」を選択し、  
「Program/Velify」ボタンを押してREVIVE USBのファームウェアを書き換える。  
6. REVIVE USBのショートピンをBOOTから戻して再度PCへ接続する。  

7. 「REVIVE_USB_MATRIX_Debounce_CT.exe」を起動して好みの設定に変更する。  

## 設定ツールについて
「REVIVE USB MATRIX, Configuration Tool」にサンプリング周期と一致検出回数の設定項目を増やしたものです。  
当ファームウェア以外では動作しません。  
デフォルトでは「サンプリング周期＝10ms／一致検出回数＝3回」に設定していますが、必要であれば変更することができます（そのままでも使えます）。   

![REVIVE USB MATRIX Debounce, Configuration Tool](https://raw.githubusercontent.com/ushui/REVIVE_USB_MATRIX_Debounce/master/revive_usb_matrix_debounce_ct.png)  
### サンプリング周期
チャタリングノイズ除去の効果があります。  
1～174msまで設定可能で、その設定値ごとにスイッチのON/OFF読み出しを行います。  
長く設定すると長い間隔で読み出されるので、チャタリングが起こりにくくなる代わりに遅延が増加します。  
### 一致検出回数
ノイズ除去の効果があります。  
1～255回まで設定可能で、この回数分スイッチがONであれば正しい入力とみなします。  
ONからOFFになる時にも回数分OFFであることを確認します。  
大きく設定するとチャタリングノイズ除去の精度向上や外来ノイズの除去が期待できますが、サンプリング周期に比例して遅延が増加します。  
### 補足
どの程度の設定値にすればよいかは使用するスイッチ・設置環境・用途によるので何とも言えません。  
一般的なマイクロスイッチであればデフォルト値から変更の必要はないと思われます。  
設定値の決め方は、設定ツールからキーボードと適当なキーに設定し、メモ帳を開いてボタンを押してチャタリングが確認できれば数値を上げてみる程度でいいと思います。  
もちろん遅延を抑えたい場合は逆のことを行えばいいでしょう。
### 遅延について
遅延秒数は **サンプリング周期 * 一致検出回数 - (サンプリング周期 / 2)** でおおよそ求められます。  
## 動作環境について
設定ツールはWindows XP以降のOSで動作します。  
書き込み・設定をWindows上で行ってしまえば、MacやLinux/UNIX系のOSでも動作します。
## 開発環境・開発言語について
### ハードウェア
REVIVE USB (PIC18F14K50)
### ファームウェア
開発環境：MPLAB IDE 8  
開発言語：C
### ソフトウェア（設定ツール）
開発環境：Visual C# 2010 Express  
開発言語：C#
## ソースコードについて
「[Assembly Desk License](https://raw.githubusercontent.com/ushui/REVIVE_USB_MATRIX_Debounce/master/LICENSE)」ライセンスに準拠します。  
「REVIVE USB MATRIX チャタリング対策版」は「REVIVE USB MATRIX」及び「REVIVE USB MATRIX, Configuration Tool」を参考にして作成しました。作成者である「Bit Trade One, LTD」に感謝いたします。

***
2017/09/03 Markdown記法の一部誤り等を修正。曖昧だった表現等の校正。  
2017/01/22 遅延に関する記述の修正。  
2017/01/04 表現の修正と簡略化。  
2016/12/31 readme作成。
***
作成者： ushui（ゆーしゅい）  
Twitter: [@kaede_hrc](https://twitter.com/kaede_hrc)  
