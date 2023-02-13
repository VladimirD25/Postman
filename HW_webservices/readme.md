### Task_1  

1. Проверить всё ли нормально в работает связка вебсервисов.

Есть 2 ws.
WS_1: http://162.55.220.72:5011/user
WS_2: http://23.88.52.139:5012/users_team


2. WS_1 получает запрос от клиента. 
POST. 
Body: json {"user_id":1}
Вставьте свой уникальный user_id.

3. После получения запроса ws_1 отправляет запрос на ws_2
POST. 
Body: json {'type': 'padawan', 'spec': 'QA', 'ex': '1', 'current_user': {'uid': YOUR_ID, 'uip:': ‘YOUR_IP’}}

4. WS_2 принимает запрос от ws_1, дополняет полученную Json дополнительной информацией.
5. WS_2 отправляет ответ на ws_1 в виде 
{
    "user_divices_data": {
        "comp": {
            "model": "Macbook",
            "monitor_diagonal": 16,
            "ram": 32,
            "resolution": [
                "Liquid Retina XDR",
                "3456x2234"
            ],
            "ssd": 1000,
            "year": 2021
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
            "uip:": "127.0.0.1"
        },
        "ex": "1",
        "spec": "QA",
        "type": "padawan"
    }
}
6. Ws_1 перенаправляет запрос клиенту


