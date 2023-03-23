# V2Ray on Docker

> 這是從屬於 [jim60105/docker-ReverseProxy](https://github.com/jim60105/docker-ReverseProxy) 的 V2Ray 方案\
必須在上述伺服器運行正常後再做

V2Ray 是現在流行的翻牆軟體，可以想為是 VPN 跳板的進化版。VPN 已經可被 GFW 識別封鎖，SS 據說也快不行了，而 V2Ray 能包成在特徵上和一般 https 訪問沒什麼不同，所以不容易識別。從 GFW 的角度來看，你就只是整天盯著同個網站的怪咖。

怪不怪呢? 當然很怪，但又沒有人規定不行。雖然 GFW 沒辦法知道你在做什麼，但從行為上能看出來你很可疑。自己心裡要有個底，和公安喝茶時多帶些伴手禮。

不過我這裡沒有 GFW，我架這個是弄好玩的，純粹當成個人的國外跳板在用囉。

## 部屬

### Server

1. 請參考`.env_sample`建立`.env`
   * DOMAIN=你的伺服器網域
   * UUID=從 [https://www.uuidgenerator.net/](https://www.uuidgenerator.net/ "https://www.uuidgenerator.net/") 取得一組隨機 UUID 後填入，和後述 Client 的 UUID 應相同
   * EMAIL=你的 email
1. `docker-compose up -d`
1. `docker-compose logs -f` 確認沒有錯誤訊息

### Client

1. 在此下載客戶端 [v2fly/v2ray-core](https://github.com/v2fly/v2ray-core/releases/latest)\
   (Windows用戶下載 `v2ray-windows-64.zip`)\
   注意你的 client 版本是 v4 還是 v5，需使用不同的設定檔
1. 依照你的 client 版本以`forClient/config_v4.json`或是`forClient/config_v5.json`取代client端程式目錄下的`config.json`
1. 以文字編輯器開啟`config.json`，替換以下所有字串
   * `your.domain.com`: 你的伺服器網域
   * `UUID`: 要和前述 Server 的 UUID 相同，注意有兩處要替換
1. Client 端運行 v2ray (v5版運行 `v2ray run -format jsonv5`)
1. 瀏覧器以[SwitchyOmega](https://chrome.google.com/webstore/detail/proxy-switchyomega/padekgcemlokbadohgkifijomclgjgif?hl=zh-TW)，由 `SOCKS5://localhost:1080` 溝通\
   ![image](https://user-images.githubusercontent.com/16995691/156827558-7404d795-2ae9-47e8-bcbf-9b0d8e9eda8f.png)
