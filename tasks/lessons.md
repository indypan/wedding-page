# 踩坑紀錄與經驗總結 (Lessons Learned)

## 2026-09-27 - GitHub Pages 部署初始設定
1. **GitHub CLI (gh) 檢查**：
   - 本地環境尚未安裝或未加入 PATH 的 `gh` CLI 工具。因此若要建立遠端儲存庫，可直接使用 GitHub 網頁介面建立，或透過使用者的 Personal Access Token (PAT) / SSH Key 進行連線。
2. **靜態資源與路徑結構**：
   - GitHub Pages 部署子目錄型 repository（如 `https://<username>.github.io/<repo>/`）時，避免在 HTML 內部使用以根目錄開頭的絕對路徑（如 `/style.css`），應採用相對路徑（如 `./style.css`）或直接內嵌於單一檔案內，能保證部署即開即用，不會發生 404 資源缺失問題。
