## flask with sql-alchemy

# set up in vscode

- pip install virtualenv
- virtual env
- .\env\Scripts\activate
- python


### python sell code for crud 

->>> import os
->>> os.listdir()
-['db_crud_demp.py', 'env']


->>> from db_crud_demo import app, db <br>
->>> app_context = app.app_context() <br>
->>> app_context.push() <br>
->>> db.create_all() <br>
 
->>> from db_crud_demo import Employee  
->>> micheal = Employee(name='Micheal',age=42, email='micheal@gmail.com')
->>> micheal
-Employee('Micheal','42','micheal@gmail.com')

->>> dwight = Employee(name='Dwight',age=23, email='dwight@gmail.com') 
->>> dwight
-Employee('Dwight','23','dwight@gmail.com')


->>> Jim = Employee(name='Jim',age=33, email='jim@gmail.com')          
->>> Jim
-Employee('Jim','33','jim@gmail.com')

 
->>> db.session.add(micheal) 
->>> db.session.commit()
->>> db.session.add_all([dwight,Jim]) 
->>> db.session.commit()


->>> employees = Employee.query.all()    
->>> employees
-[Employee('Micheal','42','micheal@gmail.com'), Employee('Dwight','23','dwight@gmail.com'), Employee('Jim','33','jim@gmail.com')]

->>> employees[1] 
-Employee('Dwight','23','dwight@gmail.com')
->>> employees[0] 
-Employee('Micheal','42','micheal@gmail.com')
->>> micheal
-Employee('Micheal','42','micheal@gmail.com')
->>> micheal.name
-'Micheal'
->>> micheal.age
-42
->>> micheal.email
-'micheal@gmail.com'


->>> for emp in employees:
-...     print(f"{emp.name} who is {emp.age} years old, has email as {emp.email} ")
-...
-Micheal who is 42 years old, has email as micheal@gmail.com
-Dwight who is 23 years old, has email as dwight@gmail.com
-Jim who is 33 years old, has email as jim@gmail.com


->>> Employee.query.first()
-Employee('Micheal','42','micheal@gmail.com')

->>> Employee.query.filter_by(name='Jim') 
-<flask_sqlalchemy.query.Query object at 0x00000176AF0D3B30>

->>> Employee.query.filter_by(name='Jim').all()
-[Employee('Jim','33','jim@gmail.com')]

->>> Employee.query.filter_by(name='Jim').first()
-Employee('Jim','33','jim@gmail.com')

->>> db.session.get(Employee, 1) 
-Employee('Micheal','42','micheal@gmail.com')
->>> micheal.age
-42
->>> micheal
-Employee('Micheal','42','micheal@gmail.com')
->>>
->>> 
->>> micheal.age = 50
->>> db.session.commit()


->>> db.session.delete(Jim)
->>> db.session.commit()
