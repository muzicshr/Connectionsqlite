# Connectionsqlite

import sqlite3

sqlite_file = 'c://users//paude//PycharmProjects//first_project//connsqlite.py'

table_name1 = 'employee' # name of the table to be created
id_column = 'Employee_ID' # name of the PRIMARY KEY column
column_name = 'Employee_Name' # name of the new column
column_name1 = 'Birth_Date' # name of the new column
column_name2 = 'Age'
column_name3 = 'Designation'

table_name2 = 'company'
column_name4 = 'Company_ID'

#Connection to the database file
conn = sqlite3.connect(sqlite_file)
c = conn.cursor()

# c.execute('CREATE TABLE {tn} ({id}, {cn}, {cn1}, {cn2}, {cn3})'\
#         .format(tn=table_name1, cn=column_name, cn1=column_name1, cn2=column_name2, cn3=column_name3,  id=id_column))

# c.execute('CREATE TABLE {tn} ({cn4}, {id})'\
#         .format(tn=table_name2, cn4= column_name4, id=id_column))

# query to alter table column

# c.execute("ALTER TABLE {tn} ADD COLUMN '{cn}'"\
#          .format(tn=table_name1, cn=column_name1))

# query to fetch column name from table

# c.execute('PRAGMA TABLE_INFO({})'.\
#           format(table_name2))
# names = [tup[1] for tup in c.fetchall()]
# print(names)

c.execute('SELECT * FROM {tn}'.\
          format(tn=table_name2))
all_rows = c.fetchall()
print('1):', all_rows)

# c.executescript('drop table if exists employee;')
# c.executescript('drop table if exists company;')

# c.execute("ALTER TABLE {tn} DROP COLUMN '{cn}'"\
#          .format(tn=table_name1, cn= drop_column))


# Insertion in employee table
# try:
#     c.execute('INSERT INTO {tn} ({id}, {cn}, {cn1}, {cn2}, {cn3}) VALUES (5, "Hope", 20016-09-10, 17, "Nepal")'.\
#         format(tn=table_name1,  id=id_column, cn=column_name, cn1=column_name1, cn2=column_name2, cn3=column_name3))
# except sqlite3.IntegrityError:
#     print('Error: ID already exists in PRIMARY KEY column{}'. format(id_column))

# insertion in company table
# c.execute('INSERT INTO {tn} ({cn4}, {id}) VALUES ("c5", 5)'.\
#           format(tn=table_name2, cn4=column_name4, id=id_column))


# Committing changes and closing the connection to the database file
conn.commit()
conn.close()
