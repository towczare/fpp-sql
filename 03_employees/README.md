## Pracownicy

03.01 Wyszukaj wszystkich pracowników?
```
select * from employees;
```
03.02 Wyszukaj wśród pracowników wszystkich mężczyczn.
```
select * from employees where gender = 'M';
```
03.02 I ogranicz wyniki do 10
```
select * from employees where gender = 'M' limit 10;
```
03.03 Znajdź 30 najstarszych pracowników
```
select * from employees order by birth_date limit 30;
```
03.04 Ile było i jest w firmie zatrudnionych pracowników?
```
select * FROM employees.dept_emp;
```
03.05 Ilu inżynierów ('engineer') pracuje obecnie w firmie (tabela titles)?
```
select count(*) from employees e join titles t on e.emp_no = t.emp_no where title = 'Engineer'
```
03.06 Policz wszystkich pracujących mężczyzn i kobiety.
```
select gender ,count(*) as 'liczba pracownikow' from employees
group by gender;
```
03.07  Policz wszystkich pracujących mężczyzn i kobiety urodzonych po 1960.
```
select count(*)'Pracowncicy urodzeni po 1960', gender
from employees
where year(birth_date) > 1960
group by gender;
```