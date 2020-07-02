# 附屬於docker-reverseProxy的V2Ray

這是從屬於 [jim60105/docker-ReverseProxy](https://github.com/jim60105/docker-ReverseProxy) 的 V2Ray 方案\
必須在上述伺服器運行正常後再做

## 說明
### Server
1. 以文字編輯器開啟`.env`，填入以下內容
	* DOMAIN=你的伺服器網域
	* UUID=從 [https://www.uuidgenerator.net/](https://www.uuidgenerator.net/ "https://www.uuidgenerator.net/") 取得一組隨機UUID後填入，和後述Client的UUID應相同
	* EMAIL=你的email
1. `docker-compose up -d`
### Client
1. 以文字編輯器開啟`forClient/config.json`，替換以下所有字串
	* `your.domain.com`: 你的伺服器網域
	* `UUID`: 要和前述Server的UUID相同
1. 以修改完的config.json替換Client端設定檔
1. Client端運行v2ray
1. Client端以SwitchyOmega之類的方式，由SOCKS5://localhost:1080溝通
