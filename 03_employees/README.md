## Pracownicy

03.01 Wyszukaj wszystkich pracowników?
<details>
<summary>Rozwiązanie...</summary>
<p>

```sql
select * from employees;
```

</p>
</details>  

03.02 Wyszukaj wśród pracowników wszystkich mężczyczn.
<details>
<summary>Rozwiązanie...</summary>
<p>

```sql
select * from employees where gender = 'M';
```

</p>
</details>  
03.02 I ogranicz wyniki do 10
<details>
<summary>Rozwiązanie...</summary>
<p>

```sql
select * from employees where gender = 'M' limit 10;
```

</p>
</details>  

03.03 Znajdź 30 najstarszych pracowników
<details>
<summary>Rozwiązanie...</summary>
<p>

```sql
select * from employees order by birth_date limit 30;
```

</p>
</details>  

03.04 Ile było i jest w firmie zatrudnionych pracowników?
<details>
<summary>Rozwiązanie...</summary>
<p>

```sql
select * FROM employees.dept_emp;
```

</p>
</details>  

03.05 Ilu inżynierów ('engineer') pracuje obecnie w firmie (tabela titles)?
<details>
<summary>Rozwiązanie...</summary>
<p>

```sql
select count(*) from employees e join titles t on e.emp_no = t.emp_no where title = 'Engineer'
```

</p>
</details>  

03.06 Policz wszystkich pracujących mężczyzn i kobiety.
<details>
<summary>Rozwiązanie...</summary>
<p>

```sql
select gender ,count(*) as 'liczba pracownikow' from employees
group by gender;
```

</p>
</details>  

03.07  Policz wszystkich pracujących mężczyzn i kobiety urodzonych po 1960.
<details>
<summary>Rozwiązanie...</summary>
<p>

```sql
select count(*)'Pracowncicy urodzeni po 1960', gender
from employees
where year(birth_date) > 1960
group by gender;
```

</p>
</details>  
