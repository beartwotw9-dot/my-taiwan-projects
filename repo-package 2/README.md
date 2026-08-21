# 我的互動體驗專案

這個資料夾包含兩個獨立的網頁體驗，已經整理成可以直接上傳到 GitHub 的結構：

```
.
├── kanding-script-murder/          崁頂時空圖鑑（12人沉浸實境劇本殺）
│   ├── kanding_dashboard.html      主頁面
│   ├── 圖片1.jpg ~ 圖片6.jpg        場景照片
│   ├── character-prompts.md        12位角色的 AI 生成圖 prompt（給 Midjourney / Higgsfield 等工具用）
│   └── characters/                 生成好的 12 張角色圖放這裡
└── zhutian-ar-guide/               竹田頓物驛站（AR 導覽 App）
    ├── 竹田頓物驛站_前台旅客AR導覽體驗.html   完整體驗版（按鈕模擬 AR）
    ├── ar-scan.html                          真實掃描版（相機真的辨識圖片）
    └── 如何測試真實掃描AR.md                  真實掃描版的設定與測試步驟
    └── 竹田頓物驛站_前台旅客AR導覽體驗.html
```

---

## 第一步：在 GitHub 建立新 repository

1. 登入 [github.com](https://github.com)，右上角點 **+** → **New repository**。
2. Repository name 隨意取，例如 `my-taiwan-projects`。
3. 選擇 **Public**（要用 GitHub Pages 免費發布網頁一定要 Public，除非你有付費方案）。
4. 不要勾選 "Add a README file"（我們已經準備好了），直接按 **Create repository**。

## 第二步：把這個資料夾的內容上傳上去

**方法 A：網頁上傳（最簡單，不用裝任何工具）**
1. 進到剛建好的空 repo 頁面，點 **uploading an existing file**。
2. 把這個資料夾裡的所有檔案跟資料夾**整個拖進去**（包含 `kanding-script-murder/`、`zhutian-ar-guide/`、`README.md`）。
3. 網頁上傳目前不支援直接拖「空資料夾」，如果 `characters/` 資料夾沒有跟著上傳，之後把生成好的圖片拖進 `kanding-script-murder/characters/` 這個路徑重新上傳一次即可。
4. 下方 commit 訊息隨意填，例如 `first upload`，按 **Commit changes**。

**方法 B：用 Git 指令（如果你電腦有裝 Git）**
```bash
cd 這個資料夾的路徑
git init
git add .
git commit -m "first upload"
git branch -M main
git remote add origin https://github.com/你的帳號/my-taiwan-projects.git
git push -u origin main
```

## 第三步：開啟 GitHub Pages（讓網址可以直接在瀏覽器打開）

1. 進到 repo 頁面 → **Settings** → 左側選單 **Pages**。
2. **Source** 選 `Deploy from a branch`，Branch 選 `main`，資料夾選 `/ (root)`，按 **Save**。
3. 等 1–2 分鐘，畫面會出現一個網址，長得像：
   `https://你的帳號.github.io/my-taiwan-projects/`
4. 之後兩個體驗的完整網址會是：
   - 崁頂時空圖鑑：`https://你的帳號.github.io/my-taiwan-projects/kanding-script-murder/kanding_dashboard.html`
   - 竹田 AR 導覽：`https://你的帳號.github.io/my-taiwan-projects/zhutian-ar-guide/竹田頓物驛站_前台旅客AR導覽體驗.html`
   - 竹田 AR 真實掃描版：`https://你的帳號.github.io/my-taiwan-projects/zhutian-ar-guide/ar-scan.html`
     （這個需要先照 `zhutian-ar-guide/如何測試真實掃描AR.md` 的步驟準備 `targets.mind`）

## 第四步：補上 12 張角色圖

1. 用 `kanding-script-murder/character-prompts.md` 裡的 prompt，到你選的 AI 生成工具（Midjourney / Higgsfield / 其他）畫出 12 張角色圖。
2. 檔名建議照文件裡的建議命名（`char-01-...jpg` ～ `char-12-...jpg`），存進 `kanding-script-murder/characters/` 資料夾。
3. 打開 `kanding_dashboard.html`，把每個角色卡片裡的：
   ```html
   <div class="avatar-placeholder">[ AI 生成圖片：... ]</div>
   ```
   換成：
   ```html
   <img src="characters/char-01-chen-shao-an.jpg" alt="陳紹安"
        style="width:100%;height:200px;object-fit:cover;border-radius:4px;">
   ```
4. 存檔後重新上傳到 GitHub（覆蓋原本的 `kanding_dashboard.html`），GitHub Pages 會自動更新。

---

有任何一步卡住，把錯誤訊息或截圖貼給我，我可以幫你排查。
