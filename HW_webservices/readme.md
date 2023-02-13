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

### Task_2

Проверить всё ли нормально в работает связка веб сервисов.

Есть 2 ws.
WS_1 - 162.55.220.72:5021
WS_2 -  23.88.52.139:5022
—---------
Endpoint /jobs
162.55.220.72:5021/jobs
GET. 
WS_1 получает запрос от клиента. 
При отправке запроса из Postman никаких параметров не нужно
WS_1 парсит json который храниться на файловой системе сервера. Внутри этого json лежит 7 вакансий.
WS_1 возвращает клиенту json в котором будет 7 вакансий.
—-------
Endpoint /jobs
162.55.220.72:5021/jobs
POST. 
WS_1 получает запрос от клиента.
В теле запроса должен быть json {“job_id”: 1}
После получения запроса ws_1 парсит json, в которой 7 вакансий и отправляет запрос на ws_2
23.88.52.139:5022/get_job
В теле запроса должен быть json {“job_id”: 1, “j_data”:  json}
WS_2 получает запрос от WS_1
WS_2 выбирает одну вакансию у которой key = “job_id”
WS_2 возвращает json вакансии в WS_1
"6": {
        "Employee Status": "Full-time",
        "Job Posting": "Nov 15 2022",
        "description": "We are looking for a Quality Assurance (QA) engineer to develop and execute exploratory and automated tests to ensure product quality. QA engineer responsibilities include designing and implementing tests, debugging and defining corrective actions. You will also review system requirements and track quality assurance metrics.",
        "firm_title": "Banyan Data Services",
        "position_title": "Quality Assurance Engineer",
        "skills": [
            "API Testing", 
            "Mobile testing",
            "Appium",
            "Selenium"
        ]
    }
WS_1 возвращает json вакансии клиенту.



