# WebServices_HW_2

#### Проверить все ли нормально в работе связки веб-сервисов

**Есть 2 WS:**     
**WS_1:** http://162.55.220.72:5021   
**WS_2:** http://23.88.52.139:5022 

1. WS_1  
*Endpoint: /jobs  
Method: GET*   

- WS_1 получает запрос от клиента. При отправке запроса из Postman никаких параметров не нужно.
- WS_1 парсит JSON, который храниться на файловой системе сервера. Внутри этого JSON лежит 7 вакансий.
- WS_1 возвращает клиенту JSON в котором будет 7 вакансий.

2. WS_1  
*Endpoint: /jobs  
Method: POST*  

- WS_1 получает запрос от клиента.
В теле запроса должен быть raw (JSON): 
```
{
  "job_id": 1
}
```
- После получения запроса WS_1 парсит JSON, в которой 7 вакансий и отправляет запрос на WS_2 - http://23.88.52.139:5022/get_job  
В теле запроса должен быть raw (JSON):
```
{
  "job_id": 1, 
  "j_data": "json"
}
```
- WS_2 получает запрос от WS_1
- WS_2 выбирает одну вакансию у которой `key = "job_id"`
- WS_2 возвращает JSON вакансии в WS_1
```
"1": {
    "Employee Status": "Full-time",
    "Job Posting": "Aug 02 2022",
    "description": "Experience with Functional Testing, including Regression Testing, Integration Testing, and API Testing. Experience with creating and executing test scripts. Experience testing developments against wireframes and style guide. Experience with systems, integration, and user acceptance testing. Experience in working with offshore /onsite Model",
    "firm_title": "Cognizant Technology Solutions",
    "position_title": "QA Functional Tester",
    "skills": [
        "postman",
        "js",
        "client_server",
        "api_testing"
    ]
}
```
- WS_1 возвращает JSON вакансии клиенту

### РЕШЕНИЕ:

При отправке запроса на WS_1 методом POST в ответе отсутсвует часть JSON `"Job Posting": "Aug 02 2022"`. Проверка работы WS_2 показала, что он отвечает правильно, следовательно, ошибка в работе WS_1.
