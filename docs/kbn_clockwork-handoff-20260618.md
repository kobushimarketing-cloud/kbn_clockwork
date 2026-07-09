# kbn_clockwork 引き継ぎドキュメント (VIP LP)

- リポジトリ: `D:\googledrive\ClaudeProjects\projects\kbn_clockwork`
- GitHub: `https://github.com/kobushimarketing-cloud/kbn_clockwork`
- 公開: GitHub Pages（`main` ブランチ配信）
- 対象: VIP 会員 LP（`vip/` 配下）

---

## 2026-06-18 更新(前半)

### 完了した作業(前半)
- VIP LP のウイスキー名を修正、店舗情報リンクを追加(commit 4205d3c)
- レディースプラン申込リンクを追加、顧客ポータル URL を修正(commit 7402cd5)
- フォントを Meiryo ベースの sans-serif スタックに変更(commit 2a8b306)

---

## 2026-06-18 更新(続き)

### 完了した作業(続き)
- VIP LP の QR画像を整理
  - 通常プランボタン内の QR画像(VIPSTRIPEQR.png参照)を削除
  - レディースプランと表示を統一(両方ともQRなし、LP内ボタン選択のみ)
  - VIPSTRIPEQR.png ファイル自体は削除していない(HTML参照のみ削除)
  - commit 8b7522c
- apply-hint 案内文をQR削除に合わせて修正
  - 「スマホの方は QR コードから、PC の方は上のボタンから」→「上のボタンからお申込みください」
  - commit c800952
- push運用の変更: 以後、git push は Claude Code側で実行する運用に変更
  (従来は井上さんの手動実施だったが、本日から自動化)

### 本番反映トラブルの記録(教訓)
- タスク1・2(レディースプラン追加、フォント変更)完了後、コミットのみでpush未実施のまま
  井上さんがLPを確認 → 古いバージョンを見て「事業者情報重複」等の誤報告が発生
- 原因: git push origin main が実行されておらず、GitHub Pagesが旧版を配信し続けていた
- 教訓: コミット後は必ずpushまで完結させ、本番HTMLとリポジトリのdiffがゼロであることを
  確認してから完了報告すること

### 関連commit一覧(本日分、VIP LP関連、時系列)
- 4205d3c fix(vip): correct whisky name + add shop info links
- 7402cd5 feat(vip): add ladies plan link + fix customer portal URL
- 2a8b306 style(vip): switch to Meiryo-based sans-serif font stack
- 8b7522c style(vip): remove QR image from normal plan button for consistency with ladies plan
- c800952 fix(vip): update apply hint text after QR image removal
