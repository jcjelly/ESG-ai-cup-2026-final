# ESG-ai-cup-2026-final
# AI CUP 2026 春季賽－ESG 永續承諾驗證競賽

## 專案介紹

本專案為 AI CUP 2026 春季賽「ESG 永續承諾驗證競賽」之參賽程式。

本研究提出 **Three Expert Framework（三專家模型）**，將競賽四項預測任務拆分為三個專家模型：

* **Anchor Expert**：負責 Promise Status（是否存在承諾）
* **Quality Expert**：負責 Evidence Status（是否提供佐證）與 Evidence Quality（佐證品質）
* **Timeline Guardian**：負責 Verification Timeline（驗證時程）

此外，本研究結合以下技術提升模型效能與穩定性：

* 5-Fold Cross Validation
* Model Ensemble
* Dynamic Feature Engineering
* FGM 對抗訓練
* Logical Gate

---

# 執行環境

本專案於 **Google Colab GPU** 環境完成開發、訓練與測試。

## 軟體環境

| 項目            | 版本                 |
| ------------- | ------------------ |
| Python        | 3.11               |
| PyTorch       | 2.11.0 (CUDA 12.8) |
| Transformers  | 5.12.0             |
| Accelerate    | 1.14.0             |
| Pandas        | 2.2.2              |
| NumPy         | 2.0.2              |
| Scikit-learn  | 1.6.1              |
| Matplotlib    | 3.10.0             |
| Seaborn       | 0.13.2             |
| tqdm          | 4.67.3             |
| SentencePiece | 0.2.1              |

## 硬體環境

| 項目   | 規格                    |
| ---- | --------------------- |
| 開發平台 | Google Colab          |
| GPU  | NVIDIA A100-SXM4-80GB |
| CUDA | 12.8                  |

---

# 專案結構

```text
AI-CUP-2026-ESG/

│
├── ESG_AICUP_Final.ipynb      # 主程式
├── README.md
├── requirements.txt
│
├── data/                      # 官方資料集
├── weights/                   # 模型權重
│   ├── anchor/
│   ├── quality/
│   └── timeline/
│
└── submission/                # 推論結果
```

---

# 資料集

請先下載 AI CUP 官方提供之資料集。

並放入：

```text
data/
```

例如：

```text
data/
    vpesg4k_train_2000.json
    vpesg4k_test_2000.json
```

---

# 模型權重

由於模型權重檔案容量較大，因此未放置於 GitHub Repository。

請由下列 Google Drive 下載：

**Google Drive：**

（請貼上 Google Drive 共用連結）

下載完成後，請保持以下資料夾結構：

```text
weights/

├── anchor/
├── quality/
└── timeline/
```

---

# 安裝方式

若使用 Google Colab，請直接開啟 Notebook，並執行第一個 Cell 安裝所需套件。

若於本機執行，請先安裝所需套件：

```bash
pip install -r requirements.txt
```

---

# Notebook 執行方式

本 Notebook 包含完整的訓練與推論流程。

若僅需重現本研究結果，**不需重新訓練模型**。

請依序執行：

1. 環境設定
2. 資料載入
3. Feature Engineering
4. 建立模型
5. 載入模型權重
6. Inference
7. 產生 submission.csv

---

# 模型訓練

Notebook 已保留完整訓練流程，包括：

* 資料前處理
* Feature Engineering
* Three Expert Framework
* 5-Fold Cross Validation
* FGM Adversarial Training
* Model Checkpoint Saving

若需重新訓練模型，可執行 Training 區塊。

---

# 推論流程

本專案已提供訓練完成之模型權重，因此**無需重新訓練模型**。

下載模型權重後，依序執行 Notebook，即可完成：

* Anchor Ensemble
* Quality Ensemble
* Timeline Ensemble
* Logical Gate
* Submission 產生

---

# 輸入資料

```text
data/

vpesg4k_train_2000.json
vpesg4k_test_2000.json
```

---

# 輸出結果

推論完成後，程式將自動於：

```text
submission/
```

產生：

```text
submission.csv
```

CSV 包含四個預測欄位：

* promise_status
* evidence_status
* evidence_quality
* verification_timeline

---

# 模型架構

本研究主要包含以下技術：

* Three Expert Framework
* Anchor Expert
* Quality Expert
* Timeline Guardian
* Dual Pooling
* ShallowEQ
* Dynamic Feature Prefix
* Timeline Feature Engineering
* FGM Adversarial Training
* 5-Fold Cross Validation
* Quality Ensemble
* Timeline Ensemble
* Logical Gate

---

# 重現方式

若要重現本研究結果，請依照以下步驟：

1. 下載 AI CUP 官方資料集並放入 `data/`
2. 下載 Google Drive 提供之模型權重並放入 `weights/`
3. 開啟 `ESG_AICUP_Final.ipynb`
4. 依序執行 Notebook 所有 Cell（Training 區塊可略過）
5. 程式將自動於 `submission/` 產生 `submission.csv`

---

# 作者

AI CUP 2026 春季賽－ESG 永續承諾驗證競賽參賽隊伍

