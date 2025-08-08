# DATABASE-BACKUP-AND-RECOVERY

1. MySQL BACKUP SCRIPT (using mysqldump)
# Full backup of the database (schema + data)
mysqldump -u root -p example_db > example_db_backup.sql

2. MySQL RESTORE SCRIPT
# First, recreate the database (if it was lost)
mysql -u root -p -e "CREATE DATABASE example_db;"

# Then restore the backup
mysql -u root -p example_db < example_db_backup.sql

 3. PostgreSQL BACKUP SCRIPT (using pg_dump)
# Full backup of the PostgreSQL database
pg_dump -U postgres -d example_db -F c -f example_db_backup.pgcustom

PostgreSQL RESTORE SCRIPT (using pg_restore)
# Recreate the database
createdb -U postgres example_db

# Restore the backup
pg_restore -U postgres -d example_db example_db_backup.pgcustom

Simulating Failure
-- MySQL
DROP DATABASE example_db;

-- PostgreSQL
DROP DATABASE example_db;

 Verification After Recovery
 SELECT COUNT(*) FROM Customers;
SELECT COUNT(*) FROM Orders;

Sample data check:
SELECT * FROM Customers WHERE CustomerID = 1;

Check relationships and foreign keys:
SELECT * FROM Orders WHERE CustomerID NOT IN (SELECT CustomerID FROM Customers);


