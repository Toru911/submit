# submit
インターンシップ選考課題の提出リポジトリ

## 重みファイルについて

本課題において最終モデルとして採用したのは、ResNet18とEfficientNetV2-Sによるアンサンブルモデルです。

本来であれば、それぞれのモデルの学習済み重みファイル（.pth）を提出物として添付する予定でしたが、
Google Colab環境における計算資源制約（無料枠および限定的な有料クレジット）により、
最終学習完了後の重みファイルの保存およびダウンロード処理を実行する前にランタイムが終了してしまい、
重みファイルの出力ができませんでした。

本実験では、モデルの学習・評価およびアンサンブルの検証はすべて正常に完了しており、
レポート内に記載した性能指標はその結果に基づいています。

重みファイル自体は、以下のコードにより再現可能です：

- `run_experiment_with_existing_loaders()` による学習
- `fit_model()` 内での `torch.save()` による保存

再実行により同様の重みファイルを生成可能であることを確認しております。

また、最終モデルの推論は以下の構成で行っています：

- ResNet18 と EfficientNetV2-S の確率出力を取得
- 重み付きソフト投票（0.5 : 0.5）
- threshold = 0.73 により分類

本件につきましてご理解いただけますと幸いです。

**実行環境**
- Google Colab上でランタイムを`H100`に設定する (提出期限に間に合うよう実験を完了させるために有料クレジットを使用しH100で動作させています)

- Google Driveに当課題のデータセットを保存し、ColabにDriveデータセットフォルダをマウントさせる。

```
# 例:
# dataset/
#   good/
#   bad/

DATASET_DIR = Path("/content/drive/MyDrive/dataset")
GOOD_DIR = DATASET_DIR / "good"
BAD_DIR = DATASET_DIR / "bad"

assert GOOD_DIR.exists(), f"Not found: {GOOD_DIR}"
assert BAD_DIR.exists(), f"Not found: {BAD_DIR}"
```

**使用したライブラリのバージョン**

- pytorch:2.10.0+cu128
- sklearn:1.6.1
- ImageHash:4.3.2

**コードの実行手順**
- セル順にコードを実行してください
