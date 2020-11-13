# Creating Database
  create database LMS; 
# using Database
  use lms;

# registraion 
  create table registration 
  ( id bigint primary key auto_increment, 
  name varchar(100) not null, 
  email varchar(100) not null unique, 
  password varchar(100) not null, 
  confirm_password varchar(100) not null, 
  registration_date timestamp not null default current_timestamp 
  );
# display registration table
  select *from registration;

# display table
  select *from registration;

# leave category table
    create table leave_categories
  (
    id bigint primary key auto_increment,
      casual_leave varchar(100) default 12 not null,
      sick_leave varchar(100) default 12 not null,
      medetory_leave varchar(100) default 12 not null
  );
  
  # Type of leave(table)
  
  create table type_of_leave
  (
    id bigint primary key auto_increment,
      type_of_leaves varchar(100) not null
  );

# apply leave table

  create table apply_leave
  (
    user_id bigint primary key auto_increment,
      name varchar(100) not null,
      email varchar(100) not null unique,
      reason varchar(100) not null,
      from_date varchar(10) not null,
      to_date varchar(10) not null,
      foreign key (user_id) references login(user_id)

  );
# inserting values
  insert into apply_leave(name,email,reason,from_date,to_date) values('prasanjeet das','prasanjeetdas44@gmail.com','leave for personal      reason','12/11/2020','15/11/20');
  insert into apply_leave(name,email,reason,from_date,to_date) values('monu','monu44@gmail.com','leave for some reason','15/11/2020','20/11/20');
  select *from apply_leave;
  alter table apply_leave add status varchar(3)  default "requested" not null;
# display table values
  select *from apply_leave;
# total leave table
  create table total_leave
  (
	id bigint primary key auto_increment,
    leave_category_id varchar(100)  not null,
    no_days varchar(100) default 0 not null,
    start_date varchar(100) not null,
   end_date varchar(100) not null,
   status varchar(3) not null default "requested"
  );
