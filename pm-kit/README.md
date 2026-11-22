# PM 工具包

讓 Claude 擔任專案管理人，巡檢你所有的開發案子。

| 檔案 | 用途 | 放在哪裡 |
|---|---|---|
| `pm/CLAUDE.md` | PM 的角色與巡檢規則 | 你電腦上的 PM 資料夾 |
| `templates/CLAUDE.md` | 每個專案的工作規則與完成標準 | 每個專案 repo 的根目錄 |
| `templates/STATUS.md` | 每個專案的進度檔 | 每個專案 repo 的根目錄 |

## 為什麼 PM 要在你的電腦上跑

你的開發案子大多跑在自己的電腦上。雲端的 PM 工作階段讀不到這些案子的對話紀錄，只看得到一行摘要。PM 放在同一台電腦上，就能直接讀每個專案資料夾裡的 `STATUS.md`、git 紀錄和程式碼。

## 設定步驟

### 1. 建立 PM 資料夾（做一次）

在你的 Mac 終端機執行：

```bash
mkdir -p ~/claude-pm
cp pm-kit/pm/CLAUDE.md ~/claude-pm/CLAUDE.md
```

打開 `~/claude-pm/CLAUDE.md`，在「你管理的專案」表格填上每個專案的資料夾路徑。

### 2. 把範本放進每個專案（每個專案做一次）

```bash
cp pm-kit/templates/CLAUDE.md  <專案資料夾>/CLAUDE.md
cp pm-kit/templates/STATUS.md  <專案資料夾>/STATUS.md
```

如果專案已經有 `CLAUDE.md`，不要覆蓋，把範本的「工作規則」和「完成標準」貼到原本檔案的最後面。

接著在該專案的 Claude Code 工作階段說一次：

> 請照 CLAUDE.md 的規則，現在先把 STATUS.md 填好。

### 3. 開始巡檢（每次要看進度時）

```bash
cd ~/claude-pm
claude --add-dir <專案資料夾1> --add-dir <專案資料夾2>
```

進入後先用 `/model` 選 Opus 5.5，然後說：

> 巡檢

如果 `claude` 指令不支援 `--add-dir`，直接在 `~/claude-pm` 開啟 Claude Code，PM 會照表格裡的路徑去讀各個專案；遇到權限詢問時允許讀取即可。
