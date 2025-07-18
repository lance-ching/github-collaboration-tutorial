# 函數型資料分析 Functional Data Analysis
一、簡介與應用場景
❖ 函數型資料 (Functional Data)
• 資料呈現為連續函數（如時間的函數），而非離散觀測值。
• 通常來自於曲線資料（如成長曲線、溫度變化、交通流量等）。
• 平滑性（smoothness）是核心假設。
❖ 應用領域
• 生物統計、生物醫學、經濟學、氣象學、環境科學、筆跡分析、交通工程等。

二、FDA的目標與挑戰
❖ 目標
• 表現資料、探索變異性、建構模型、比較不同資料組。
• 透過平滑或插值從離散資料轉為函數。
• 進行EDA、主成分分析（FPCA）、函數線性模型（FLM）等。
❖ 挑戰
• 噪音觀測下的函數估計。
• 無窮維函數空間的數值表示。
• 解釋與變異性建模。
• 資料常有 n < p = ∞。

三、函數表示與平滑方法
❖ 從離散資料轉換為函數：
• 優點：可於任意時間評估值、估導數、去除雜訊、統一時間軸。
❖ 方法一：基底展開（Basis Expansion）
• 用固定的 basis 系統（如 Fourier、B-splines）將函數寫成線性組合。
• 最小平方法估計係數。
❖ 方法二：平滑處罰（Smoothing Penalty）
• 加入 roughness penalty，。
• λ 通常使用 GCV（廣義交叉驗證）選取。
❖ 基底系統：
• Fourier basis：週期性資料。
• B-spline basis：非週期性資料，具有良好近似與區域控制特性。
❖ 局部多項式平滑（Local Polynomial Smoothing）
• 使用 kernel 為權重，常見如局部線性迴歸。

四、探索性資料分析（EDA）
❖ 描述統計：
• 平均函數： μ(t)=E[X(t)]\mu(t) = E[X(t)]
• 變異數函數： σ^2(t)= = Var[X(t)]
• 共變異數與相關函數： Cov[X(s),X(t)], Corr[X(s),X(t)]
❖ 主成分分析（FPCA）：
• 以函數共變異數函數做特徵分解。
• 可視化方法包括主成分曲線疊加、FPC scores 的散佈圖。

五、R 語言的 fda 套件簡介
❖ 主要物件
物件功能basis定義 basis 系統fd函數型資料物件bifd二維函數Lfd定義平滑懲罰的微分算子fdPar結合 fd、Lfd 和平滑參數 
❖ 常用函數
• create.fourier.basis(), create.bspline.basis()
• smooth.basis(), pca.fd(), var.fd(), mean.fd()
• fRegress(), fRegress.stderr(), fRegress.CV()

六、函數線性模型（Functional Linear Models, FLM） 
❖ FPCA-Based Regression
• 使用主成分展開的係數作為回歸自變量。

七、實作與練習
❖ 練習題（以 Berkeley Growth Data 為例）
• 用 B-spline 平滑。
• 求平均與共變異函數。
• 做 FPCA、VARIMAX 旋轉。
• 視覺化 FPC scores。
• 解釋主成分與變異性比例。

八、進階應用：基因表達資料聚類
• 使用 FPC scores 搭配 k-centers FC 分群。
• 將基因依功能類別（如 eye-specific、muscle-specific）分群。
