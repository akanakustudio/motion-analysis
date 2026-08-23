# Basketball Shot Form Coach

バスケットボールのシュートフォーム改善に特化した、単眼カメラによる姿勢可視化プロトタイプです。[MediaPipe BlazePose](https://github.com/google-ai-edge/mediapipe)（Pose Landmarker, world landmarks）を利用し、サーバーへの映像送信なしでブラウザ内で推論します。

## 特徴

- シュートフォームに特化した肘・肩・膝の角度可視化
- フリースローやジャンプシュートのフォーム比較に適したリアルタイム計測
- One Euro Filter によるランドマークの平滑化（ジッター low減）
- 体幹の傾きや腕の伸展状態を可視化して、フォームの再現性を確認
- 計測ログのCSV書き出し
- フロント／リアカメラの切り替え

## 公開URL

GitHub Pages で公開済みです。

- 本アプリ: https://akanakustudio.github.io/motion-analysis/

## 使い方

1. 上記の公開URLへアクセスします。
2. フリースローまたはジャンプシュートの動作を、正面〜斜め45度の角度で撮影します。
3. 「カメラを起動」を押し、カメラアクセスを許可します。
4. シュートフォームモードで各角度を確認し、肘・肩・膝の角度や体幹の傾きを比較します。
5. 「ログ記録 開始」で計測データの記録を開始し、「ログ記録 停止」でCSVとして保存されます。

### ローカルでの起動例

```bash
npx serve docs
```

## 技術構成

- [MediaPipe Tasks Vision](https://ai.google.dev/edge/mediapipe/solutions/vision/pose_landmarker)（`@mediapipe/tasks-vision`、CDN経由でロード）
- Pose Landmarker Full モデル（`pose_landmarker_full`）
- Vanilla JavaScript（ビルド不要、単一HTMLファイル）

## 更新履歴

- 2026-08-23: シュートフォーム改善に特化した計測モードへ変更し、READMEとUI文言を更新。
- 2026-08-23: GitHub Pages での公開URLを追加し、READMEにアクセス先を明記。
- 2026-08-23: 3D姿勢推定プロトタイプの初期版を作成し、ブラウザ内でのリアルタイム計測機能を実装。

## 注意事項

本プロトタイプは単眼カメラを用いているため、3D座標は相対値であり奥行きのスケールは較正されていません。絶対的な距離・角度は参考値としてご利用ください。また、高速な動作では検出精度が低下する場合があります。

## ライセンス

[MIT License](LICENSE)
