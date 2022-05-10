from dbmodule import connect 
#Create connection object
Connection = connect('databasename','username','pswd')

#Create a cursor object
Cursor = connection.cursor()

#Run Queries
Cursor.execute('select* from mytable')
Results = cursor.fetchall()

#Free resources
Cursor.close()
Connection.close()
