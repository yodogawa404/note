# cf-sx3にarchを入れた

## 詰まったところ

### 画面の照度調節

``xf86-video-intel``をpacmanなどでインストール、  
``/etc/default/grub``を以下のように編集後、``grub-mkconfig -o /boot/grub/grub.cfg``。  
```diff
- GRUB_CMDLINE_LINUX_DEFAULT="loglevel=3 quiet"
+ GRUB_CMDLINE_LINUX_DEFAULT="loglevel=3 quiet acpi_backlight=legacy acpi_osi="
```

### タッチパッドでのエッジスクロール

``xf86-input-synaptics``をインストールすると、  
xfceの設定(マウスとタッチパッド→タッチパッド→スクロールモード)で変更できた。  

### スピーカー

[kapper氏のツイート](https://twitter.com/kapper1224/status/1210856500131811328)を参考にした。  
自分の環境だとサウンドカードの番号が違ったので一応書いておく。  
``alsamixer``コマンドで、F6を押すとサウンドカードの一覧が出てくるので、  
HDA Intel PCHと書かれた番号をメモ。  
``amixer -c 上述の番号 sset Headphone 100%``のように実行すると音が出た。  
尚、なぜか自分の環境だとxfceの自動起動に入れても有効にならなかったため、  
aliasを使って都度コマンドを実行している。

