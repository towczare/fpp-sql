## Procedury, funkcje i triggery (wyzwalacze?)

Pierwsza funkcja
```
delimiter //

CREATE FUNCTION HelloWorld () RETURNS VARCHAR(20) DETERMINISTIC
BEGIN
	RETURN 'Hello World';
END
//
delimiter ;
```
* `DELIMITER //` - powoduje zastąpienie średnika `//`
* `DELIMITER ;` - na końcu powoduje, że średnik odzyskuje swoje dawne znaczenie

Wywołaj funkcję:
```
SELECT HelloWorld();
```

Pierwsza procedura:
```
delimiter //

CREATE PROCEDURE all_employees ()

SELECT * FROM employees;
//
delimiter ;
```
wywołanie procedury:
```
CALL all_employees;
```

Pierwszy trigger:

Utwórzmy dodatkową tabelę gdzie będziemy przechowywać dane, zasilane automatycznie podczas naszych akcji
```
CREATE TABLE new_employees_counter (
    id INT AUTO_INCREMENT PRIMARY KEY,
    action_date DATETIME DEFAULT NULL
);
```
Sprawdźmy, że jest pusta:
```
SELECT * FROM new_employees_counter;
```
Teraz tworzymy trigger, który będzie wyzwalany w przypadku dodania nowej osoby do bazy:
```
DELIMITER //
CREATE TRIGGER before_employee_insert
    BEFORE INSERT ON employees
    FOR EACH ROW
BEGIN
    INSERT INTO new_employees_counter
    SET action_date = NOW();
END//
DELIMITER ;
```
Następnie dodajmy jedną osobę:
```
INSERT INTO employees.employees (emp_no, birth_date, first_name, last_name, gender, hire_date) VALUES (20401122, '1988-04-20', 'Joanna', 'Kowalska', 'F', '2005-06-02');
```
I sprawdźmy jeszcze raz naszą tabelę `new_employees_counter`
```
SELECT * FROM new_employees_counter;
```
Powinniśmy zobaczyć nowy wpis.

08.01 Stwórz funkcje `yearsSince(dateFrom DATE)` zwracającą jako rezultat ilość lat które minęły od podanej daty.
Funkcję wykorzystaj aby wyświetlić dane o pracownikach i zamień dwa pola:
* birth_date - zamień na pole age wykorzystując w tym celu twoją funkcję `yearsSince`
* hire_date -  zamień na pole hiredAgo wykorzystując w tym celu twoją funkcję `yearsSince`

08.02 Stwórz funkcję pozwalającą na prezentację miesięcznych zarobków pracownika (dla przypomnienia, obecne dane w tabeli salaries zapisane są jako informacje roczne)

08.03 Stwórz funkcję prezentującą ilość lat zatrudnienia dla dwóch parametrów `from_date` i `to_date` z tabeli `dept_emp`
* 08.03.01 Niektóe wpisy w kolumnie `to_date` mają zapisaną wartość 9999-01-01 oznacza ona zatrudnienie na czas nieokreślony, dla takich dat chcielibyśmy aby funkcja prezentowała wartośc dla aktualnego roku

08.04 Stwórz procedurę o nazwie `employees_with_current_salaries()` prezentującą pracowników, z ostatnią wypłatą i tytułem. Pojedynczy wiersz powinien wyglądać jak poniżej:
```
10001	Senior Engineer	1953-09-02	Georgi	Facello	M	1986-06-26	60117	2002-06-22
```
08.05 Stwórz trigger który będzie zapisywał modyfikacje danych użytkowników i przechowywał je w specjalnej tabeli audytowej o nazwie `employee_audit` Będziemy w niej przechowywać:
* id
* employee_number
* first_name
* last_name
* modify_date

aby dostać się do tych pól, można skorzystać z przedrostka `OLD` np. `OLD.first_name` co zwróci dane przez operacją.

08.:bulb: Kolej na Ciebie :thinking:, przygotuj 3 własne zagadki i zaproponowane rozwiązania.
