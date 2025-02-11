# 大型語言模型中階班

一、RPA 與 AI 基礎

[課前安裝軟體](https://www.notion.so/19754713b8fe8041a43df7209e5e86aa?pvs=21)

- RPA技術概述：原理、工具和平臺

- 常見的RPA應用場景和案例

- 自動化與人工智慧應用案例

    - 半自動寫文章

    - 使用 n8n + LINE Notify 來做爬蟲通知：[https://medium.com/@NeroHin/自動化工具-使用-n8n-line-notify-來做爬蟲通知-以研究所獎學金為例-90982259c196](https://medium.com/@NeroHin/%E8%87%AA%E5%8B%95%E5%8C%96%E5%B7%A5%E5%85%B7-%E4%BD%BF%E7%94%A8-n8n-line-notify-%E4%BE%86%E5%81%9A%E7%88%AC%E8%9F%B2%E9%80%9A%E7%9F%A5-%E4%BB%A5%E7%A0%94%E7%A9%B6%E6%89%80%E7%8D%8E%E5%AD%B8%E9%87%91%E7%82%BA%E4%BE%8B-90982259c196)

    - RSS 整理 <https://www.youtube.com/watch?v=M_4AjvLqBiY>

    - 自動化服務之間處理資料，轉換或傳遞數據

        - 設定 TaskRunner 利用 API 觸發器用以自動運行 n8n 工作流程，並使用節點完成工作流程自動化，整合各種服務與應用程式。無需編寫大量程式，在這些自動化服務之間處理資料，轉換或傳遞數據，即時回應處理狀況。
        - TaskRunner 使用 API 提供人工智慧服務，在運行工作任務時，分析資料並透過機器學習功能增強應用程式。
        - 簡化工作流程並減少編寫程序，僅在必要時使用 JavaScript 編寫自訂程序，以提高創建複雜工作流程的速度。

![image](https://github.com/user-attachments/assets/1c703416-5c57-4091-a21a-a1418b192758)



- n8n 簡介

    - n8n 是一個開源的工作流自動化平台，於 2019 年由 Jan Oberhauser 在柏林創建。它允許用戶建立業務流程，並集成和互動超過 1000 個應用程序 [https://n8n.io/integrations/。](https://n8n.io/integrations/%E3%80%82)

    - n8n 的主要功能

        - 低代碼自動化：n8n 提供超過 1100 個以上的的工作流模板 ，並且可以通過 API 連接任何服務。
        - 多步驟工作流：用戶可以創建多步驟的工作流，將不同的工具和服務整合在一起。
        - AI 功能：n8n 添加 AI 功能，例如使用 OpenAI 的 ChatGPT 進行聊天互動等。
        - 地端語言模型推論平台：<https://ollama.com/>, <https://lmstudio.ai/>
    - 如何開始使用 n8n

        - 註冊和設置：n8n 可以作為雲服務、npm 模塊和 Docker 映像使用。新用戶可以免費試用雲服務。
        - 創建新工作流：打開 n8n 後，可以創建一個新的工作流，並添加觸發節點來啟動工作流。
        - 添加節點：例如，可以添加 AI Agent 節點來處理用戶查詢，並使用 OpenAI Chat Model 來生成回應。
    - **觸發節點（Triggers）：**作為工作流的第一個節點，它可以是這個程式的"開始"。 定時執行、從聊天軟體接收一個資訊、在介面上點一下按鈕，這些都可以是觸發節點。

        - 觸發節點每個工作流必然有至少一個觸發節點，不然這個工作流永遠無法被開啟。因為一個工作流不可能無緣無故的自己啟動起來，必須要認為設定這個工作流開始執行的條件，也就是 Trigger。
    - **執行節點（Actions）：**不能作為工作流的第一個節點，它只能被其他執行節點 or 觸發節點觸發執行。 通常我們需要的複雜處理邏輯都是由執行節點完成的。例如在介面上點擊一下 **Test Flow**這個本身也是一種觸發節點。

        - 下面我們以 Gmail 為例子，來詳細說明這兩類節點的區別。

            - n8n 的 Gmail 節點類型中封裝了一個觸發節點，叫做 On Message Received。 節點實際的含義是系統會每分鐘（這個週期可以配置）有沒有收到新的郵件，如果收到，就代表這個節點被觸發了，它就被執行了，自然而然的它的後續節點，以及整個工作流都會開始執行程式。

![image](https://github.com/user-attachments/assets/2302b278-efc1-4ac4-bbc4-d86edbd25d9b)



        - **執行節點：**n8n 中 Gmail 節點類型中封裝了 25 個執行節點。

            - 包括給郵件標籤、刪除郵件、讀取郵件內容、改變郵件的讀取狀態、發送郵件等等所有你能想到的能在介面上進行的操作，n8n 幾乎都可以實現。

            - 收到一封新郵件的通知，就好比在手機上收到了App 的 Push，但是這個時候郵件的具體內容是什麼，並不知道，因為人收到了通知，觸發了後續的動作，所以收到新郵件的通知本身這件事是一個觸發節點。但是讀取郵件內容，是在收到通知之後的行為，這就是一個執行節點，至於讀取之後是否要回復，或者是選擇把郵件直接扔到垃圾箱，這些都是執行節點。大部分情況下，執行節點的數量都是遠多於觸發節點的。

![image](https://github.com/user-attachments/assets/114161c9-7dfe-41b5-bf7f-9829787120ec)



    - **n8n節點功能表的分類**

        | **ㅤ** | **觸發節點（Triggers）** | **執行節點（Actions）** |
        | --- | --- | --- |
        | 外部節點（需要依賴外部服務 API 的節點） | 舉例：Gmail 收到新的郵件，觸發工作流執行; | 舉例：通過 Gmail 寫一封郵件並且發出去; |
        | 自有節點（不依賴外部，或者基於標準協定，如 HTTP/html/os 介面等開發的節點） | 舉例：點擊Test Workflow 按鈕，觸發工作流執行 | 舉例：內建的邏輯節點，比如條件、判斷、迴圈、數據處理等; |

- 建置工作流程

![image](https://github.com/user-attachments/assets/246e1aff-b499-4d89-871e-361d892826cb)



    - Action in an app：外界服務的 API 封裝的節點，比如Google Sheets; 【外部節點】
        - 羅列了市面上眾多的開放服務的節點
        - 每個外部服務的節點都會被分類成【觸發節點】和【執行節點】
    - 數據處理節點：用來做數據的過濾或者轉化【自有節點、執行節點】
    - Flow 節點：主要是條件、迴圈、合併等邏輯操作【自有節點、執行節點】
    - Core 節點：主要是程式節點【自有節點、執行節點】
    - 人工智慧節點【為人工智慧打造的複合型節點，比較特殊】
    - 添加另一個觸發器：【觸發節點】
        - 在 n8n 上面點擊一下運行按鈕，觸發程序運行【自有節點】
        - 外界 API 發來的命令，比如 Gmail 收到一封信件【外部節點】
        - 每天/每小時固定一個時間執行【自有節點】
        - 通過 HTTP 請求觸發任務【自有節點】
        - 由另一個 Workflow 觸發這個任務【自有節點】
        - 由聊天框消息觸發這個程式運行（AI 對話類節點專用）【為人工智慧打造的複合型節點，比較特殊】
        - 文件變更/Email/等等【自有節點】
        - 透過搜巡加功能表的分類，我們就可以很容易找到自己需要的節點了。
        - 節點的本質是對外部服務（比如 Gmail、OpenAI）的公開 API 的封裝，這些封裝能夠帶來 2 個好處：
            - 有一些過於抽象的介面設計會被包裝的更易懂
            - 對於不寫程式的人來說，他們可以不用寫程式就能調用這些公開 API
- n8n 安裝

    - Node.js (跨平台的 JavaScript 執行環境) [NVM](https://github.com/coreybutler/nvm-windows#installation--upgrades)
        1. 下載 [nvm-setup.exe](https://github.com/coreybutler/nvm-windows/releases/download/1.1.12/nvm-setup.exe) 進行安裝

        2. <https://nodejs.org/en/> 下載 <https://nodejs.org/dist/v20.18.0/node-v20.18.0-x64.msi> 安裝檔進行安裝

        3. 在 C:\Users\<Yourname>\AppData\Roaming 資料夾下建立 npm 資料夾

        4. 按開始或放大鏡輸入 cmd 打開命令提示字元後輸入 npx n8n 安裝n8n

       ![image](https://github.com/user-attachments/assets/d78877f2-fb19-40a2-a784-605d73ace15a)


        5. 更新 n8n 軟體 npm update -g n8n

    - Docker ([**250 employees** OR more than **$10 million** in annual revenue requires a paid subscription](https://www.docker.com/pricing/))
        - 基本安裝

            ```
            docker volume create n8n_data
            docker run -it --rm --name n8n -p 5678:5678 -v n8n_data:/home/node/.n8n docker.n8n.io/n8nio/n8n
            ```

        - n8n 更新

            ```
            docker pull [docker.n8n.io/n8nio/n8n](<http://docker.n8n.io/n8nio/n8n>)
            ```

        - 設定時區，預設式 America/New_York 改為 Asia/Taipei

            - 請根據自己的帳號修改：<你的用戶名>

                ```
                docker run -it --rm --name n8n -p 5678:5678 -v n8n_data:/home/node/.n8n -v /c/Users/<你的用戶名>/Downloads:/home/node/downloads -e GENERIC_TIMEZONE="Asia/Taipei" -e TZ="Asia/Taipei" docker.n8n.io/n8nio/n8n
                ```

            - `-rm`：在容器停止後自動移除容器。

            - `-name n8n`：命名容器為 `n8n`。

            - `p 5678:5678`：將主機的 5678 端口映射到容器的 5678 端口。

            - `v n8n_data:/home/node/.n8n`：將名為 `n8n_data` 的 Docker 卷掛載到容器內的 `/home/node/.n8n` 路徑。

            - `e GENERIC_TIMEZONE="Asia/Taipei"` 和 `e TZ="Asia/Taipei"`：設置容器的時區為台北時間。

            - `docker.n8n.io/n8nio/n8n`：使用 n8n 的 Docker 映像。

            - 將 Windows 下載資料夾掛載到 Docker 容器中的 `/home/node/downloads`

- 開啟 n8n 的二因素驗證

    - 在 n8n 裡開啟二階段驗證。 由於 n8n 支援安裝第三方 npm 節點，因此駭客如果攻破了你的 n8n 不止能夠隨意刪改你的 n8n Workflow，還有可能直接攻破你的伺服器，控制一切。

![image](https://github.com/user-attachments/assets/133ab0cd-fd7c-4222-940c-6c34aaf1e98b)



    - 使用 Google Authenticator 掃描 QR code 後輸入6位數字進行驗證

![image](https://github.com/user-attachments/assets/52bebd19-97ae-4f11-a8a3-5f1d0be738fa)





    - 存下恢復碼

![image](https://github.com/user-attachments/assets/fc21f0b9-e2d2-42e9-bc35-31e5e3cd5611)



- 資料處理

    - 處理不同的資料類型（例如，XML、HTML、日期、時間和二進位資料）。
    - 合併來自不同來源（例如資料庫、電子表格CRM）的資料。
    - Code/HTTP Request
        - Code 節點
            - Mode：選擇 Code 節點的運行方式，分為 Run Once for All items 和 Run Once for Each Item。當上游傳來一組資料的時候，Code 節點是整組資料運行一次，還是每行資料運行一次。
                - 比如說，如果你 Code 是要給一組資料中整體進行操作（增減一行，刪除一列），你就選 Run Once for All items。
                - 如果你想讓 Code 是要針對一組資料中的每一行進行操作（每行中的某個字段做下修改），你就選 Run Once for Each Item。
            - Language：設定 Code 節點編寫程式碼的語言，分為 JavaScripts 和 Python。 n8n 在執行 JavaScripts 程式時更穩定。 如果你不會這兩種語言，在用 ChatGPT 結對編寫 Workflow，建議選擇 JavaScripts。
        - **注意事項：**
            - Code 節點預設只引用了少數的 JavaScripts 庫，如需使用更多庫，可參閱官方文檔： Code 節點不支援向本地伺服器讀取或寫入檔，你需要先用 Read File（s） From Disk 或 Write File to Disk 節點來處理讀取和寫入的步驟。
            - Code 節點不支援發起 HTTP 請求，你需要使用 HTTP Request 節點來處理遠端請求。 Code 節點的 Python 移植自 Pyodide，這意味著它僅包含極少數的庫，且性能較差。
    - HTTP Request：節點在各種情況下都非常有用。
        - 常見的使用場景包括：從 API 獲取數據：許多雲服務（如天氣預報、股市資訊、社交平台等）都提供 API 來訪問其資料。使用 HTTP Request 節點，你可以在 n8n 中直接調用這些 API，從而獲取你需要的資料。
        - 提交資料到 API：除了獲取資料，你也可以使用 HTTP Request 節點將資料提交到 API。 例如，你可能需要向某個服務提交表單資料，或者向某個資料庫 API 提交新的記錄。
        - 觸發網頁爬蟲：如果你正在執行一個網頁爬蟲，你可以使用 HTTP Request 節點來觸發爬蟲程式，從而抓取網頁上的資料。
        - 如果你希望使用的某個在雲服務沒有在 n8n 中，你可以使用 HTTP Request 節點來與該服務進行交互。 只要這個服務提供了 API，你就可以通過發送 HTTP 請求來調用這個 API，從而實現與該服務的互動。
    - 錯誤和異常處理策略
- OpenAI 及 LangChain

    - API：即應用程式介面，是一套規定了軟體元件之間交互的規則。 它允許不同的軟體系統之間進行通信，交換資料和功能。 簡單來說，ChatGPT 是 OpenAI 做來給你（人類）使用的介面，GPT-4 API 是 OpenAI 做來給其他程式（機器）使用的介面，n8n 是一個程式，因此在 n8n 系統中接入 AI 需要對應 AI 的 API。不同的 AI 在註冊開發者帳號上略有不同，由於涉及比較敏感的內容。

    - LangChain 是一種 python 套件用於大語言模型的交互，專門為了將大語言模型溝通而設計。 它可以將各種大語言模型（如 GPT-4、Gemini Pro 或 Claude 3）的 API 進行統一，使得我們在編寫 AI 相關的程式時可以方便的使用不同的大語言模型進行各種任務，無需關心模型之間的差異性。 簡單來說，LangChain 就是在 AI 和程式之間的一個「溝通的橋樑」。

    - 在 n8n 中，LangChain 是一個包含子節點的 AI 節點。 在你更換不同的 AI 服務時，可以不用重新設置所有的節點設置，大幅提高我們調試 Workflow 的效率。

    - 在 n8n 中，Advaced AI 是一個專門的 node 類別，其下有多種不同的 AI 類型。 在這裡，我們會詳細介紹兩個最常用的 AI 節點，讓你掌握 AI 在 n8n 中的接入邏輯。

![image](https://github.com/user-attachments/assets/c75528bc-1beb-4a24-bf35-37a7e4122d57)



        - 大部分的 AI 節點都在介紹里寫明瞭自己的用處是什麼，你還可以點擊 AI Templates 從官方社區下載別人已經組合好的 Chain。

![image](https://github.com/user-attachments/assets/f4c3e0bf-4f7e-4137-badd-6ac59f9067d6)



    - **Basic LLM Chain：**節點是用於連接大語言模型的最簡單節點。 它不適合用來做 Agent，也不太適合用來做對話。 特別適合那種做一次性的文本處理與判斷。

        - 比如：文本總結、文本摘要、語法糾正、文本分類等等。
        - 它的節點內邏輯非常簡單：從上游節點獲取資料、將參數設置中的 prompt 和資料一同提交給 Large Language Model (LLM) API、從 API 獲得 LLM 傳回的結果。
    - **參數說明**

        - **Prompt (必填)**：這是一個選項類的參數
        - **Chat Messages (可選) （If Using a Chat Model）**：
            - 如果你在使用一個專門為聊天設計的模型，並且打算做一個對話型應用，這裡可以添加聊天提示。 這允許節點處理上下文更豐富的對話，提高回答的相關性和準確性。
            - 你可以在這裡添加已預製的對話 Prompt，它的子參數包括 Type Name or ID（角色）、Message Type（圖片、文字、URL）和 Message（對話內容）。
            - 你在一個角色扮演的情況下，用於類比一個對話場景的中途。 這樣，當你在 Workflow 開始執行，相當於使用者是從這個場景的中途開始與 AI 對話。
            - System prompt：給 AI 角色扮演的 prompt
            - User prompt：使用者的輸入資訊
            - AI prompt：AI 回應
                - 例如：要 AI 進行翻譯
                    - System prompt：You are a summary agent, always summarize the text in "zh-Tw" language, with the most unique and helpful points, into a numbered list of key points and takeaways. Must reply in "traditional chinese."
                    - User prompt：為輸入文字
    - **Chat Trigger**： 這是 n8n 中的一個特殊的觸發器，它允許你通過一個聊天視窗觸發 Workflow。 它的消息會默認傳遞給下一層的 AI 節點。

        - Chat Trigger 沒有參數設置，只要在畫布中創建，就會將 Workflow 更改為聊天觸發。
        - Chat Trigger 的觸發方式是，每發送一次消息，完整觸發一次 Workflow。
        - 在下游 AI 節點沒有加入 Memory 服務的情況下，Chat Trigger 每次觸發都會忘記上次的對話，也就是說它預設不具備上下文能力，AI 不會記得你上一句話說了什麼。
        - 當添加 Chat Trigger 時，n8n 會提示這個觸發器需要與 AI 節點連接。 實際上，這並不是必須的。 你完全可以將 Chat Trigger 作為輸入觸發器。 比如，你的一個 Workflow 需要從資料庫中篩選指定日期的文章。 你可以通過 Chat Trigger 來輸入這個日期，並在後續的篩選中引用這個輸入的日期進行篩選，而無需在每次運行時修改篩選條件。
    - **AI Agent**

        | **選項** | **支援模組** | **簡單說明** |
        | --- | --- | --- |
        | **Tools Agent** | Memory/Tool | 用自然語言操作一個工具，比如你可以用它來讓 AI 算數，因為對於大語言模型來說，計算機就是一個工具。 該模式不支援上下文記憶。 |
        | **Conversational Agent** | Memory/Tool | 用於完成對話的模式，和 Basic LLM Chain 比增加了 Memory 和 Tool 模組，你可以為對話添加上下文記憶功能，還可以接入額外的工具，比如搜尋或天氣預報 |
        | **OpenAI Functions Agent** | Memory/Tool | 專門用於發起 Function Call 的模組 |
        | **Plan and Execute Agent** | Tool | 自然語言調用工具的模型，允許連接多個工具，由 AI 自行計畫使用哪些工具以及如何組合。 |
        | **ReAct Agent** | Memory/Tool | Plan and Execute Agent 的進階版本， AI 會根據你的自然語言任務，選擇合適的工具執行任務，然後再檢查工具返回的結果，如果結果不正確，就再試試其他方法。 該模式可能會對 AI 發起多次請求。 |
        | **SQL Agent** | Memory | 直接與 Sql 資料庫對話。 |

    - 不同類型的 Agent 有不同的必填參數，你可以在配置頁面查看，或者閱讀相關類型 Agent 的官方節點。

        - **Memory：**AI Agent 節點的部分任務類型支援使用 Memory 子節點，這個子節點的作用是為 AI 進行上下文記憶。 這裏同時指一次性的記憶和永久的記憶。
        - 該節點支援以下類型的記憶服務：
            - **Window Buffer Memory** - 瀏覽器視窗緩存記憶，顧名思義，你不需要部署任何額外的服務，直接把對話的上下文存在瀏覽器裡。 但缺點也很明顯：更新就消失了，不能永久保存。
            - **Motorhead -** 一個專門為 AI 打造的開源記憶服務，它能簡單的説明 AI 服務存儲、向量化和檢索記憶，有開源版本。
            - **Postgres Chat Memory** - 是一個免費的開源=資料庫管理系統 （RDBMS），強調可擴展性。
            - **Redis Chat Memory** - 將聊天記錄存儲在伺服器的 Redis 緩存伺服器裡，可以在刷新瀏覽器視窗後找回之前的記憶，但這也是短時記憶，因為 Redis 會根據設置在指定的時間後清空緩存。
            - **Xata** - 一個專門為 AI 打造的無伺服器資料檢索系統，它不開源，付費可用，無需部署。 相當於你在別人的雲服務裡買了個可直接連接的資料庫，填寫授權即可存儲、處理、讀取數據。
            - **Zep -** 和 Xata 差不多，另一個專門為 AI 打造的長期記憶服務商，不開源，要付費，免部署。
    - **Tool：**你可以看到，在添加一個 tool 之後，你向 AI 發出的請求，會經過 tool 的調用再返回。 右邊log裡畫圈的部分，能讓你更直觀的理解為什麼叫"LangChain"。

    - AI Agent 節點的部分任務類型支援使用 Tool 子節點，這個子節點是用來執行那些特定非 AI 任務的。 比如：計算機、搜尋網站頁面、從維基百科獲取相關資訊等。

    - 目前，n8n 支援以下幾種類型的 Tool 子節點：

        - **Calculator -** 計算機，顧名思義，用傳統方法進行數字計算，避免你的大模型出現"1+1=8"的智障行為。
        - **Custom Code Tool -** 你自己寫一段代碼作為一個工具讓 AI 調用，支援 JavaScript 和 Python。
        - **SerpAPI -** Google 搜尋 API，如果你希望你的 AI 節點能聯網查資料，主要就靠它。 申請 SerpAPI 的方法參見這裡：<https://serpapi.com/search-api>
        - **Wikipedia** - 從 Wikipedia 獲取相關資訊，這樣可以避免模型在不知道相關主題的情況下依據幻覺編造。
        - **Wolfram Alpha -** 一個國外很流行的更偏向學術的問答搜尋引擎，比 Google 的資訊品質更高，並且支援高級數學提問回傳函數影像等等。
        - **Custom n8n Workflow Tool -** 將另一個 n8n Workflow 作為一個 Tool 來調用。
    - OpenAI 提供的各種API（如ChatGPT, DALL-E）

    - OpenAI 文字、影像、聲音應用

- 地端模型：Taide / Taiwan LLM / Breeze

    ```
    # Meta Llama 3.2 3B
    ollama run llama3.2

    # Google Gemma-2 2b
    ollama run gemma2:2b

    # Taide 模型
    ollama run adsfaaron/llama3-taide-lx-8b-chat-alpha:q5_k_m

    # Taiwan LLM
    ollama run wangrongsheng/taiwanllm-7b-v2.1-chat

    # MKT breeze
    ollama run ycchen/breeze-7b-instruct-v1_0
    ```

- 地端語言模型推論 Ollama

    Ollama Base URL：<http://127.0.0.1:11434> / <http://host.docker.internal:11434> (Docker)

    [AI_agent_ollama.json](https://prod-files-secure.s3.us-west-2.amazonaws.com/4a2f169b-da02-4121-8ba8-bc36de3803ae/bf478086-412e-429a-92fc-7fc19bb6db4e/AI_agent_ollama.json)

- OpenAI Whisper 語音轉文字

    [OpenAI_Whisper.json](https://prod-files-secure.s3.us-west-2.amazonaws.com/4a2f169b-da02-4121-8ba8-bc36de3803ae/f31cd58b-1562-49a8-a36f-75c6718ec7db/OpenAI_Whisper.json)

- OpenAI Whisper 語音轉文字 + 語音重點整理輸出

    [OpenAI_Whisper_summarize.json](https://prod-files-secure.s3.us-west-2.amazonaws.com/4a2f169b-da02-4121-8ba8-bc36de3803ae/18007e8d-cb74-414e-a5ca-7579655ffb14/OpenAI_Whisper_summarize.json)

參考資料：

- n8n 文件：<https://docs.n8n.io/>
- n8n 模板：<https://n8n.io/workflows/>
- <https://www.youtube.com/@n8n-io>
- n8n 討論社群：<https://community.n8n.io/>
