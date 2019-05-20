## Import bazy pracowników

0. Skopiuj cały folder `employees` do ścieżki `C:\DB` (alternatywnie możesz zmienić namiary w pliku `employees.sql` na takie aby wskazywały lokalizacje tego folderu)
1. Otwórz konsolę mysql. W pasku start wpisz mysql i kliknij:
    ![./images/import_1.png](./images/import_1.png)
2. Po wprowadzeniu swojego hasła administratora udostępniona zostanie konsola:
    ![./images/import_2.png](./images/import_2.png)
3. Z poziomu konsoli wykonaj następujące polecenie jako drugi parametr podając ścieżkę do skryptu `employees.sql`
```
mysql> source C:\DB\employees\employees.sql
```
4. Polecenie powinno rozpocząć import danych. Powinieneś zobaczyć następujące logi:
    ![./images/import_3.png](./images/import_3.png)