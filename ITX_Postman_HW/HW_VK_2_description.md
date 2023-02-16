
#### Домашняя работа

Protocol: http, 
IP: 162.55.220.72,
Port: 5005

---
Статус код 200 для всех запросов

```javascript
pm.test("Status code is 200", function () {
pm.response.to.have.status(200);
});
```
---
1. Отправить запрос GET
http://162.55.220.72:5005/first
```
Response:
This is the first responce from server!ss
```
2. Проверить, что в body приходит правильный string.
```javascript
pm.test("Body matches string", function () {
    pm.expect(pm.response.text()).to.include("This is the first responce from server!ss");
});
```
---
1. Отправить запрос POST
http://162.55.220.72:5005/user_info_3
```javascript
Response:
{
    "age": "31",
    "family": {
        "children": [
            [
                "Alex",
                24
            ],
            [
                "Kate",
                12
            ]
        ],
        "u_salary_1_5_year": 600000
    },
    "name": "DmitriiD",
    "salary": 150000
}
```
2. Спарсить response body в json.
```javascript
var resp_f = pm.response.json();
```
3. Проверить, что name в ответе равно name s request (name вбить руками.)
```javascript
pm.test("Check name", function () {
    pm.expect("DmitriiD").to.eql(resp_f.name);
});
```
4. Проверить, что age в ответе равно age s request (age вбить руками.)
```javascript
pm.test("Check age", function () {
    pm.expect(31).to.eql(+resp_f.age);
});
```
5. Проверить, что salary в ответе равно salary s request (salary вбить руками.)
```javascript
pm.test("Check salary", function () {
    pm.expect(150000).to.eql(resp_f.salary);
});
```
6. Спарсить request.
```javascript
let req_f = request.data;
```
7. Проверить, что name в ответе равно name s request (name забрать из request.)
```javascript
pm.test("Check name", function () {
    pm.expect(req_f.name).to.eql(resp_f.name);
});
```
8. Проверить, что age в ответе равно age s request (age забрать из request.)
```javascript
pm.test("Check age", function () {
    pm.expect(req_f.age).to.eql(resp_f.age);
});
```
9. Проверить, что salary в ответе равно salary s request (salary забрать из request.)
```javascript
pm.test("Check salary", function () {
    pm.expect(+req_f.salary).to.eql(resp_f.salary);
});
```
10. Вывести в консоль параметр family из response.
```javascript
console.log(resp_f.family)
```
11. Проверить что u_salary_1_5_year в ответе равно salary*4 (salary забрать из request)
```javascript
pm.test("Check salary value", function () {
    pm.expect(4 * req_f.salary).to.eql(resp_f.family.u_salary_1_5_year);
});
```
---
http://162.55.220.72:5005/object_info_3
1. Отправить запрос.
2. Статус код 200
3. Спарсить response body в json.
4. Спарсить request.
5. Проверить, что name в ответе равно name s request (name забрать из request.)
6. Проверить, что age в ответе равно age s request (age забрать из request.)
7. Проверить, что salary в ответе равно salary s request (salary забрать из request.)
8. Вывести в консоль параметр family из response.
9. Проверить, что у параметра dog есть параметры name.
10. Проверить, что у параметра dog есть параметры age.
11. Проверить, что параметр name имеет значение Luky.
12. Проверить, что параметр age имеет значение 4.
---
http://162.55.220.72:5005/object_info_4
1. Отправить запрос.
2. Статус код 200
3. Спарсить response body в json.
4. Спарсить request.
5. Проверить, что name в ответе равно name s request (name забрать из request.)
6. Проверить, что age в ответе равно age из request (age забрать из request.)
7. Вывести в консоль параметр salary из request.
8. Вывести в консоль параметр salary из response.
9. Вывести в консоль 0-й элемент параметра salary из response.
10. Вывести в консоль 1-й элемент параметра salary параметр salary из response.
11. Вывести в консоль 2-й элемент параметра salary параметр salary из response.
12. Проверить, что 0-й элемент параметра salary равен salary из request (salary забрать из request.)
13. Проверить, что 1-й элемент параметра salary равен salary*2 из request (salary забрать из request.)
14. Проверить, что 2-й элемент параметра salary равен salary*3 из request (salary забрать из request.)
15. Создать в окружении переменную name
16. Создать в окружении переменную age
17. Создать в окружении переменную salary
18. Передать в окружение переменную name
19. Передать в окружение переменную age
20. Передать в окружение переменную salary
21. Написать цикл который выведет в консоль по порядку элементы списка из параметра salary
---
http://162.55.220.72:5005/user_info_2
1. Вставить параметр salary из окружения в request
2. Вставить параметр age из окружения в age
3. Вставить параметр name из окружения в name
4. Отправить запрос.
5. Статус код 200
6. Спарсить response body в json.
7. Спарсить request.
8. Проверить, что json response имеет параметр start_qa_salary
9. Проверить, что json response имеет параметр qa_salary_after_6_months
10. Проверить, что json response имеет параметр qa_salary_after_12_months
11. Проверить, что json response имеет параметр qa_salary_after_1.5_year
12. Проверить, что json response имеет параметр qa_salary_after_3.5_years
13. Проверить, что json response имеет параметр person
14. Проверить, что параметр start_qa_salary равен salary из request (salary забрать из request.)
15. Проверить, что параметр qa_salary_after_6_months равен salary*2 из request (salary забрать из request.)
16. Проверить, что параметр qa_salary_after_12_months равен salary*2.7 из request (salary забрать из request.)
17. Проверить, что параметр qa_salary_after_1.5_year равен salary*3.3 из request (salary забрать из request.)
18. Проверить, что параметр qa_salary_after_3.5_years равен salary*3.8 из request (salary забрать из request.)
19. Проверить, что в параметре person, 1-й элемент из u_name равен salary из request (salary забрать из request.)
20. Проверить, что что параметр u_age равен age из request (age забрать из request.)
21. Проверить, что параметр u_salary_5_years равен salary*4.2 из request (salary забрать из request.)
22. ***Написать цикл который выведет в консоль по порядку элементы списка из параметра person.

