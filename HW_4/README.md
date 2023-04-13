# WebServices_HW_2

#### Check if everything is normal in the web services:

**WS_1:** http://23.88.52.139:5041 (acts as a proxy from the client, all client requests go through it)    
**WS_2:** http://23.88.52.139:5042 (list of all job applications)   
**WS_3:** http://23.88.52.139:5043 (list of skills)   
**WS_4:** http://23.88.52.139:5044 (position list)  
**WS_5:** http://23.88.52.139:5045 (list of departments)

1. View lists:  

- |               | Method        | Endpoint          |
  |:------------- |:------------- |:----------------  |
  |  1            | GET           | WS_1/all_jobs     |
  |  2            | GET           | WS_2/get_all_jobs |

- |               | Method        | Endpoint                  |
  |:------------- |:------------- |:------------------------  |
  |  1            | GET           | WS_1/get_skills           |
  |  2            | GET           | WS_3/get_tech_skills_list |
  
- |               | Method        | Endpoint                |
  |:------------- |:------------- |:----------------------  |
  |  1            | GET           | WS_1/get_positions      |
  |  2            | GET           | WS_4/get_positions_list |     
     
- |               | Method        | Endpoint                  |
  |:------------- |:------------- |:------------------------  |
  |  1            | GET           | WS_1/get_departments      |
  |  2            | GET           | WS_5/get_departments_list |       
  	  
2. Create job:

  - *Method: POST  
     Endpoint: WS_1/create_job*    
     
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
     Endpoint: WS_2/create_job_position*    
     
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
   Endpoint: WS_3/skill_config*    
     
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
   Endpoint: WS_4/position_config*    
     
  Body raw (JSON): 
```  
    {
      "position_id": position_id
     }
```
 - *Method: POST  
    Endpoint: WS_5/department_config*    
     
  Body raw (JSON): 
```  
    {
      "department_id": department_id
     }
```

3. You can find logs on server in w1.log

### SOLUTION

1. Check all endpoints

2. Log onto the server:   
`ssh test_31@23.88.52.139`

3. Find files `w1.log`, `w2.log`, `w3.log`, `w4.log`, `w5.log`:   
`find -name "w?.log"`

4. Download them to computer:
```
exit
scp test_31@23.88.52.139:/usr/t4_ws/t4/w1/w1.log w1.log
scp test_31@23.88.52.139:/usr/t4_ws/t4/w2/w2.log w2.log
scp test_31@23.88.52.139:/usr/t4_ws/t4/w3/w3.log w3.log
scp test_31@23.88.52.139:/usr/t4_ws/t4/w4/w4.log w4.log
scp test_31@23.88.52.139:/usr/t4_ws/t4/w5/w5.log w5.log
```

5. Output to the `logs.log` file only those requests with my IP and 10 lines around it:
`grep -a -C10 "0.0.0.0" w?.log >logs.log`

6. Open `logs.log` file:
`vim logs.log`

7. There are no errors in the logs
