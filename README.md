# Практическая работа 2: Типы данных, арифметика, условные операторы
**Студент:** Паринова Ксения Николаевна
**Группа:** 1зб_ИВТ(ускор.)/25
**Дата:** 02 апреля 2026
---
## Задание 2.1: Вычисление формулы
### Постановка задачи
Напишите программу, которая вычислит значение выражения.
для значений: a = 0.12, b = 3.5, c = 2.4, x = 1.4
### Математическая модель
Выражение состоит из двух дробей, которые вычитаются:
Первая дробь: $\frac{x-a}{\sqrt[3]{x^2+a^2}}$
Вторая дробь: $\frac{\sqrt[4]{(x^2+b^2)^3}}{2+a+b+\sqrt[3]{(x-c)^2}}$
Результат: $h = -\text{первая дробь} - \text{вторая дробь}$
### Список идентификаторов
| Имя | Тип | Описание |
|-----|-----|----------|
| a | double | Константа a = 0.12 |
| b | double | Константа b = 3.5 |
| c | double | Константа c = 2.4 |
| x | double | Переменная x = 1.4 |
| num1 | double | Числитель первой дроби |
| denom1 | double | Знаменатель первой дроби |
| term1 | double | Значение первой дроби|
| num2 | double | Числитель второй дроби |
| denom2 | double | Знаменатель второй дроби |
| term2 | double | Значение второй дроби |
| h | double | Результат вычисления |
### Код программы
```c
#include <stdio.h>
#include <math.h>

int main(void) {
    double a = 0.12, b = 3.5, c = 2.4, x = 1.4;
    
    double num1 = x - a;  // числитель: (x - a)
    double denom1 = pow(x*x + a*a, 1.0/3.0);  // знаменатель: ∛(x² + a²)
    double term1 = num1 / denom1;  // первая дробь
    
    double num2 = pow(x*x + b*b, 3.0/4.0);  // числитель: ∜((x² + b²)³)
    double denom2 = 2 + a + b + pow(pow(x-c,2),1.0/3.0);  // знаменатель
    double term2 = num2 / denom2;  // вторая дробь
    
    double h = -term1 - term2;
    
    printf("h(%.2f) = %.6f\n", x, h);
    
    return 0;
}
```
### Результаты работы
![Результат вычисления](practice-2/screenshot/task2-1.png)
---
## Задание 2.2: Чётное или нечётное
### Постановка задачи
Напишите программу, которая определяет, является ли введённое число чётным или нечётным.
### Математическая модель
Число является чётным, если остаток от деления на 2 равен 0:
nmod2=0
### Список идентификаторов
| Имя | Тип | Описание |
|-----|-----|----------|
| number | int | Введённое число |
### Код программы
```c
#include <stdio.h>

int main(void) {
    int number;
    
    printf("Enter number: ");
    scanf("%d", &number);
    
    if (number % 2 == 0) {
        printf("%d is even\n", number);
    } else {
        printf("%d is odd\n", number);
    }
    
    return 0;
}
```
### Результаты работы
![Результат](practice-2/screenshot/task2-2.png)
---
## Задание 2.3: Максимум из трёх
### Постановка задачи
Напишите программу, которая находит максимальное из трёх введённых чисел.
### Математическая модель
Максимум из трёх чисел:
max(a,b,c)= 
a,если a≥b и a≥c
b,если b≥a и b≥c
c,в остальных случаях
### Список идентификаторов
| Имя | Тип | Описание |
|-----|-----|----------|
| a | int | Первое число |
| b | int | Второе число |
| c | int | Третье число |
| max | int | Максимальное значение |
### Код программы
```c
#include <stdio.h>

int main(void) {
    int a, b, c, max;
    
    printf("Enter three numbers: ");
    scanf("%d %d %d", &a, &b, &c);
    
    max = a;
    if (b > max) {
        max = b;
    }
    if (c > max) {
        max = c;
    }
    
    printf("Maximum: %d\n", max);
    
    return 0;
}
```
### Результаты работы
![Результат](practice-2/screenshot/task2-3.png)
---
## Задание 2.4: Тип треугольника
### Постановка задачи
Напишите программу, которая по трём сторонам определяет тип треугольника:
Равносторонний — все стороны равны
Равнобедренный — две стороны равны
Разносторонний — все стороны разные
Не существует — если сумма двух сторон меньше или равна третьей
### Математическая модель
Условие существования треугольника:
a+b>c и a+c>b и b+c>a
### Список идентификаторов
| Имя | Тип | Описание |
|-----|-----|----------|
| a | double | Первая сторона |
| b | double | Вторая сторона |
| c | double | Третья сторона |
### Код программы
```c
#include <stdio.h>

int main(void) {
    double a, b, c;
    
    printf("Enter sides a, b, c: ");
    scanf("%lf %lf %lf", &a, &b, &c);
    
    if (a + b <= c || a + c <= b || b + c <= a) {
        printf("Triangle does not exist\n");
    }
    else if (a == b && b == c) {
        printf("Equilateral triangle\n");
    }
    else if (a == b || a == c || b == c) {
        printf("Isosceles triangle\n");
    }
    else {
        printf("Scalene triangle\n");
    }
    
    return 0;
}
```
### Результаты работы
![Результат](practice-2/screenshot/task2-4-1.png)
![Результат](practice-2/screenshot/task2-4-2.png)
![Результат](practice-2/screenshot/task2-4-3.png)
![Результат](practice-2/screenshot/task2-4-4.png)
---
## Задание 2.5: Квадратное уравнение
### Постановка задачи
Напишите программу для решения квадратного уравнения $ax^2 + bx + c = 0$:
Вычислить дискриминант: $D = b^2 - 4ac$
Если $D > 0$: два корня $x_{1,2} = \frac{-b \pm \sqrt{D}}{2a}$
Если $D = 0$: один корень $x = \frac{-b}{2a}$
Если $D < 0$: корней нет
### Математическая модель
D=b² −4ac
x1,2=-b+-sqrt(D), D>0
x=-b/2a, D=0
### Список идентификаторов
| Имя | Тип | Описание |
|-----|-----|----------|
| a | double | Коэффициент при x² |
| b | double | Коэффициент при x |
| c | double | Свободный член |
| D | double | Дискриминант |
| x1 | double | Первый корень |
| x2 | double | Второй корень |
### Код программы
```c
#include <stdio.h>
#include <math.h>

int main(void) {
    double a, b, c, D, x1, x2;
    
    printf("Enter a, b, c: ");
    scanf("%lf %lf %lf", &a, &b, &c);
    
    if (a == 0) {
        printf("This is not a quadratic equation (a = 0)\n");
        return 1;
    }
    
    D = b*b - 4*a*c;
    
    printf("D = %.2f\n", D);
    
    if (D > 0) {
        x1 = (-b + sqrt(D)) / (2*a);
        x2 = (-b - sqrt(D)) / (2*a);
        printf("x1 = %.2f\n", x1);
        printf("x2 = %.2f\n", x2);
    }
    else if (D == 0) {
        x1 = -b / (2*a);
        printf("x = %.2f\n", x1);
    }
    else {
        printf("No real roots\n");
    }
    
    return 0;
}
```
### Результаты работы
![Результат] (practice-2/screenshot/task2-5-1.png)
![Результат] (practice-2/screenshot/task2-5-2.png)
![Результат] (practice-2/screenshot/task2-5-3.png)
---
## Задание 2.6: Калькулятор
### Постановка задачи
Напишите программу-калькулятор, которая:
Запрашивает два числа
Запрашивает операцию (+, -, *, /)
Выводит результат
Обрабатывает деление на ноль
### Математическая модель
a+b,a−b,a×b,a÷b (при b!=0)
### Список идентификаторов
| Имя | Тип | Описание |
|-----|-----|----------|
| num1 | double | Первое число |
| num2 | double | Второе число |
| result | double | Результат операции |
| operation | char | Знак операции (+, -, *, /) |
### Код программы
```c
#include <stdio.h>

int main(void) {
    double num1, num2, result;
    char operation;
    
    printf("Enter first number: ");
    scanf("%lf", &num1);
    
    printf("Enter second number: ");
    scanf("%lf", &num2);
    
    printf("Enter operation (+, -, *, /): ");
    scanf(" %c", &operation);  
    
    switch (operation) {
        case '+':
            result = num1 + num2;
            printf("Result: %.2f + %.2f = %.2f\n", num1, num2, result);
            break;
        case '-':
            result = num1 - num2;
            printf("Result: %.2f - %.2f = %.2f\n", num1, num2, result);
            break;
        case '*':
            result = num1 * num2;
            printf("Result: %.2f * %.2f = %.2f\n", num1, num2, result);
            break;
        case '/':
            if (num2 != 0) {
                result = num1 / num2;
                printf("Result: %.2f / %.2f = %.2f\n", num1, num2, result);
            } else {
                printf("Error: Division by zero!\n");
            }
            break;
        default:
            printf("Error: Invalid operation!\n");
    }
    
    return 0;
}
```
### Результаты работы
![Результат](practice-2/screenshot/task2-6-1.png)
![Результат](practice-2/screenshot/task2-6-2.png)
---
