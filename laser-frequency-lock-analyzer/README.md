# Laser Frequency Lock Analyzer

レーザー周波数安定化系の開ループ伝達関数と安定余裕を、ブラウザ内で計算する静的Webアプリです。

## GitHub Pagesで公開する方法

1. GitHub の Repository で `index.html` と `README.md` を `main` ブランチ直下にアップロードします。
2. **Settings → Pages** を開きます。
3. **Build and deployment → Source** を `Deploy from a branch` にします。
4. Branch を `main`、Folder を `/(root)` にして Save します。
5. 数分後、`https://suzuka-tech.github.io/laser-frequency-lock-analyzer/` でアクセスできます。

## モデル

- `G(s) = A/s`, `A = 2π KFM kφ/(Rs + rd)`
- `D(s) = exp(-sτ)`
- `C_PI(s) = -(R2_PI/R1_PI + 1/(s R1_PI C_PI))`
- Fast枝：`R1_LF` と `C_LF` の直列インピーダンス
- Slow枝：`R2_LF`
- 出力負荷：`RG` を接地
- `C_eq(s) = F_F(s) + F_S(s) C_PI(s)`
- `L(s) = polarity × G(s) × C_eq(s) × D(s)`

**重要：** Loop Filter の接続は仮定モデルです。実際の回路図と相違がないか確認し、必要に応じて `F_F(s)` と `F_S(s)` の式を修正してください。安定余裕は指定周波数範囲内の全交差点から計算しますが、Nyquist表示は正周波数側のみであり、厳密なNyquist安定判別を代替するものではありません。

## Privacy

入力値、計算、グラフ描画はローカルブラウザ内で完結します。外部API、データベース、アクセス解析は使用しません。
