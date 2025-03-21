# 物理演算シミュレーション

このプロジェクトは、物理演算を用いた2Dシミュレーションを実装したものです。上から見下ろした箱の中で4つの色付きブロックが斜め方向に移動し、壁で反射しながら、最初にゴールに到達したブロックが勝利します。

## 機能

- 上から見下ろした2D画面
- 4つの色の異なるブロック（赤、緑、青、黄）
- ブロックは斜め4方向に移動
- 壁に当たると反射
- ブロック同士も衝突して反射
- 5秒後から、ゴールの反対側から白い壁がゆっくり迫ってくる（25秒かけて）
- ゴールに最初に到達した色が勝利
- BGMと効果音付き
- リセット機能（Rキー）
- 動画エクスポート機能（YouTubeなどにアップロード可能）

## 必要環境

- Python 3.6以上
- pygame
- numpy
- scipy

## セットアップと実行方法

### セットアップ

1. まず、セットアップスクリプトを実行して必要なライブラリをインストールします：

```
python physics_simulation/setup.py
```

このスクリプトは以下の作業を行います：
- 必要なパッケージ（pygame, numpy, scipy）のインストール
- サウンドファイルの生成

### 実行方法

セットアップが完了したら、以下のコマンドでシミュレーションを起動します：

```
python physics_simulation/main.py
```

#### コマンドライン引数

以下のコマンドライン引数を使用して、シミュレーションをカスタマイズできます：

```
python physics_simulation/main.py -c 5  # 5つの動画を連続生成
python physics_simulation/main.py --count 10  # 10個の動画を連続生成
python physics_simulation/main.py --no-video  # 動画出力を無効化
```

* `-c, --count`: 生成する動画の数（デフォルト: 1個）
* `--no-video`: 動画出力を無効にする

## 操作方法

- ESCキー: 終了
- Rキー: リセット（新しいゲームを開始）

## 動作説明

1. シミュレーション開始時、4つの色付きブロック（固定）がランダムな位置に配置されます
2. ブロックは斜め方向（45度、135度、225度、315度）にランダムに動き始めます
3. 壁に当たると反射します（衝突音付き）
4. ブロック同士も衝突すると反射します（衝突音付き）
5. 開始から5秒後、上部から白い壁がゆっくりと下に向かって移動を開始します
6. この壁は25秒かけて上から下へと移動し、ブロックを下に押し出します
7. 最初にゴール（画面下部中央の金色の領域）に到達したブロックが勝利します
8. 勝利すると、勝ったブロックの色で「Red Win!」「Green Win!」などと表示されます
9. 勝利後5秒経過、または最大2分経過すると自動的に終了し、動画ファイルが保存されます

## ファイル構成

- `main.py`: メインのシミュレーションプログラム
- `generate_sounds.py`: BGMと効果音を生成するスクリプト
- `setup.py`: 環境セットアップ用スクリプト
- `bgm.wav`: 自動生成されたBGM
- `collision.wav`: 壁との衝突音
- `goal.wav`: ゴール到達時の効果音
- `simulation_YYYYMMDD_HHMMSS.mp4`: 自動生成される動画ファイル

## カスタマイズ

`main.py`の上部にある定数を変更することで、様々な設定を調整できます：

- `WIDTH`, `HEIGHT`: 画面サイズ
- `BOX_SIZE`: 箱のサイズ
- `BLOCK_SIZE`: ブロックのサイズ
- `FPS`: フレームレート
- `BLOCK_COLORS`: ブロックの色
- `RECORD_VIDEO`: 動画を記録するかどうか（True/False）
- `MAX_GAME_TIME`: 最大ゲーム時間（秒）
- `WIN_DISPLAY_TIME`: 勝利後の表示時間（秒）
- `VIDEO_FPS`: 出力動画のフレームレート

## ライセンス

このプロジェクトはオープンソースです。
