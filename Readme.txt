������������ ������ � 4
1. ������������� ������ � ������� SPERSON � ��������  �������  ����� ������.
2. ������������� ������ � ������� SPERSON ��������� �������:
���� ������ ���������� � ������������ �������; ��� ���������� ������ ������� ����������� ������� � �������� ���������� �������.
3. ��������� ���������� �����������, ���������� � ������ ������.
4. ���������� ������������ � ����������� ������� ������������ ����������� � ������ ������.
5. ���������� ������������ � ����������� ������� ������������ �����������, ���������� � �����, �������� � � ������ (Tokyo, Brussel, Chicago).
6. ���������� ������� ������� ������������ ��� ���� ������� �� ����������� ����� (Tokyo). � �������������� ������� ���������� ������ �� ������, ��� ������� ������� ������� ������������ >11%.
7. ���������� �������, ����������� � ������������ ���������� ��������� ���������� ���� (Desc lamp).
8. ��������� ���������� �����������, ���������� � ������ ������. � �������������� ������� ���������� ������ �� ������, � ������� �������� ����� ���� �����������.

�������:
���������� ����� � ������� SPERSON
select count(*) from sperson;

���������� �������� �������� � ������� man_id
select count(man_id) from sperson;

���������� ���������� �������� � ������� man_id
select count(distinct man_id) from sperson;

select min(data) from sale;
select min(sp_name) from sperson;

����� ������������ ������������ �� �����
select max(comm) from sperson;

����� ������������ ������������ � ������ �������
select o.of_id, o.office, max(s.comm) max_comm, avg(s.comm) avg_comm 
from office o, sperson s
where o.of_id=s.of_id
group by o.office, o.of_id
order by 2

����� ������������ ������������ � ������ �������, ����� ���, ��� avg(s.comm)<11
select o.of_id, o.office, max(s.comm) max_comm, avg(s.comm) avg_comm 
from office o, sperson s
where o.of_id=s.of_id
group by o.office, o.of_id
having avg(s.comm) >=11
order by 2

����� ������������ ������������ � ������ �������, ����� Tokyo � ���, ��� avg(s.comm)<11
select o.of_id, o.office, max(s.comm) max_comm, avg(s.comm) avg_comm 
from office o, sperson s
where o.of_id=s.of_id and o.office!='Tokyo'
group by o.office, o.of_id
having avg(s.comm) >=11  
order by 2
