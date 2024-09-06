from one_to_many import app, db
>>> from one_to_many import Player, Team
>>> app_ctx = app.app_context()
>>> app_ctx.push()
>>> db.create_all()
>>> csk = Team(team='CSK', state='Tamil Nadu') 
>>> csk = Team(team='CSK', state='Karnataka')  
>>> mi = Team(team='MI', state='Maharashtra') 
>>> db.session.add_all([csk, mi])  
>>> db.session.commit()
>>> rcb = Team(team='RCB', state='Karnataka')  
>>> db.session.add_all([rcb]) 
>>> db.session.commit()
>>> msd = Player(name='Dhoni',nationality='Indian',team=csk)
>>> msd
Players('Dhoni','Indian')
>>> db.session.add_all([msd]) 

>>> db.session.commit()
>>> moeen = Player(name='Moeen Ali',nationality='Englend',team=csk) 
>>> jadeja =Player(name='Rabi Jadeja',nationality='Indian',team=csk)   

>>> kholi = Player(name='Virat Kholi',nationality='Indian',team=rcb)  
>>> faf = Player(name='Faf Du Plesis',nationality='South Africa',team=rcb)  
>>> rohit = Player(name='Rohit Sharma',nationality='Indian',team=mi)  

>>> tim= Player(name='Tim David',nationality='Australin',team=mi)  
>>> db.session.add_all([moeen, jadeja, kholi, faf, rohit, tim]) 
>>> db.session.commit()
>>> Team.query.first()
Team('CSK', 'Karnataka')

>>> csk_team = Team.query.first() 
>>> csk_team
Team('CSK', 'Karnataka')
>>> csk_team.members
[Players('Dhoni','Indian'), Players('Moeen Ali','Englend'), Players('Rabi Jadeja','Indian')]

>>> for pl in csk_team.members:
...     print(f"{pl.name} is an {pl.nationality} natinality")   

Dhoni is an Indian natinality
Moeen Ali is an Englend natinality
Rabi Jadeja is an Indian natinality


>>> msd_player = csk_team.members[0]
>>> msd_player
>>> msd_player = csk_team.members[0]
>>> msd_player
Players('Dhoni','Indian')
>>> msd_player
Players('Dhoni','Indian')
Players('Dhoni','Indian')
>>> msd_player.team
>>> msd_player.team
Team('CSK', 'Karnataka')
>>> app_ctx.pop()
>>> app_ctx.pop()
>>> exit()



