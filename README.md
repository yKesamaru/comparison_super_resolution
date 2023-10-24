# 画像拡大マスター：超解像セットアップシリーズ④ 超画像モデルの比較

超解像シリーズは全部で4編書きます。
1.　MAX Image Resolution Enhancer
2.　GFPGAN
3.　VQFR
4.　1~3の比較

この超解像シリーズでは、いくつかの超解像技術をピックアップして、それぞれの環境構築方法を中心にご紹介します。

今回は、MAX Image Resolution Enhancer（SRGAN）, GFPGAN, VQFRの3つの超解像技術を比較します。

## 注意
- 画像比較の性質上、PCでの閲覧を推奨します。
- 大量の画像が存在するため、通信量が多くなります。

![](https://raw.githubusercontent.com/yKesamaru/comparison_super_resolution/master/assets/eye_catch.png)

- [画像拡大マスター：超解像セットアップシリーズ④ 超画像モデルの比較](#画像拡大マスター超解像セットアップシリーズ-超画像モデルの比較)
  - [注意](#注意)
  - [元画像](#元画像)
  - [出力結果](#出力結果)
  - [感想](#感想)
  - [追加実験：2023年10月24日](#追加実験2023年10月24日)
    - [元画像](#元画像-1)
    - [SRGAN](#srgan)
    - [GFPGAN](#gfpgan)
    - [VQFR](#vqfr)

https://zenn.dev/ykesamaru/articles/86ace66f116553

https://zenn.dev/ykesamaru/articles/35f05023d537c2

https://zenn.dev/ykesamaru/articles/fae6f5f30e5522


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
~~このようなハルシネーションを起こさないSRGANを選択する、というのも一つの手かもしれません。~~
（SRGANもハルシネーションを起こします。`追加実験2023年10月24日`を参照して下さい。）

![](https://raw.githubusercontent.com/yKesamaru/comparison_super_resolution/master/assets/g2044.png)

今回の比較実験で判明しましたが、GFPGANとVQFRは、入力画像として500X500ピクセルのサイズを期待しているようです。
そこから外れた場合、Segmentation faultを起こしてしまいます。
入力画像サイズについて、両者ともREADMEに記載がないので、注意が必要です。

以上です。ありがとうございました。

## 追加実験：2023年10月24日
SRGAN, GFPGAN, VQFRの3つの超解像技術において、元画像がどのような劣化（ぼかし）を受けているかにより、出力結果が変わることを確認しました。

### 元画像
- BLUR
  - ![](https://raw.githubusercontent.com/yKesamaru/comparison_super_resolution/master/assets/original_blur_1.png)
- FILM
  - ![](https://raw.githubusercontent.com/yKesamaru/comparison_super_resolution/master/assets/original_film_2.png)
- MOSAIC
  - ![](https://raw.githubusercontent.com/yKesamaru/comparison_super_resolution/master/assets/original_mosaic_3.png)

### SRGAN
- BLUR
  - ![](https://raw.githubusercontent.com/yKesamaru/comparison_super_resolution/master/assets/SRGAN_BLUR.png)
- FILM
  - ![](https://raw.githubusercontent.com/yKesamaru/comparison_super_resolution/master/assets/SRGAN_FILM.png)
- MOSAIC
  - ![](https://raw.githubusercontent.com/yKesamaru/comparison_super_resolution/master/assets/SRGAN_MOSAIC.png)

### GFPGAN
- BLUR
  - ![](https://raw.githubusercontent.com/yKesamaru/comparison_super_resolution/master/assets/GFPGAN_BLUR.png)
- FILM
  - ![](https://raw.githubusercontent.com/yKesamaru/comparison_super_resolution/master/assets/GFPGAN_FILM.png)
- MOSAIC
  - ![](https://raw.githubusercontent.com/yKesamaru/comparison_super_resolution/master/assets/GFPGAN_MOSAIC.png)

### VQFR
- BLUR
  - ![](https://raw.githubusercontent.com/yKesamaru/comparison_super_resolution/master/assets/VQFR_BLUR.png)
- FILM
  - ![](https://raw.githubusercontent.com/yKesamaru/comparison_super_resolution/master/assets/VQFR_FILM.png)
- MOSAIC
  - ![](https://raw.githubusercontent.com/yKesamaru/comparison_super_resolution/master/assets/VQFR_MOSAIC.png)

