# keirin-app-data

競輪選手メモアプリ（keirin-memo-app）の**当日データ配信用**リポジトリ。GitHub Pages で静的 JSON を配信する。

## ファイル
- `<YYYY-MM-DD>.json` … 1日分の**全レース**（出走表・予測確率・SHAP 根拠・3連単買い目）
- `index.json` … 利用可能な日付一覧（`dates` / `latest`）
- `.nojekyll` … Pages の Jekyll 処理を無効化し JSON をそのまま配信

## 生成・更新
予測エンジン `keirin-ai` 側で生成・push する:
```
python -m scripts.export_app_daily --out ../keirin-app-data   # JSON 生成のみ
python -m scripts.sync_app_data                               # 生成＋ pull/commit/push
```

## 配信 URL（GitHub Pages）
```
https://kurinaka12-afk.github.io/keirin-app-data/<YYYY-MM-DD>.json
https://kurinaka12-afk.github.io/keirin-app-data/index.json
```

買い目は予測エンジンが保存した canonical な推奨（`trifecta_recommendations`）。予測は機械学習による参考情報で的中を保証しない。車券購入は自己責任。
