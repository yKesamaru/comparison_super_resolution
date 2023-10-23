# 画像拡大マスター：超解像セットアップシリーズ④ 超画像モデルの比較

超解像シリーズは全部で4編書きます。
1.　MAX Image Resolution Enhancer
2.　GFPGAN
3.　VQFR
4.　1~3の比較

この超解像シリーズでは、いくつかの超解像技術をピックアップして、それぞれの環境構築方法を中心にご紹介します。

今回は、MAX Image Resolution Enhancer（SRGAN）, GFPGAN, VQFRの3つの超解像技術を比較します。

![](https://raw.githubusercontent.com/yKesamaru/comparison_super_resolution/master/assets/eye_catch.png)

- [画像拡大マスター：超解像セットアップシリーズ④ 超画像モデルの比較](#画像拡大マスター超解像セットアップシリーズ-超画像モデルの比較)
  - [元画像](#元画像)
  - [出力結果](#出力結果)
  - [感想](#感想)


## 元画像
![](https://raw.githubusercontent.com/yKesamaru/comparison_super_resolution/master/assets/tmp/processed_1.png)
![](https://raw.githubusercontent.com/yKesamaru/comparison_super_resolution/master/assets/tmp/processed_2.png)
![](https://raw.githubusercontent.com/yKesamaru/comparison_super_resolution/master/assets/tmp/processed_3.png)
![](https://raw.githubusercontent.com/yKesamaru/comparison_super_resolution/master/assets/tmp/processed_4.png)

## 出力結果
![](https://raw.githubusercontent.com/yKesamaru/comparison_super_resolution/master/assets/g1164.png)
![](https://raw.githubusercontent.com/yKesamaru/comparison_super_resolution/master/assets/text1035.png)

## 感想
論文の発表年順に、SRGAN, GFPGAN, VQFRを試してみました。
SRGANは、良くも悪くも、小さい画像をそのまま拡大しているような感じがします。
SRGANにくらべ、GFPGANとVQFRは顔に特化している分、顔の拡大には優れているように感じます。

しかしながら、VQFRは過度に顔の修復をしている感じがします。
おそらくデータセットに存在した顔の特徴を、他の顔にも適用しているのではないでしょうか？

![](https://raw.githubusercontent.com/yKesamaru/comparison_super_resolution/master/assets/g1973.png)

GFPGANが元画像を忠実に超解像しているのに対し、VQFRでは顔が変わってしまっています。
また、両者ともに、はっきりした二重瞼を「創作」する傾向がありそうです。
このようなハルシネーションを起こさないSRGANを選択する、というのも一つの手かもしれません。

![](https://raw.githubusercontent.com/yKesamaru/comparison_super_resolution/master/assets/g2044.png)

今回の比較実験で判明しましたが、GFPGANとVQFRは、入力画像として500X500ピクセルのサイズを期待しているようです。
そこから外れた場合、Segmentation faultを起こしてしまいます。
入力画像サイズについて、両者ともREADMEに記載がないので、注意が必要です。

以上です。ありがとうございました。