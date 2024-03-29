
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
Response:
```javascript
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
1. Отправить запрос GET http://162.55.220.72:5005/object_info_3
Response:
```javascript
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
        "pets": {
            "cat": {
                "age": 3,
                "name": "Sunny"
            },
            "dog": {
                "age": 4,
                "name": "Luky"
            }
        },
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
3. Спарсить request.
```javascript
let req_f = pm.request.url.query.toObject()
```
4. Проверить, что name в ответе равно name s request (name забрать из request.)
```javascript
pm.test("Check name", function () {
    pm.expect(req_f.name).to.eql(resp_f.name);
});
```
5. Проверить, что age в ответе равно age s request (age забрать из request.)
```javascript
pm.test("Check age", function () {
    pm.expect(req_f.age).to.eql(resp_f.age);
});
```
6. Проверить, что salary в ответе равно salary s request (salary забрать из request.)
```javascript
pm.test("Check salary", function () {
    pm.expect(+req_f.salary).to.eql(resp_f.salary);
});
```
7. Вывести в консоль параметр family из response.
```javascript
console.log(resp_f.family)
```
8. Проверить, что у параметра dog есть параметры name.
```javascript
let resp_dog = resp_f.family.pets.dog;

pm.test("dog has property name", function () {
    pm.expect(resp_dog).to.have.property("name");
});
```
9. Проверить, что у параметра dog есть параметры age.
```javascript
pm.test("dog has property age", function () {
    pm.expect(resp_dog).to.have.property("age");
});
```
10. Проверить, что параметр name имеет значение Luky.
```javascript
let resp_dog_name = resp_f.family.pets.dog.name;

pm.test("Check dog name", function () {
    pm.expect(resp_dog_name).to.eql('Luky');
});
```
11. Проверить, что параметр age имеет значение 4.
```javascript
let resp_dog_age = resp_f.family.pets.dog.age;

pm.test("Check dog age", function () {
    pm.expect(resp_dog_age).to.eql(4);
});
```
---
1. Отправить запрос GET http://162.55.220.72:5005/object_info_4
Response:
```javascript
{
    "age": 31,
    "name": "DmitriiD",
    "salary": [
        150000,
        "300000",
        "450000"
    ]
}
```
2. Спарсить response body в json.
```javascript
var resp_f = pm.response.json();
```
3. Спарсить request.
```javascript
let req_f = pm.request.url.query.toObject()
```
4. Проверить, что name в ответе равно name s request (name забрать из request.)
```javascript
pm.test("Check name", function () {
    pm.expect(req_f.name).to.eql(resp_f.name);
});
```
5. Проверить, что age в ответе равно age из request (age забрать из request.)
```javascript
pm.test("Check age", function () {
    pm.expect(+req_f.age).to.eql(resp_f.age);
});
```
6. Вывести в консоль параметр salary из request.
```javascript
console.log("Salary_req = " + +req_f.salary)
```
7. Вывести в консоль параметр salary из response.
```javascript
console.log("Salary_resp = " + resp_f.salary)
```
8. Вывести в консоль 0-й элемент параметра salary из response.
```javascript
console.log("Salary[0] = " + resp_f.salary[0])
```
9. Вывести в консоль 1-й элемент параметра salary параметр salary из response.
```javascript
console.log("Salary[1] = " + resp_f.salary[1])
```
10. Вывести в консоль 2-й элемент параметра salary параметр salary из response.
```javascript
console.log("Salary[2] = " + resp_f.salary[2])
```
11. Проверить, что 0-й элемент параметра salary равен salary из request (salary забрать из request.)
```javascript
pm.test("Salary resp[0] to eql req", function () {
    pm.expect(resp_f.salary[0]).to.eql(+req_f.salary);
});
```
12. Проверить, что 1-й элемент параметра salary равен salary*2 из request (salary забрать из request.)
```javascript
pm.test("Salary resp[1] to eql req * 2", function () {
    pm.expect(+resp_f.salary[1]).to.eql(req_f.salary * 2);
});
```
13. Проверить, что 2-й элемент параметра salary равен salary*3 из request (salary забрать из request.)
```javascript
pm.test("Salary resp[2] to eql req * 3", function () {
    pm.expect(+resp_f.salary[2]).to.eql(req_f.salary * 3);
});
```
14. Создать в окружении переменную name
15. Создать в окружении переменную age
16. Создать в окружении переменную salary
17. Передать в окружение переменную name
```javascript
pm.environment.set("name", resp_f.name);
```
18. Передать в окружение переменную age
```javascript
pm.environment.set("age", resp_f.age);
```
19. Передать в окружение переменную salary
```javascript
pm.environment.set("salary", resp_f.salary[0]);
```
20. Написать цикл который выведет в консоль по порядку элементы списка из параметра salary
```javascript
for (let i = 0; i < Object.keys(resp_f.salary).length; i++){
    console.log("salary from cycle =" + resp_f.salary[i])
}
```
---
1. Вставить параметр salary из окружения в request
2. Вставить параметр age из окружения в age
3. Вставить параметр name из окружения в name
4. Отправить запрос POST http://162.55.220.72:5005/user_info_2
Response:
```javascript
{
    "person": {
        "u_age": 31,
        "u_name": [
            "DmitriiD",
            150000,
            31
        ],
        "u_salary_5_years": 630000.0
    },
    "qa_salary_after_1.5_year": 495000.0,
    "qa_salary_after_12_months": 405000.0,
    "qa_salary_after_3.5_years": 570000.0,
    "qa_salary_after_6_months": 300000,
    "start_qa_salary": 150000
}
```
5. Спарсить response body в json.
```javascript
var resp_f = pm.response.json();
```
6. Спарсить request.
```javascript
let req_f = request.data;
```
7. Проверить, что json response имеет параметр start_qa_salary
```javascript
pm.test("start_qa_salary", function () {
    pm.expect(resp_f).to.have.property("start_qa_salary");
});
```
8. Проверить, что json response имеет параметр qa_salary_after_6_months
```javascript
pm.test("qa_salary_after_6_months", function () {
    pm.expect(resp_f).to.have.property("qa_salary_after_6_months");
});
```
9. Проверить, что json response имеет параметр qa_salary_after_12_months
```javascript
pm.test("qa_salary_after_12_months", function () {
    pm.expect(resp_f).to.have.property("qa_salary_after_12_months");
});
```
10. Проверить, что json response имеет параметр qa_salary_after_1.5_year
```javascript
pm.test("qa_salary_after_1.5_year", function () {
    pm.expect(resp_f).to.have.property("qa_salary_after_1.5_year");
});
```
11. Проверить, что json response имеет параметр qa_salary_after_3.5_years
```javascript
pm.test("qa_salary_after_3.5_years", function () {
    pm.expect(resp_f).to.have.property("qa_salary_after_3.5_years");
});
```
12. Проверить, что json response имеет параметр person
```javascript
pm.test("response have property person", function () {
    pm.expect(resp_f).to.have.property("person");
});
```
13. Проверить, что параметр start_qa_salary равен salary из request (salary забрать из request.)
```javascript
pm.test("Check start_qa_salary value", function () {
    pm.expect(resp_f.start_qa_salary).to.eql(+req_f.salary);
});
```
14. Проверить, что параметр qa_salary_after_6_months равен salary*2 из request (salary забрать из request.)
```javascript
pm.test("Check qa_salary_after_6_months value", function () {
    pm.expect(resp_f.qa_salary_after_6_months).to.eql(req_f.salary * 2);
});
```
15. Проверить, что параметр qa_salary_after_12_months равен salary*2.7 из request (salary забрать из request.)
```javascript
pm.test("Check qa_salary_after_12_months value", function () {
    pm.expect(resp_f.qa_salary_after_12_months).to.eql(req_f.salary * 2.7);
});
```
16. Проверить, что параметр qa_salary_after_1.5_year равен salary*3.3 из request (salary забрать из request.)
```javascript
pm.test("Check qa_salary_after_1.5_year value", function () {
    pm.expect(resp_f["qa_salary_after_1.5_year"]).to.eql(req_f.salary * 3.3); // обходим "." в запросе через [""]
});
```
17. Проверить, что параметр qa_salary_after_3.5_years равен salary*3.8 из request (salary забрать из request.)
```javascript
pm.test("Check qa_salary_after_3.5_years value", function () {
    pm.expect(resp_f["qa_salary_after_3.5_years"]).to.eql(req_f.salary * 3.8);
});
```
18. Проверить, что в параметре person, 1-й элемент из u_name равен salary из request (salary забрать из request.)
```javascript
pm.test("Check resp_u_name eql req_name", function () {
    pm.expect(resp_f.person.u_name[0]).to.eql(req_f.name);
});
```
19. Проверить, что что параметр u_age равен age из request (age забрать из request.)
```javascript
pm.test("Check resp_u_age eql req_age", function () {
    pm.expect(resp_f.person.u_age).to.eql(+req_f.age);
});
```
20. Проверить, что параметр u_salary_5_years равен salary*4.2 из request (salary забрать из request.)
```javascript
pm.test("Check resp_salary_5_y eql req_salary_5_y", function () {
    pm.expect(resp_f.person.u_salary_5_years).to.eql(req_f.salary * 4.2);
});
```
21. ***Написать цикл который выведет в консоль по порядку элементы списка из параметра person.

```javascript
for (let i = 0; i < Object.keys(resp_f.person).length; i++){
    console.log([i] + " element from person = " + Object.values(resp_f.person)[i])
};
```
