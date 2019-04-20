check databases (cmd)
=======================
~~~sql 
select name from sys.databases 
go
~~~


check databases (cmd)
=======================
~~~sql 
show databases 
~~~


Alter table
=================

~~~sql
ALTER TABLE `taitra_member`.`taitra_member_account` 
ADD COLUMN `VERIFICATION_CHECK_CODE` VARCHAR(10) NULL AFTER `PROFILE_PHOTO_URL`,
ADD COLUMN `VERIFICATION_STATUS` CHAR(1) NULL AFTER `VERIFICATION_CODE`,
ADD COLUMN `VERIFICATION_TYPE` CHAR(3) NULL AFTER `VERIFICATION_STATUS`;
~~~