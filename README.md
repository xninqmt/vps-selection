# VPS 購買：看懂規格、線路與計費週期，用 DMIT 洛杉磯／香港／東京方案示範從選型到下單

買 VPS 最容易出錯的地方不在付款那一刻，而在付款之前。

「1 核 2G、20GB SSD、每月 1TB 流量」這種規格表，十家商家有八家長得差不多。但同樣的數字，一台機器能穩定跑三年，另一台每天晚八點準時開始掉包。差別不在規格欄，而在線路類型、超售程度，以及商家對「流量用完」和「IP 被牆」的處理方式。

以下用 DMIT 這家在中文 VPS 圈討論度不低的商家當實例，把 VPS 購買時真正需要判斷的幾件事拆開講，最後附上它目前三個機房的方案價格對照與下單流程。

## 買之前先想清楚三件事

**機房位置決定延遲的物理下限。** 這是沒辦法用錢繞過去的。洛杉磯到中國大陸的延遲普遍在 150–200ms，香港可以壓到 50ms 以內，東京介於中間。如果你的使用者主要在大陸，香港的物理距離優勢比任何優化線路都直接；但如果只是自己跑腳本、放監控或面向海外使用者，美西的年付價格通常便宜一大截。

**線路要對應你的寬頻商。** 同一家商家的「中國優化」標籤底下，其實常見三種東西：走中國電信 CN2 GIA 的、走中國移動 CMIN2 與聯通 9929 的、以及什麼都不優化的國際 BGP。電信用戶買了只優化移動的方案，錢花了但體驗不會變好。反過來也一樣。

**計費週期是折扣開關。** 月付最貴但最靈活，年付單價低但等於綁一年。很多低價入門機型甚至只開放季付或年付，月付選項直接被拿掉。如果你只是想試線路，季付通常是折衷點。

## VPS 購買時最容易踩的四個坑

**超售。** 母雞塞太多小雞，是低價 VPS 掉速最常見的原因。多篇第三方評測都提到 DMIT 不超售、效能穩定，這類說法可以當作參考指標，但沒有一家商家會承諾「保證不掉速」，實際還是要看你的使用時段。

**流量用完直接斷網。** 這點差別很大。DMIT 的作法是超量後不停機，降速繼續跑：Pro 系列降到 4–10Mbps 不等，T1 系列依方案降到 100Mbps 甚至 1Gbps。對偶爾爆流量的站點來說，這比直接斷線友善很多。

**IP 被牆之後怎麼辦。** DMIT 有條件式的免費更換 IP 機制，另外也可付費更換。不過第三方整理的具體條件說法並不一致（有的寫每 15 天一次免費、有的寫需要開機滿 7 天且每 IP 限一次），這種會變動的政策，下單前直接看官網說明比較穩。

**硬體世代。** DMIT 目前同時並存 AS3（AMD EPYC 7003）、AN4（EPYC 9004）、AN5（EPYC 9005）三個平台，庫存與報價經常變動。其中 AS3 官方自己在定價頁提醒：平台仍處於建設與優化階段，磁碟效能與 SLA 可能低於成熟平台。要放正式業務的話，這行字值得先看一遍。

## DMIT 的三種網路，差別在哪

| 網路系列 | 主要線路 | 適合誰 | 價格定位 |
| --- | --- | --- | --- |
| Pro（Premium） | 三網回程 CN2 GIA，電信去程 CN2 GIA、聯通 9929、移動 CMIN2 | 电信用戶、對大陸訪問品質要求高的建站與業務 | 最貴 |
| EB（Eyeball） | 三網回程 CMIN2，電信／聯通回程走 9929 | 移動、聯通用戶，想要大流量與高頻寬 | 中間 |
| T1（Tier 1） | 國際 BGP，不含中國大陸優化 | 海外業務、開發測試、只需要一個國外 IP | 最便宜，流量與端口最大 |

選購邏輯可以簡化成一句：先看你的使用者用哪家寬頻，再看你能接受多少錢，最後才比規格。

## DMIT 方案與價格對照

以下價格與規格整理自官方價目頁可對照的第三方資料，以美元計價，庫存與售價變動頻繁，實際金額請以結帳頁顯示為準。

### 美國洛杉磯 LAX（AS3 平台）

