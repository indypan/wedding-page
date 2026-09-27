# 踩坑紀錄與經驗總結 (Lessons Learned)

## 2026-09-27 - GitHub Pages 部署初始設定
1. **GitHub CLI (gh) 於 Windows 的自動安裝與環境變數**：
   - 透過 `winget install --id GitHub.cli` 可無痛安裝，但當前 PowerShell Session 尚未刷新 PATH，需直接呼叫 `C:\Program Files\GitHub CLI\gh.exe` 或刷新 `$env:Path`。
2. **無人值守 / 快速驗證流程**：
   - 使用 `gh auth login --web` 的 Device Code 授權機制，在終端產生一次性代碼並自動複製至剪貼簿，大幅簡化使用者手動產生 Personal Access Token 的摩擦力。
3. **GitHub Pages API 自動啟用**：
   - 透過 `gh api --method POST /repos/{owner}/{repo}/pages` 傳入 `source: {branch: 'main', path: '/'}`，即可直接在終端開啟 Pages 功能，無需使用者手動進入網頁設定。
4. **靜態資源與路徑結構**：
   - GitHub Pages 部署子目錄型 repository（如 `https://<username>.github.io/<repo>/`）時，避免在 HTML 內部使用以根目錄開頭的絕對路徑（如 `/style.css`），應採用相對路徑（如 `./style.css`）或直接內嵌於單一檔案內，能保證部署即開即用，不會發生 404 資源缺失問題。
