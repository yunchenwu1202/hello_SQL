## CREATE Function
```sql
create table TEST(
  ID integar, 
  NAME varchar(30)
  );
```

### 1. Creating a table called country with ID column, a two letter country code column, and a variable length country name column.
```sql
create table COUNTRY(
  ID int 
  CCODE char(2)
  NAME varchar(60)
  );
```

### Sometimes you may see additional keywords in a create table statement
```sql
create table COUNTRY(
  ID int NOT NULL,
  CCODE cahr(2)
  NAME varchar(60)
  PRIMARY KEY (ID),
  PRIMARY KEY (ID)
);
```

### DROP Function
```sql
dropt table COUNTRY;
create table COUNTRY (
  ID integar PRIMARY KEY NOT NULL
  CCODE char(2)
  NAME varchar(60)
  );
```



