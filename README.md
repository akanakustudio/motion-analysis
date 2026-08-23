# Motion Analysis — Markerless Motion 3D Pose Prototype

スマートフォンやPCのカメラだけで全身の姿勢を推定し、関節角度などをリアルタイムに可視化するブラウザ内蔵型プロトタイプです。[MediaPipe BlazePose](https://github.com/google-ai-edge/mediapipe)（Pose Landmarker, world landmarks）を利用し、サーバーへの映像送信を行わずすべてブラウザ内で推論します。

## 特徴

- 単眼カメラ映像からの3D姿勢推定（ブラウザ内推論、GPU利用）
- One Euro Filter によるランドマークの平滑化（ジッター low減）
- 用途別の関節角度計算モード
  - 汎用（肘・膝角度、体幹傾き）
  - スクワット（膝・股関節角度）
  - 投球フォーム（肘・肩角度）
- FPSと各種角度のリアルタイム表示
- 計測ログのCSV書き出し
- フロント／リアカメラの切り替え

## 公開URL

GitHub Pages で公開済みです。

- 本アプリ: https://akanakustudio.github.io/motion-analysis/

## 使い方

1. 上記の公開URLへアクセスします。
2. [`src/index.html`](src/index.html) を静的サーバーで配信するか、そのままブラウザで開きます（カメラ利用には `https` または `localhost` が必要です）。
3. 「カメラを起動」を押し、カメラアクセスを許可します。
4. スマホを縦か横に固定し、全身が映る距離（2〜3m）、正面〜斜め45度の角度で撮影します。
5. 用途に応じて計測モード（汎用／スクワット／投球フォーム）を選択します。
6. 「ログ記録 開始」で計測データの記録を開始し、「ログ記録 停止」でCSVとして保存されます。

### ローカルでの起動例

```bash
npx serve src
```

## 技術構成

- [MediaPipe Tasks Vision](https://ai.google.dev/edge/mediapipe/solutions/vision/pose_landmarker)（`@mediapipe/tasks-vision`、CDN経由でロード）
- Pose Landmarker Full モデル（`pose_landmarker_full`）
- Vanilla JavaScript（ビルド不要、単一HTMLファイル）

## 注意事項

本プロトタイプは単眼カメラを用いているため、3D座標は相対値であり奥行きのスケールは較正されていません。絶対的な距離・角度は参考値としてご利用ください。また、高速な動作では検出精度が低下する場合があります。

## ライセンス

[MIT License](LICENSE)