| 方案 | CPU | 記憶體 | SSD | 月流量／頻寬 | 超量後 | 價格 | 購買 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| LAX.AS3.Pro.TINY | 1 核 | 2GB | 20GB | 1000GB @ 1Gbps | 4Mbps 不限量 | $10.90/月 | [ 選 TINY 入手 CN2 GIA](https://www.dmit.io/aff.php?aff=12046&pid=253) |
| LAX.AS3.Pro.Pocket | 2 核 | 2GB | 40GB | 1500GB @ 4Gbps | 4Mbps 不限量 | $16.90/月 | [ 查看 Pocket 方案](https://www.dmit.io/aff.php?aff=12046&pid=254) |
| LAX.AS3.Pro.STARTER | 2 核 | 2GB | 80GB | 3000GB @ 10Gbps | 4Mbps 不限量 | $34.90/月 | [ 查看 STARTER 方案](https://www.dmit.io/aff.php?aff=12046&pid=255) |
| LAX.AS3.Pro.MINI | 4 核 | 4GB | 80GB | 5000GB @ 10Gbps | 8Mbps 不限量 | $62.90/月 | [ 查看 MINI 方案](https://www.dmit.io/aff.php?aff=12046&pid=256) |
| LAX.AS3.Pro.MICRO | 4 核 | 4GB | 160GB | 7000GB @ 10Gbps | 8Mbps 不限量 | $87.90/月 | [ 查看 MICRO 方案](https://www.dmit.io/aff.php?aff=12046&pid=257) |
| LAX.AS3.Pro.MEDIUM | 6 核 | 8GB | 160GB | 14000GB @ 10Gbps | 10Mbps 不限量 | $199.90/月 | [ 查看 MEDIUM 方案](https://www.dmit.io/aff.php?aff=12046&pid=258) |
| LAX.AS3.T1.WEE | 1 核 | 1GB | 20GB | 1000GB @ 4Gbps | 100Mbps 不限量 | $36.90/年 | [ 用年付價入手最便宜的洛杉磯方案](https://www.dmit.io/aff.php?aff=12046&pid=270) |
| LAX.AS3.T1.TINY | 1 核 | 1GB | 20GB | 2000GB @ 4Gbps | 100Mbps 不限量 | $6.90/月 | [ 查看 T1 TINY](https://www.dmit.io/aff.php?aff=12046&pid=271) |
| LAX.AS3.T1.STARTER | 1 核 | 2GB | 40GB | 4000GB @ 10Gbps | 100Mbps 不限量 | $12.90/月 | [ 查看 T1 STARTER](https://www.dmit.io/aff.php?aff=12046&pid=272) |
| LAX.AS3.T1.MINI | 2 核 | 2GB | 60GB | 8000GB @ 10Gbps | 100Mbps 不限量 | $21.90/月 | [ 查看 T1 MINI](https://www.dmit.io/aff.php?aff=12046&pid=273) |
| LAX.AS3.T1.MICRO | 4 核 | 4GB | 120GB | 16000GB @ 10Gbps | 200Mbps 不限量 | $32.90/月 | [ 查看 T1 MICRO](https://www.dmit.io/aff.php?aff=12046&pid=274) |

洛杉磯的 EB 系列（三網回程 CMIN2）與 Pro 同批補貨時同樣有 TINY／Pocket／STARTER／MINI／MICRO／MEDIUM 六個檔位，價格與 Pro 同級或略低，但補貨節奏比 Pro 更不固定，經常一批放完就缺。想蹲 EB 的話直接看結帳頁最準：[👉 查看洛杉磯目前所有可下單方案](https://www.dmit.io/aff.php?aff=12046)。

### 中國香港 HKG（AS3 平台）

| 方案 | CPU | 記憶體 | SSD | 月流量／頻寬 | 價格 | 購買 |
| --- | --- | --- | --- | --- | --- | --- |
| HKG.AS3.T1.WEE | 1 核 | 1GB | 20GB | 1000GB @ 4Gbps | $36.90/年 | [ 香港最低價入門](https://www.dmit.io/aff.php?aff=12046&pid=197) |
| HKG.AS3.T1.TINY | 1 核 | 1GB | 20GB | 2000GB @ 4Gbps | $6.90/月 | [ 查看香港 T1 TINY](https://www.dmit.io/aff.php?aff=12046&pid=198) |
| HKG.AS3.T1.STARTER | 1 核 | 2GB | 40GB | 4000GB @ 10Gbps | $12.90/月 | [ 查看香港 T1 STARTER](https://www.dmit.io/aff.php?aff=12046&pid=199) |
| HKG.AS3.T1.MINI | 2 核 | 2GB | 60GB | 8000GB @ 10Gbps | $21.90/月 | [ 查看香港 T1 MINI](https://www.dmit.io/aff.php?aff=12046&pid=200) |
| HKG.AS3.T1.MICRO | 4 核 | 4GB | 80GB | 16000GB @ 10Gbps | $32.90/月 | [ 查看香港 T1 MICRO](https://www.dmit.io/aff.php?aff=12046&pid=201) |
| HKG.AS3.T1.MEDIUM | 4 核 | 8GB | 160GB | 32000GB @ 10Gbps | $49.90/月 | [ 查看香港 T1 MEDIUM](https://www.dmit.io/aff.php?aff=12046&pid=202) |
| HKG.AS3.T1.LARGE | 8 核 | 16GB | 320GB | 64000GB @ 10Gbps | $99.90/月 | [ 查看香港 T1 LARGE](https://www.dmit.io/aff.php?aff=12046&pid=203) |
| HKG.AS3.T1.GIANT | 8 核 | 24GB | 640GB | 128000GB @ 10Gbps | $199.90/月 | [ 查看香港 T1 GIANT](https://www.dmit.io/aff.php?aff=12046&pid=204) |
| HKG.AS3.Pro.TINY | 1 核 | 1GB | 20GB | 500GB @ 1Gbps | $39.90/月 | [ 香港 CN2 GIA 入門](https://www.dmit.io/aff.php?aff=12046&pid=265) |
| HKG.AS3.Pro.STARTER | 1 核 | 2GB | 40GB | 1000GB @ 1Gbps | $79.90/月 | [ 查看香港 Pro STARTER](https://www.dmit.io/aff.php?aff=12046&pid=266) |
| HKG.AS3.Pro.MINI | 2 核 | 4GB | 60GB | 1500GB @ 1Gbps | $126.90/月 | [ 查看香港 Pro MINI](https://www.dmit.io/aff.php?aff=12046&pid=267) |
| HKG.AS3.Pro.MICRO | 4 核 | 4GB | 80GB | 2000GB @ 1Gbps | $179.90/月 | [ 查看香港 Pro MICRO](https://www.dmit.io/aff.php?aff=12046&pid=268) |
| HKG.AS3.Pro.MEDIUM | 4 核 | 8GB | 160GB | 2500GB @ 1Gbps | $239.90/月 | [ 查看香港 Pro MEDIUM](https://www.dmit.io/aff.php?aff=12046&pid=269) |

香港是三個機房裡價格最硬的一個，Pro 入門就要 $39.90/月，是洛杉磯 Pro 入門的近四倍。原因不難理解：香港 CN2 GIA 的頻寬成本本身就高。另外香港的 EB 系列補貨狀況比洛杉磯更不穩定，時有整批下線的情況，看到有貨建議當下就決定。

### 日本東京 TYO（AS3 平台）

| 方案 | CPU | 記憶體 | SSD | 月流量／頻寬 | 價格 | 購買 |
| --- | --- | --- | --- | --- | --- | --- |
| TYO.AS3.Pro.TINY | 1 核 | 1GB | 20GB | 500GB @ 1Gbps | $21.90/月 | [ 東京 CN2 GIA 入門](https://www.dmit.io/aff.php?aff=12046&pid=138) |
| TYO.AS3.Pro.STARTER | 1 核 | 2GB | 40GB | 1000GB @ 1Gbps | $39.90/月 | [ 查看東京 Pro STARTER](https://www.dmit.io/aff.php?aff=12046&pid=139) |
| TYO.AS3.Pro.MINI | 2 核 | 2GB | 60GB | 2000GB @ 1Gbps | $79.90/月 | [ 查看東京 Pro MINI](https://www.dmit.io/aff.php?aff=12046&pid=140) |
| TYO.AS3.Pro.MICRO | 4 核 | 4GB | 80GB | 4000GB @ 1Gbps | $159.90/月 | [ 查看東京 Pro MICRO](https://www.dmit.io/aff.php?aff=12046&pid=141) |
| TYO.AS3.Pro.MEDIUM | 4 核 | 8GB | 160GB | 5000GB @ 1Gbps | $259.90/月 | [ 查看東京 Pro MEDIUM](https://www.dmit.io/aff.php?aff=12046&pid=142) |
| TYO.AS3.Pro.LARGE | 8 核 | 16GB | 320GB | 8000GB @ 1Gbps | $429.90/月 | [ 查看東京 Pro LARGE](https://www.dmit.io/aff.php?aff=12046&pid=143) |
| TYO.AS3.Pro.GIANT | 8 核 | 24GB | 640GB | 15000GB @ 1Gbps | $799.90/月 | [ 查看東京 Pro GIANT](https://www.dmit.io/aff.php?aff=12046&pid=144) |
| TYO.AS3.T1.TINY | 1 核 | 1GB | 20GB | 2000GB @ 4Gbps | $6.90/月 | [ 查看東京 T1 TINY](https://www.dmit.io/aff.php?aff=12046&pid=131) |
| TYO.AS3.T1.STARTER | 1 核 | 2GB | 40GB | 4000GB @ 10Gbps | $12.90/月 | [ 查看東京 T1 STARTER](https://www.dmit.io/aff.php?aff=12046&pid=132) |
| TYO.AS3.T1.MINI | 2 核 | 2GB | 60GB | 8000GB @ 10Gbps | $21.90/月 | [ 查看東京 T1 MINI](https://www.dmit.io/aff.php?aff=12046&pid=133) |
| TYO.AS3.T1.MICRO | 4 核 | 4GB | 80GB | 16000GB @ 10Gbps | $32.90/月 | [ 查看東京 T1 MICRO](https://www.dmit.io/aff.php?aff=12046&pid=134) |
| TYO.AS3.T1.MEDIUM | 4 核 | 8GB | 160GB | 32000GB @ 10Gbps | $49.90/月 | [ 查看東京 T1 MEDIUM](https://www.dmit.io/aff.php?aff=12046&pid=135) |
| TYO.AS3.T1.LARGE | 8 核 | 16GB | 320GB | 64000GB @ 10Gbps | $99.90/月 | [ 查看東京 T1 LARGE](https://www.dmit.io/aff.php?aff=12046&pid=136) |
| TYO.AS3.T1.GIANT | 8 核 | 24GB | 640GB | 128000GB @ 10Gbps | $199.90/月 | [ 查看東京 T1 GIANT](https://www.dmit.io/aff.php?aff=12046&pid=229) |

東京的 EB 系列（TYO.AS3.EB）已在先前整批下架，目前想買東京只能從 Pro 與 T1 兩條線挑。

### 不定期補貨的限量特價機型

DMIT 另外會週期性放出限量特價機，規格通常比同價位常規方案縮水，但單位價格明顯更低，賣完就等下一批：

| 特價機型 | 規格概略 | 價格 | 購買 |
| --- | --- | --- | --- |
| LAX.Pro.MALIBU | 1 核／1GB／20GB，1TB @ 1Gbps | $49.9/年 | [ 搶洛杉磯 GIA 特價機](https://www.dmit.io/aff.php?aff=12046&pid=186) |
| LAX.EB.WEE | 1 核／1GB／20GB，1000GB @ 1Gbps | $39.9/年 | [ 搶洛杉磯 CMIN2 特價機](https://www.dmit.io/aff.php?aff=12046&pid=188) |
| LAX.EB.CORONA | 1 核／1GB／20GB，1500GB @ 2Gbps | $49.9/年 | [ 查看 CORONA 方案](https://www.dmit.io/aff.php?aff=12046&pid=218) |
| LAX.EB.FONTANA | 2 核／2GB／40GB，2500GB @ 4Gbps | $100/年 | [ 查看 FONTANA 方案](https://www.dmit.io/aff.php?aff=12046&pid=219) |
| LAX.Pro.PalmSpring | 2 核／2GB／40GB，2000GB @ 2Gbps | $100/年 | [ 查看 PalmSpring 方案](https://www.dmit.io/aff.php?aff=12046&pid=182) |

這類機型的庫存是最不確定的部分，第三方整理的補貨紀錄顯示，同一個方案常在數小時內售完。真正想買的時候，直接看官網當下狀態最快：[👉 查看 DMIT 目前所有可下單方案與即時庫存](https://www.dmit.io/aff.php?aff=12046)。

## 優惠碼怎麼用，能省多少

第三方整理的 DMIT 優惠碼裡，有兩組是長期掛在網路上的年付／半年付折扣，適用於 T1 這類標準網路系列：

- `Lite-Annually-Recur-30OFF`：年付 7 折
- `Lite-Semi-Annually-Recur-20OFF`：半年付 8 折

另外幾組聖誕檔期的促銷碼（例如 `2025-XMAS-LAX-PRO-EB-10-OFF-RECURRING` 這類）是節慶活動期間發出的循環折扣碼，是否仍有效要看當期活動，不建議當成常態優惠來算預算。也有第三方文章提到洛杉磯部分方案在年付時會直接在結帳頁顯示折扣、不需要輸入優惠碼。

用法很單純：選好方案與計費週期後，在結帳頁的優惠碼欄位填入，按「Validate Code」驗證，通過才會反映在帳單金額上。不同代碼對應不同產品線與付款週期，填錯不會生效——驗證鍵按下去那一刻就是答案。

## 下單流程實際怎麼走

1. 從上方表格挑一個方案，進入該方案的訂購頁。
2. 選計費週期（月付／季付／半年付／年付），週期會直接影響單價與是否觸發折扣。
3. 在訂購頁設定主機名稱、root 密碼、作業系統，並確認機房位置。
4. 填入優惠碼並按 Validate Code 驗證。
5. 選付款方式。DMIT 支援支付寶、微信支付、PayPal 與信用卡，對沒有外幣卡的使用者比較友善，也提供中文客服工單。
6. 付款完成後等開通郵件，內容會包含 IP、SSH 連接埠與登入資訊。

第一次買的話，建議先選季付或半年付試一個計費週期，確認你所在的地區、你所用的寬頻商，連到這台機器的實際延遲與尖峰時段表現是否符合預期，再考慮轉年付。

## 常見問題

**流量用完了會怎樣？**
不會斷網，會降速繼續跑。降速幅度依方案不同，Pro 系列大致在 4–10Mbps，T1 系列從 100Mbps 到 1Gbps 都有。實際數值看方案說明。

**Pro 和 EB 該選哪個？**
電信使用者優先看 Pro，移動與聯通使用者看 EB 通常更划算。兩者的差價在洛杉磯不算大，在香港則差得很明顯。

**T1 比較便宜，是不是更划算？**
不是同一類產品。T1 是國際 BGP，不含中國大陸優化，電信用戶買了可能比洛杉磯還慢。它的價值在流量大、端口大、價格低，適合面向海外使用者的業務或純測試用途。

**可以只買一個月試線路嗎？**
部分入門機型已經取消月付，最低從季付起。想試的話，先確認該方案當下是否開放月付。

**能加購 IP 或升級配置嗎？**
部分方案支援，價格依官方頁面為主。這類加購項目不建議事先規劃得太精細，開通後在控制台看實際選項更準。

## 結論：先確定線路，再比價格

如果你的使用者主要在中國大陸，VPS 購買的判斷順序是：先確認自己或客戶用哪家寬頻 → 對應選 Pro 或 EB → 再看機房（香港最快、洛杉磯最便宜、東京居中）→ 最後才比 CPU 與記憶體。把這個順序顛倒過來，很容易買到一台規格漂亮但實際連線體驗一般的機器。

預算抓得緊、只是想有個穩定的國外節點，LAX.AS3.T1.WEE 的 $36.90／年是全系列裡最低的入場價；要在美西拿到 CN2 GIA 又想控制成本，LAX.AS3.Pro.TINY 的 $10.90／月是目前門檻最低的一檔：[👉 用最低門檻入手洛杉磯 CN2 GIA 方案](https://www.dmit.io/aff.php?aff=12046&pid=253)。至於香港，$39.90／月的 Pro 入門是為了延遲付的溢價，值得不值得，取決於那 100ms 對你的業務重不重要。
