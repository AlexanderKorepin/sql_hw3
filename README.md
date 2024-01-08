# sql_hw3
--1--Необходимо вывести идентификатор, имя, фамилию, заработную плату из сущности staff при этом данные должны быть отсортированы в порядке возрастания заработной платы.
select id, firstname, lastname, salary
from staff
order by salary;

--2--Необходимо вывести идентификатор, имя, фамилию, заработную плату из сущности staff при этом данные должны быть отсортированы в порядке убывания заработной платы.
select id, firstname, lastname, salary
from staff
order by salary desc;

--3--Необходимо вывести идентификатор, имя, фамилию, заработную плату пяти самых высокооплачиваемых сотрудников из сущности staff.
select id, firstname, lastname, salary FROM staff
order by salary desc
LIMIT 5;

--4--Посчитайте и выведите суммарную зарплату (salary) по каждой специальности (роst) из сущности staff.
Порядок вывода атрибутов: должность, суммарная зарплата.
select post, sum(salary)
from staff
group by post;

--5--Посчитайте и выведите количество сотрудников с должностью 'Рабочий' и возрастом не моложе 24 лет и не старше 49 лет.
SELECT COUNT(post) as number
FROM staff
WHERE (post="Рабочий") AND (age BETWEEN 24 AND 49);

--6--Посчитайте и выведите количество уникальных должностей, имеющихся у сотрудников в сущности 'staff'.
select count(*)
from (select distinct post from staff) as temp;

--7--Найдите средний возраст сотрудников по каждой должности из сущности staff.
Выведите только те должности, у которых средний возраст меньше 30 лет.
select post
from staff
group by post
having avg(age)<30;
