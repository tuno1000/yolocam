# YOLO カメラ検出

スマホのカメラ映像を YOLOv8n でリアルタイム物体検出する Web ページです。人を見つけると、YOLOv8n-pose で読み取った姿勢と動きから「戦闘値」を表示します（体格・構え・ガード・速さ・存在感から計算する遊びの数値です）。処理はすべてブラウザ内で行い、映像は外部に送信しません。

## 公開手順（GitHub Pages）

1. GitHub で新しいリポジトリを作成（例: `yolo-cam`、Public）
2. このフォルダの中身をすべてアップロード（Add file → Upload files）
3. Settings → Pages → Branch を `main` / `(root)` にして Save
4. 数分後に `https://<ユーザー名>.github.io/yolo-cam/` をスマホで開く
5. 「ライブ検出」→ カメラを許可

## ファイル

| ファイル | 内容 |
|---|---|
| index.html | ページ本体 |
| yolov8n.onnx | YOLOv8n モデル（COCO 80 クラス） |
| yolov8n-pose.onnx | YOLOv8n-pose モデル（人の 17 関節） |
| ort.wasm.min.js / ort-wasm*.wasm | ONNX Runtime Web 1.17.3 |

## 注意

- カメラは HTTPS でのみ動きます（`file://` で直接開くと不可）。PC でローカル確認するなら `python -m http.server` で `http://localhost:8000` を開く。
- YOLOv8n / YOLOv8n-pose モデルは Ultralytics の AGPL-3.0 ライセンスです。
