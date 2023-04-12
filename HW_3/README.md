# WebServices_HW_3

#### Проверить все ли нормально в работе связки веб-сервисов

**Есть 2 WS:**     
**WS_1:** http://162.55.220.72:5031   
**WS_2:** http://23.88.52.139:5032  

===============================
1. WS_1  
*Endpoint: /jobs_count   
Method: GET*  

- WS_1 получает запрос от клиента. Никаких параметров не нужно
- WS_1 отправляет запрос на WS_2 - http://23.88.52.139:5032/get_jobs_count  
- WS_2 получает запрос от WS_1
- WS_2 парсит JSON, в которой 7 вакансий и считает количество вакансий. По умолчанию в JSON 7 вакансий
- WS_2 отправляет ответ на WS_1, в котором будет JSON
```
{
  "jobs_count": 7
}
```
- WS_1 получает ответ от WS_2 и отправляет JSON клиенту
```
{
  "jobs_count": 7
}  
```
===============================  
2. WS_1   
*Endpoint: /all_jobs   
Method: GET*   

- WS_1 получает запрос от клиента. Никаких параметров не нужно
- WS_1 отправляет запрос на WS_2
- WS_2 получает запрос от WS_1
- WS_2 парсит JSON, в которой 7 вакансий и считает количество вакансий. По умолчанию в JSON 7 вакансий
- WS_2 отправляет ответ на WS_1, в котором будет JSON + все добавленные пользователем вакансии
- WS_1 получает ответ от WS_2 и отправляет JSON клиенту   

===============================  
3. WS_1  
*Endpoint: /add_job   
Method: POST*   

- WS_1 получает запрос от клиента в теле которого должна быть JSON-ка
```
{
  "firm_title": "firm_title",
  "position_title": "position_title",
  "skills": [
     "skill_1", 
     "skill_2", 
     "skill_3"
    ]
  "description": description,
  "Job Posting": job_posting,
  "Employee Status": employee_status
}
```
- WS_1 отправляет запрос на WS_2 - http://23.88.52.139:5032/add_job_item   
В теле запроса должен быть JSON полученный от клиента:
```
{
  "firm_title": "firm_title",
  "position_title": "position_title",
  "skills": [
     "skill_1",
     "skill_2",
     "skill_3"
     ]
  "description": description,
  "Job Posting": job_posting,
  "Employee Status": employee_status
}
```
- WS_2 получает запрос от WS_1
- WS_2 парсит JSON, в которой 7 вакансий и считает количество вакансий. По умолчанию в JSON 7 вакансий
- WS_2 добавляет в JSON присланную из WS_1 JSON.   
У добавленной вакансии будет `id = +1` к общему количеству вакансий в JSON `(n+1)`
- WS_2 отправляет ответ на WS_1 в котором будет JSON:  
```
{
  "result_message": "Job added. Job id is 8",
  "check_message": "call /all_jobs endpoint for checking."
}
```

РЕШЕНИЕ:

При отправке запроса POST http://23.88.52.139:5032/add_job_item отсутсвует часть ответа в JSON `"Job Posting": " "`. 
Следовательно, ошибка в работе WS_2.
