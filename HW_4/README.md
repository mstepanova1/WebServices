# WebServices_HW_4

#### Check if everything is normal in the web services:

**WS_1:** http://23.88.52.139:5041 (acts as a proxy from the client, all client requests go through it)    
**WS_2:** http://23.88.52.139:5042 (list of all job applications)   
**WS_3:** http://23.88.52.139:5043 (list of skills)   
**WS_4:** http://23.88.52.139:5044 (position list)  
**WS_5:** http://23.88.52.139:5045 (list of departments)

I. View lists:  

  - *Method: GET    
     Endpoint: WS_1/all_jobs -->  
	   Method: GET  
     Endpoint: WS_2/get_all_jobs*  
     
  - *Method: GET  
     Endpoint: WS_1/get_skills -->  
	   Method: GET   
     Endpoint: WS_3/get_tech_skills_list*  
     
  - *Method: GET  
     Endpoint: WS_1/get_positions -->   
	   Method: GET   
     Endpoint: WS_4/get_positions_list*  
     
  - *Method: GET  
     Endpoint: WS_1/get_departments -->  
	   Method: GET  
     Endpoint: WS_4/get_departments_list*   
	  
II. Create job:

  - *Method: POST  
     Endpoint: WS_1/create_job* -->   
     
  Body raw (JSON): 
```  
    {
       "department": department_id,
       "position": position_id,
       "skills": [
          skill_id, 
          skill_id, 
          ..., 
          skill_id
        ]
     }
```
  - *Method: POST  
     Endpoint: WS_2/create_job_position* -->   
     
Body raw (JSON):   
```
  {
       "department": department_id,
       "position": position_id,
       "skills": [
          skill_id, 
          skill_id, 
          ..., 
          skill_id
        ]
     }
```
 - *Method: POST  
   Endpoint: WS_3/skill_config* -->   
     
  Body raw (JSON): 
```  
    {
      "skill_ids": [
          skill_id, 
          skill_id, 
          ..., 
          skill_id
        ]
     }
```
 - *Method: POST  
   Endpoint: WS_4/position_config* -->   
     
  Body raw (JSON): 
```  
    {
      "position_id": position_id
     }
```
 - *Method: POST  
    Endpoint: WS_5/department_config* -->   
     
  Body raw (JSON): 
```  
    {
      "department_id": department_id
     }
```

III. You can find logs on server in w1.log
