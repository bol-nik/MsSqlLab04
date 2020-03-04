Лабораторная работа № 4
1. Отсортировать записи в таблице SPERSON в обратном  порядке  кодов офисов.
2. Отсортировать записи в таблице SPERSON следующим образом:
коды офисов установить в возрастающем порядке; для одинаковых офисов фамилии сотрудников вывести в обратном алфавитном порядке.
3. Посчитать количество сотрудников, работающих в каждом городе.
4. Определить максимальный и минимальный процент комиссионных сотрудников в каждом городе.
5. Определить максимальный и минимальный процент комиссионных сотрудников, работающих в Токио, Брюсселе и в Чикаго (Tokyo, Brussel, Chicago).
6. Определить средний процент комиссионных для всех городов за исключением Токио (Tokyo). В результирующей таблице отобразить только те города, для которых средний процент комиссионных >11%.
7. Определить среднюю, минимальную и максимальную закупочную стоимость Настольных ламп (Desc lamp).
8. Посчитать количество сотрудников, работающих в каждом городе. В результирующей таблице отобразить только те города, в которых работает более двух сотрудников.

Примеры:
Количество строк в таблице SPERSON
select count(*) from sperson;

Количество непустых значений в столбце man_id
select count(man_id) from sperson;

Количество уникальных значений в столбце man_id
select count(distinct man_id) from sperson;

select min(data) from sale;
select min(sp_name) from sperson;

Найти максимальные комиссионные на фирме
select max(comm) from sperson;

Найти максимальные комиссионные в каждом регионе
select o.of_id, o.office, max(s.comm) max_comm, avg(s.comm) avg_comm 
from office o, sperson s
where o.of_id=s.of_id
group by o.office, o.of_id
order by 2

Найти максимальные комиссионные в каждом регионе, кроме тех, где avg(s.comm)<11
select o.of_id, o.office, max(s.comm) max_comm, avg(s.comm) avg_comm 
from office o, sperson s
where o.of_id=s.of_id
group by o.office, o.of_id
having avg(s.comm) >=11
order by 2

Найти максимальные комиссионные в каждом регионе, кроме Tokyo и тех, где avg(s.comm)<11
select o.of_id, o.office, max(s.comm) max_comm, avg(s.comm) avg_comm 
from office o, sperson s
where o.of_id=s.of_id and o.office!='Tokyo'
group by o.office, o.of_id
having avg(s.comm) >=11  
order by 2
