# Identifying Statistical Bias in Dataset Replication

## Info
- Author: Logan Engstrom, Andrew Ilyas, Shibani Santurkar, Dimitris Tsipras, Jacob Steinhardt, Aleksander Madry
- Date: 2020/05/19
- Abst: データセット複製は、特定のベンチマークでのテスト精度の向上が、モデルの汎化能力の向上に一致するかどうかを評価するのに有用なツールです。この研究では、データセット複製に対する標準的なアプローチが統計的バイアスを導入し、結果の観測を歪めてしまう、直感的ではないが重要な方法を提示します。我々は、ImageNetデータセットの複製であるImageNet-v2を研究しています。このデータセットでは、データ品質の標準的な人間によるループ内測定を制御した後でも、モデルは精度の有意な低下（11-14％）を示します。識別された統計的バイアスを補正した後、当初の11.7%±1.0%の精度低下のうち、推定3.6%±1.5%しか補正されていないことを示した。最後に、データセットの複製におけるバイアスを認識し、回避するための具体的な推奨事項を示す。

## Link
- [arXiv](https://arxiv.org/abs/2005.09619)
- [blog](https://gradientscience.org/data_rep_bias/)
- [GitHub](https://github.com/MadryLab/dataset-replication-analysis)


## Points
- 既存のベンチマークを使った評価は、下記のような問題点がある。
	- test setへの過学習
	- データセットの作成方法に鋭敏（ラベルの付け方、画像の圧縮方法など）

- dataset replication は汎化性能が向上しているかの評価方法として用いられるが、複製されたtest setでの精度は大きく下がる傾向が知られている。

- ImageNet-v2 では test set において 11-14% の精度低下が報告されたが、この大きな精度の低下の原因は以前として未解決問題出会った。

- この研究では dataset replication のプロセスを通して統計的なバイアスが生じる仕組みを特定する。

- この仕組みによって 11.7% の精度低下のうちの3.6%は説明が可能。

- 現象の説明は dataset replication の中の statistic matching のステップを中心に展開される。

- statistic matching ではモデル性能に影響を与えることが知られている変数を制御することによって、元のテストセットとその複製でのモデル性能が比較可能であるようにする。

- ImageNet-v2 では selection frequency に基づくstatistic matching が行われた。