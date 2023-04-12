# WebServices_HW_1

#### Проверить все ли нормально в работе связки веб-сервисов

Есть 2 WS  
- WS_1: http://162.55.220.72:5011/user
- WS_2: http://23.88.52.139:5012/users_team  

1. WS_1 получает запрос от клиента

POST
Body: Raw(json) {"user_id": 1}
Вставьте свой уникальный user_id.

2. После получения запроса WS_1 отправляет запрос на WS_2
POST
Body: Raw(json) 
{
	"type": "padawan", 
	"spec": "QA", 
	"ex": "1", 
	"current_user": {
		"uid": YOUR_ID,  //1
		"uip": "YOUR_IP" //"5.152.62.104"
	}
}

3. WS_2 принимает запрос от WS_1, дополняет полученную json дополнительной информацией.
4. WS_2 отправляет ответ на WS_1 в виде
{
	"user_devices_data": {
		"comp": {
			"model": "Macbook",
			"monitor_diagonal": 16,
			"ram": 32,
			"resolusion": [
				"Liquid Retina XDR",
				"3456x2234"
			],
			"ssd": 1000,
			"year": 2021,
		},
		"mobile": {
			"cpu": "ARM, SnapDragon 840",
			"model": "Samsung a52",
			"os": "Android",
			"ram": 6
		}
	},
	"user_static_data": {
		"current_user": {
			"uid": 1,
			"uip": "127.0.0.1"
		},
		"ex": "1",
		"spec": "QA",
		"type": "padawan"
	}
}

5. WS_1 перенаправляет запрос клиенту
