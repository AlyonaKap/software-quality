# Лаборатоорна робота 2
## Проєктування тестів. Checklist, Test Cases та Decision Table

**Виконала:** Капінос Альона
**Група:** 6.1213-2пі
**Дата виконання:** 24.09.2026

## Test Conditions 

- TCND-01 - авторизація з обліковими даними користувача, що існує в системі;
- TCND-02 - авторизація з валідним Password,але неправильним Username;
- TCND-03- авторизація з валідним Username, але неправильним Password;
- TCND-04 - авторизація з порожнім Username, але заповненим Password;
- TCND-05 - авторизація з порожнім Password, але заповненим Username;
- TCND-06 - авторизація заблокованого користувача.


## Checklist

- Авторизація з обліковими даними користувача, що існує в системі > успіх;
- Авторизація з валідним Password,але неправильним Username > помилка;
- Авторизація з валідним Username, але неправильним Password > помилка;
- Авторизація з порожнім Username, але заповненим Password > помилка;
- Авторизація з порожнім Password, але заповненим Username > помилка;
- Авторизація заблокованого користувача > помилка;

## Test Cases

### TC-LOGIN-01. Успішна авторизація standard_user

**Type:** Positive 

**Preconditions:** 
- Сторінка Login (https://www.saucedemo.com) відкрита 
- Користувач не авторизований в системі

**Test Data:**
Username: standard_user
Password: secret_sauce

**Steps:**
1. Ввести Username з Test Data y поле Username
2. Ввести Password з Test Data у поле Password
3. Натиснути на кнопку Login

**Expected Result:**
1. Username відображається у полі без повідомлення про помилку
2. Password відображається у полі без повідомлення про помилку
3. Користувач успішно авторизовується у системі 

**Actual Result:**
Після введення валідних Username та Password та натискання на кнопку Login користувач авторизовується та відбувається перехід на сторінку Product. 

**Status:**
Passed 

### TC-LOGIN-02. Авторизація з валідним Username, але неправильним Password

**Type:** Negative 

**Preconditions:** 
- Сторінка Login (https://www.saucedemo.com) відкрита 
- Користувач не авторизований в системі

**Test Data:**
Username: standard_user
Password: 12345678

**Steps:**
1. Ввести Username з Test Data y поле Username
2. Ввести Password з Test Data у поле Password
3. Натиснути на кнопку Login

**Expected Result:**
1. Username відображається у полі без повідомлення про помилку
2. Password відображається у полі без повідомлення про помилку
3. Виводиться повідомлення про некоректно введені облікові дані - користувач не авторизовується. 

**Actual Result:**
Після введення валідного Username та невалідного Password та натискання на кнопку Login користувач не авторизовується - відбувається вивід помилки "Epic sadface: Username and password do not match any user in this service". 

**Status:**
Passed 


### TC-LOGIN-03. Авторизація заблокованого користувача

**Type:** Negative 

**Preconditions:** 
- Сторінка Login (https://www.saucedemo.com) відкрита 
- Користувач не авторизований в системі
- Користувач був заблокований

**Test Data:**
Username: locked_out_user
Password: secret_sauce

**Steps:**
1. Ввести Username з Test Data y поле Username
2. Ввести Password з Test Data у поле Password
3. Натиснути на кнопку Login

**Expected Result:**
1. Username відображається у полі без повідомлення про помилку
2. Password відображається у полі без повідомлення про помилку
3. Виводиться повідомлення про те, що користувач заблокований - авторизація користувача не відбувається.

**Actual Result:**
Після введення облікових даних заблокованого користовуча та натискання на кнопку Login користувач не авторизовується - відбувається вивід помилки "Epic sadface: Sorry, this user has been locked out.". 

**Status:**
Passed 

## Decision Table

Були додані правила:
- R3. invalid Username + valid Password
- R4. valid Username + invalid Password
- R5. invalid Username + invalid Password

| | R1 | R2 | R3 | R4 | R5 |
|---|---|---|---|---|---|
| Username входить до списку допустимих? | T | T | F | T | F |
| Password правильний? | T | T | T | F | F |
| Користувач заблокований? | F | T | – | – | – |
| **A1: Products** | X | | | | |
| **A2: Locked message** | | X | | | |
| **A3: Invalid credentials** | | | X | X | X |

Правила, що залишилися без окремого Test Case: R3. invalid Username + valid Password, R5. invalid Username + invalid Password

## Результати виконання

| Test Case | Type | Result |
|---|---|---|
| TC-LOGIN-01 | Positive | Passed |
| TC-LOGIN-02 | Negative | Passed |
| TC-LOGIN-03 | Negative | Passed |









