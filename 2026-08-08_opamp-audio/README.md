# 2026-08-08_opamp-audio

ISHI会「オーディオ用OPAMP半導体ハンズオン」(2026/08/08, WeWork日比谷) の成果物。
プロセス: OpenSUSI-TR10 (TR-1um) / ツール: KLayout, xschem, ngspice

## 成果物

- 差動増幅回路: `opamp_r2r_diff_yamazaki.sch` / `opamp_r2r_diff_yamazaki.gds`
- AB級出力段: `opamp_r2r_ABAMP_yamazaki.sch` / `opamp_r2r_ABAMP_yamazaki.gds`

両ブロックとも DRC 0件 / LVS "Netlists match" 確認済み。サイズ制限(差動300×500µm, AB級800×500µm)内であることも実測確認。前回に続きチップアート "T.Y" をM1に刻印。

## メモ・感想

- 提出物確定後、残り時間でtry_layout_01〜09をゼロから自力再現。PCell配置→M1/VIA/M2配線→ウェルタップ→ガードリングまで到達、DRC 0件を達成
- 前回はsubckt名とセル名の不一致でLVSが失敗したが、今回は`cp`でファイル複製したため名前ズレなし。LVSが見るのはファイル名でなく中身のセル名、という切り分けができた
- スナップ設定0.005µmが原因でOFFGRID違反268件を経験。グリッド設定は作業前に確認すべし
- 井戸をNWレイヤーで描いてしまいDRC大量発生→正しくはWN。プロセスのレイヤー名は思い込み禁物
- サンプルの余裕ある配置は全てDRCルール由来。エラーを読むことが「なぜその形か」の答え合わせになる
