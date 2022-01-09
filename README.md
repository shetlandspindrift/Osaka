# 大阪　ハンズオンセミナー 2022年1月10日


10箇所のリピート伸長を持つデータ(chimera.maf)を使ってtandem-genotypesを試してみよう！

## tandem-getotypesのテスト

* リードの長さの変化を出力

    tandem-genotypes hg38-disease-tr.txt chimera.maf > out

* リード名も出力

    tandem-genotypes -v hg38-disease-tr.txt chimera.maf > out-v

* 2アリルごとの推定を出してくれる

    tandem-genotypes -o2 hg38-disease-tr.txt chimera.maf > out-o2

* ヒストグラムを出してくれる（Rが必要）

    tandem-genotypes-plot out
    


## リードのアライメント

* LASTのインストールが必要です　https://gitlab.com/mcfrith/last
* 参照ゲノム：https://gitlab.com/mcfrith/last/-/blob/main/doc/last-cookbook.rst

### hg38をインストール

http://hgdownload.soe.ucsc.edu/goldenPath/hg38/bigZips/analysisSet/hg38.analysisSet.fa.gz

### 

    lastdb -P8 -uNEAR hg38db GRCh38.fa 

### エラー推定とアライメント

    last-train -P8 hg38db chimera.fa > train.out 

    lastal -P8 -p train.out  hg38db chimera.fa | last-split > out.maf
