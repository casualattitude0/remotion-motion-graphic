# Remotion 影片工作區

用 [Remotion](https://www.remotion.dev/) 以 React 程式碼製作影片的工作區。每支影片是一個獨立的專案，各自放在一個子目錄裡，擁有自己的 `package.json`、相依套件與 git repo。

## 結構

```
Remotion/
├── CLAUDE.md          # 給 AI agent 的工作規則
├── AGENTS.md          # 指向 CLAUDE.md 的 symlink，供其他 agent 工具讀取
├── README.md
├── .claude/skills/    # 工作區 skill（motion-graphics：從需求訪談到輸出影片）
└── my-first-video/    # 一支影片 = 一個獨立的 Remotion 專案
```

## 需求

- Node.js（目前使用 v24）
- npm

## 新增影片

在工作區根目錄執行：

```bash
npx create-video@latest --yes --blank <影片名稱>
```

`--blank` 是空白模板，其他模板可用 `npx create-video@latest --help` 查看。

## 製作與輸出

以下指令都在該影片的專案目錄內執行。

開啟 Remotion Studio 預覽與編輯：

```bash
npm run dev
```

輸出影片：

```bash
npx remotion render
```

檢查程式碼（ESLint 與 TypeScript）：

```bash
npm run lint
```

## 專案內的檔案

- `src/Root.tsx`：註冊 composition（尺寸、fps、長度）
- `src/Composition.tsx`：影片內容
- `public/`：圖片、音訊等素材
- `remotion.config.ts`：Remotion 設定

## 授權

Remotion 對個人與三人以下的團隊免費，公司使用可能需要授權，詳見 [Remotion License](https://www.remotion.pro/license)。
