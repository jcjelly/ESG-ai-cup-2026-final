# ESG-ai-cup-2026-final
本研究提出 Three Expert Framework（三專家模型），將競賽四項預測任務拆分為三個專家模型：

Anchor Expert：負責 Promise Status（是否存在承諾）
Quality Expert：負責 Evidence Status（是否提供佐證）與 Evidence Quality（佐證品質）
Timeline Guardian：負責 Verification Timeline（驗證時程）

除此之外，模型亦結合：

5-Fold Cross Validation
Model Ensemble
Dynamic Feature Engineering
FGM 對抗訓練
Logical Gate

以提升模型穩定性與預測效能。

執行環境
項目	版本
Python	3.11
PyTorch	2.x
Transformers	4.x
Pandas	最新版本
NumPy	最新版本
Scikit-learn	最新版本
Google Colab	建議使用

硬體需求：

CUDA GPU（建議）
Google Colab GPU
專案結構
AI-CUP-2026-ESG/

│

├── ESG_AICUP_Final.ipynb      # 主程式

├── README.md

├── requirements.txt

│

├── data/                      # 資料集

│

├── weights/                   # 模型權重

│   ├── anchor/

│   ├── quality/

│   └── timeline/

│

└── submission/                # 推論結果

資料集

請先下載 AI CUP 官方提供之資料集。

將資料放入：

data/

例如：

data/

vpesg4k_train_2000.json

vpesg4k_test.json
模型權重

由於模型權重檔案較大，因此未直接放置於 GitHub。

請至下列 Google Drive 下載：

Google Drive：

（請貼上你的 Google Drive 共用連結）

下載完成後，請保持以下資料夾結構：

weights/

├── anchor/
├── quality/
└── timeline/

例如：

weights/

anchor/
    best_anchor_fold1.pt
    ...
    best_anchor_fold5.pt

quality/
    best_quality_fold1.pt
    best_quality_fgm_esonly_fold1.pt
    ...
    best_quality_fold5.pt

timeline/
    best_timeline_fold_new1.pt
    best_timeline_testsafe_fold1.pt
    ...
安裝方式

建議使用 Google Colab 執行。

若於本機執行，可安裝所需套件：

pip install -r requirements.txt

若沒有 requirements.txt，可依 Notebook 安裝所需套件。

訓練流程

Notebook 已包含完整訓練流程，包括：

載入資料集
資料前處理
Feature Engineering
建立 Three Expert 模型
5-Fold Cross Validation
FGM 對抗訓練
儲存模型權重

訓練完成後，模型權重將存放於：

weights/
推論流程

請先下載模型權重並放入：

weights/

依序執行 Notebook 中 Cell，即可完成：
(本專案已提供訓練完成之模型權重，因此不需重新執行訓練模型區塊即可重現推論結果。)

載入權重
Anchor Ensemble
Quality Ensemble
Timeline Ensemble
Logical Gate
產生最終預測結果
輸入資料

Notebook 使用：

data/

vpesg4k_train_2000.json

vpesg4k_test_2000.json
輸出結果

推論完成後，將產生：

submission/

submission.csv

CSV 內容包含四個欄位：

promise_status
evidence_status
evidence_quality
verification_timeline
模型架構

本系統主要包含：

Three Expert Framework
Anchor Expert
Quality Expert
Timeline Guardian
Dual Pooling
ShallowEQ
Dynamic Feature Prefix
Timeline Feature Engineering
FGM Adversarial Training
5-Fold Cross Validation
Quality Ensemble
Timeline Ensemble
Logical Gate
重現方式

若要重現本研究結果，請依照以下步驟：

下載 AI CUP 官方資料集。
將資料放入 data/。
下載 Google Drive 提供之模型權重。
將模型權重放入 weights/。
開啟 ESG_AICUP_Final.ipynb。
依照 Notebook 由上至下依序執行所有 Cell。
程式將自動於 submission/ 產生 submission.csv。
作者

AI CUP 2026 春季賽－ESG 永續承諾驗證競賽參賽隊伍
