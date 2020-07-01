# 附屬於docker-nextcloud的V2Ray

這是從屬於 [jim60105/docker-nextcloud](https://github.com/jim60105/docker-nextcloud) 的 V2Ray 方案\
使用了現存的 [nginx-proxy/nginx-proxy](https://github.com/nginx-proxy/nginx-proxy) 做SSL管理和反代\
必須在上述伺服器運行正常後再做此方案

## 說明
### Server
1. 依序以文字編輯器開啟所有文件，修改以下所有字串
	* your.domain.com: 你的伺服器網域
	* your@email.com: 你的email
	* UUID: 從 https://www.uuidgenerator.net/ 取得一組隨機UUID後填入，所有UUID應相同，格式如`0ee7e35f-bca2-47b9-8948-f74f76aea7c2`
1. 重命名`your.domain.com_location`檔案名稱為: 你的伺服器網域加上`_location`
1. `docker-compose up -d`
### Client
1. 以 [forClient/config.json](forClient/config.json) 替換client端的config.json檔案，記得也要修改上述內容
1. Client端運行v2ray
1. Client端以SwitchyOmega之類的方式和SOCKS5 localhost:1080溝通
