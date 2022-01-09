# 大阪　ハンズオンセミナー 2022年1月10日


リピート病を引き起こす、10箇所のリピート伸長を持つデータ(10-repeat-expansion.maf)を使ってtandem-genotypesを試してみよう！

## tandem-genotypes

* リードの長さの変化を出力


    tandem-genotypes disease-tr.txt 10-repeat-expansion.maf > out

* リード名も出力


    tandem-genotypes -v disease-tr.txt 10-repeat-expansion.maf > out-v

* 2アリルごとの推定を出してくれる


    tandem-genotypes -o2 disease-tr.txt 10-repeat-expansion.maf > out-o2

* ヒストグラムを出してくれる（Rが必要）

    tandem-genotypes-plot out plot


## リードのアライメント

* LASTのインストールが必要です　https://gitlab.com/mcfrith/last
* 参照ゲノム：https://gitlab.com/mcfrith/last/-/blob/main/doc/last-cookbook.rst


    lastdb -P8 -uNEAR hg38db GRCh38.fa 

    last-train -P8 hg38db 10-repeat-expansion.fa > train.out 

    lastal -P8 -p train.out  hg38db 10-repeat-expansion.fa | last-split > 10-repeat-expansion.maf
