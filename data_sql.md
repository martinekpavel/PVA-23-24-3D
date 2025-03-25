# Zadání z moodlu Access

## Stáhneme si sqlite3

https://www.sqlite.org/download.html

Přímo soubor: [https://www.sqlite.org/2025/sqlite-tools-osx-x64-3490100.zip](https://www.sqlite.org/2025/sqlite-tools-win-x64-3490100.zip)

Pozn. 1: Bylo by dobré přidat do `PATH`.

Pozn. 2: Alternativně můžeme s sqlite databázovými soubory soubory pracovat přímo ve VSC pomocí pluginů.

## Otevřeme nový soubor (databázi)

Windows CLI
Otevřeme si ve složce terminál (cmd) a vytvoříme novou databázi:
```
sqlite3 db.sqlite
```

## V moodle si otevřeme soubor s daty (xls)

Koukneme na strukturu tabulek v xls souboru a vytvoříme podobnou v naší sqlite databázi.

```sql
create table obyvatele (
    cislo integer primary key,
    jmeno text not null,
    prijmeni text not null,
    ulice text not null,
    c_p_ text not null,
    mesto text not null,
    psc text not null,
    rodne_cislo text not null
    );

create table mazlicek (
    cislo integer primary key, 
    druh text not null, 
    jmeno text not null, 
    datum_narozeni date not null, 
    datum_porizeni date not null, 
    majitel integer, 
    FOREIGN KEY (majitel)
    REFERENCES obyvatele (cislo)          
       ON UPDATE SET NULL
       ON DELETE SET NULL
    );

create table automobily (
    id integer primary key autoincrement,
    spz text not null,
    znacka text not null,
    pocet_dveri integer not null,
    vykon integer not null,
    barva text not null,
    majitel integer,
    rok_vyroby integer,
    FOREIGN KEY (majitel)
    REFERENCES obyvatele (cislo)          
       ON UPDATE SET NULL
       ON DELETE SET NULL
       );
    

```



Zobrazit tabulky v databázi: `.tables`

## Naimportujeme data

insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('5J7 3291','fiat',3,90,'modrá',47,1985);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('1V2 8558','Škoda',5,98,'fialová',20,1986);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('3M2 9255','VW',5,125,'červená',5,1986);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('5L3 3625','Škoda',3,96,'bílá',19,1988);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('1T2 5596','Seat',3,69,'stříbrná',2,1991);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('5A6 7832','Škoda',5,50,'červená',37,1993);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('6L3 9561','Škoda',3,110,'modrá',18,1993);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('3A4 5599','Ford',3,86,'stříbrná',56,1995);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('3M2 9355','Škoda',5,65,'černá',15,1995);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('4T5 7456','Škoda',3,75,'červená',29,1995);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('2K9 3621','Audi',5,105,'zelená',1,1996);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('2S5 9556','BMW',5,72,'stříbrná',16,1996);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('3T4 5897','Ford',3,60,'žlutá',28,1996);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('3A3 8523','BMW',5,130,'modrá',56,1997);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('3T9 5845','Škoda',5,75,'růžová',18,1997);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('6E2 4236','Renault',3,90,'zelená',54,1997);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('2Z3 8541','Škoda',5,100,'červená',42,1998);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('3M2 7458','Mercedes',5,80,'stříbrná metalíza',30,1998);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('3T5 9826','Fiat',3,67,'černá',30,1998);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('9T8 3456','Fiat',6,100,'stříbrná',16,1998);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('1T5 1216','Škoda',5,110,'stříbrná',59,1999);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('2K3 6543','Renault',5,110,'Zelená',12,1999);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('2M5 8956','Toyota',3,70,'červená',32,1999);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('3B2 9854','Seat',3,85,'černá',49,1999);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('3H6 5864','Opel',5,130,'červená',12,1999);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('3M2 9256','Ford',4,128,'zelená',20,1999);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('3M4 9856','Volkswagen Polo',5,40,'modrá metalíza',9,1999);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('5B3 7856','Mercedes',5,100,'černá',27,1999);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('1K1 5489','Škoda Fabia',5,47,'stříbrná metalíza',8,2000);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('3M2 9524','Ford',3,140,'černá',54,2000);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('6T8 9766','Porche',2,150,'červená',14,2000);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('1A5 6691','BMW',5,120,'žlutá',34,2001);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('5L8 6954','Škoda',5,145,'černá ',4,2001);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('5T2 9854','Ford',3,150,'černá',47,2001);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('6L2 5865','Mercedes',5,150,'modrá',8,2001);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('3T1 2645','Seat',3,90,'Zelená',52,2002);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('3T7 8523','BMW',3,125,'černá',60,2002);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('4T4 1516','VW',5,115,'zelená',47,2002);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('2S4 5885 ','Audi',5,119,'zelená',38,2003);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('2T8 0536','Škoda',5,120,'Stříbrná',47,2003);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('3B5 1436','Renault',5,65,'střibrná',34,2003);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('3L7 0396','Peugeot',5,130,'červená',48,2003);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('4N6 1236','Audi',5,150,'Stříbrná',49,2003);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('6V9 9412','Honda',3,130,'modrá',3,2003);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('7P2 4747','Audi',4,120,'oranžová',23,2003);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('3N4 8542','Audi',3,145,'modrá',18,2004);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('3S2 4512','Ford',5,130,'fialová',48,2004);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('5M3 9615','Mercedes',5,84,'červená',14,2004);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('5T7 1745','Peugeot',5,115,'Červená',50,2004);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('6L3 9768','Volzwagen',4,128,'černá',29,2004);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('2T5 7889','BMW',3,120,'šedá',36,2005);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('2V4 6996','Smart',2,65,'zelená',45,2005);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('5T2 9478','Mazda',3,115,'Modrá',54,2005);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('5T6 1892','Renault',5,100,'Žlutá',51,2005);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('6K4 2145','Fiat',5,120,'zelená',16,2005);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('7K5 1458','Mercedes-Benz SLK',3,120,'stříbrná metalíza',12,2005);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('2L9 3479','Škoda',5,110,'oranžová',19,2006);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('5E8 8956','Opel Combo',3,66,'pastelově bílá',3,2006);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('3K1 7487','Mercedes',3,150,'růžová',24,2007);
insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('4D8 1234','Volkswagen Golf GTI',5,147,'stříbrná metalíza',7,2007);


`="insert into automobily (spz,znacka,pocet_dveri,vykon,barva,majitel,rok_vyroby) values ('"&A2&"','"&B2&"',"&C2&","&D2&",'"&E2&"',"&F2&","&G2&");"`

`="insert into obyvatele (cislo, jmeno, prijmeni, ulice, c_p_, mesto, psc, rodne_cislo) values ("&A2&",'"&B2&"','"&C2&"','"&D2&"','"&E2&"','"&F2&"','"&G2&"','"&H2&"');"`

`="insert into mazlicek (cislo, druh, jmeno, datum_narozeni, datum_porizeni, majitel) values ("&A2&",'"&B2&"','"&C2&"',"&D2&","&E2&","&F2&");"`

### Vylepšení
```
.mode box
.header on
```

 `select * from obyvatele join mazlicek on mazlicek.cislo = obyvatele.cislo where mazlicek.druh = 'kočka' or mazlicek.druh = 'pes';`

 `select obyvatele.jmeno,obyvatele.prijmeni,mazlicek.druh,mazlicek.jmeno from obyvatele join mazlicek on mazlicek.cislo = obyvatele.cislo where mazlicek.druh = 'kočka' or mazlicek.druh = 'pes';`

  `select obyvatele.jmeno,obyvatele.prijmeni,mazlicek.druh,mazlicek.jmeno from obyvatele join mazlicek on mazlicek.cislo = obyvatele.cislo where mazlicek.druh = 'kočka' or mazlicek.druh = 'pes' order by mazlicek.druh;`


## Záloha

`.backup nazev_souboru`

## Update

### Example

UPDATE employees
SET lastname = 'Smith'
WHERE employeeid = 3;

### Syntax

UPDATE table_name
SET column1 = value1, column2 = value2,
WHERE condition;

###  Updating Multiple Columns

UPDATE employees
SET city = 'Toronto', state = 'ON', postalcode = 'M5P 2N7'
WHERE employeeid = 4;



## Delete

### Example

To delete a specific row from a table:

DELETE FROM table_name WHERE condition;
For instance, to delete a row with id = 1:

DELETE FROM employees WHERE id = 1;

### Deleting Multiple Rows

To delete multiple rows based on a condition:

DELETE FROM employees WHERE department = 'Sales';

### Deleting All Rows

To delete all rows from a table:

DELETE FROM employees;
