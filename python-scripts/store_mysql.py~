#encoding=utf-8
#!/usr/bin/env python 
import mysql.connector
import mysql.connector.errors

def store_mysql(filepath):
	conn=mysql.connector.connect(user='root',password='123456',database='zsy_db')
	cursor=conn.cursor()
	
	
	cursor.execute('show tables in zsy_db;')
	tables=cursor.fetchall()
	#ll = [y for x in tables for y in x if 'Code' in y]
	#findtables = (len(ll) > 0)
	print tables
	findtables=False
	for table in tables:
		print table
		for tt in table:
			print tt
			if u'Code' in tt:
				findtables=True
	if not findtables:
		cursor.execute('''
			create table ShowMeTheCode
			(id int not null auto_increment primary key,
			code char(10) not null);
			''')
	f=open(filepath,'rb')
	for line in f.readlines():
		code=line.strip()
		cursor.execute("insert into ShowMeTheCode (code) values(%s);",[code])

	conn.commit()
	cursor.close()
	conn.close()

if __name__=='__main__':
	store_mysql('/home/jeremy/files/python-scripts/python-projects/Activation_code.txt')
