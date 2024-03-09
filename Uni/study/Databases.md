#uni
Крашенинников Сергей Вениаминович
**email:** data_bases@mail.ru - only for info
**Books:** Дэйт "Введение в системы базы данных", Кузнецов Сергей Дмитриевич "Системы баз данных"

# First lab
Given a CD market. 
We need to make a scheme of a database for this market.
## How to make a scheme of a database
Create data objects:
1. Disc (properties: Name, Company, ID, ...). Properties are being added to the table
2. Song (properties: ID, Name, Duration, ...)
3. Artist (properties: ID, Name, Year, ...)

Any table has a key (ID) - a special value which is individual for every row
of a table.
There are 3 different types of connections between tables:
1. one-to-one ($1 : 1$)
2. one-to-many ($1 : n$) - songs has pointers to disc ID's
3. many-to-many ($m : n$) - the third table of unique pairs is being created
## Let's open the store!
Someone just bought our disc. We have to write down when it was made, what has been bought, how much money we got... In other words, we have to *change our tables*.

For this information, two tables are being created. The information is being *added* to those tables.
For our case: 
1. Receipt (ID, Date, ...)
2. Receipt positions (Bill ID) - connected with bill through one-to-many connection

# First lecture
There were 2 main data storages:
1. Magnetic tape memory storage
2. Magnetic drum memory storage
Revolution in data conservation has begun after inventing magnetic discs
## The Unix legacy
- The file is a set of bytes, which can be read and rearranged (rwx)
- **The alternative to a mandate approach:** 3 indicators - owner, group, any. With these indicators we can add 9 bits to *every* file to exactly give properties for every user as he is being added to specific indicator.
- **Directories**
## The company problem
Given an OS and a set of applications, we need to create an employee record.

First idea: create a table with columns:
- number
- name
- adress
- salary
- place
- department number
- department manager ...
If we delete a row, *we lose information about that row completely*. Therefore, the first idea is bad

Second idea: create second table
- department number
- department name
- department manager
First table has to refer to a second table, so as second to first - there is need in protocols.
There are languages for data orders


# Second lecture
## Semantic data model
1976, Chen, "Entity-relationship"
Graphical representation of relations and objects
Three main terms:
1. Entity - represented with a rectangle
2. Relation
3. Atribute - represented with a circle

![[Examples.pdf]]
# Third lecture
