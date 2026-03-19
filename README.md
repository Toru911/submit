# submit
インターンシップ選考課題の提出リポジトリ

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
