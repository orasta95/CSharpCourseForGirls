## Глава 2. Работа с переменными, операторами и выражениями

### Содержание
- Переменные и константы
- Типы данных
- Арифметические операции языка C#
- Конструкция if..else и тернарная операция
- Конструкция switch

## 1.1 Переменные 

Для хранения данных в программе применяются переменные. Переменная представляет именнованную область памяти, в которой хранится значение определенного типа. Переменная имеет тип, имя и значение. Тип определяет, какого рода информацию может хранить переменная.

```
тип имя_переменной;
```

Например, определим простейшую переменную:

```
string name;
```

Отличительной чертой переменных является то, что в программе можно многократно менять их значение. Например, создадим небольшую программу, в которой определим переменную, поменяем ее значение и выведем его на консоль:

```
string name = "Anna";  // определяем переменную и инициализируем ее
  
Console.WriteLine(name);    
  
name = "Mercedes";       
Console.WriteLine(name);    
```
## 1.2 Константы

Отличительной особенностью переменных является то, что мы можем изменить их значение в процессе работы программы. Но, кроме того, в C# есть константы. Константа должна быть обязательно инициализирована при определении, и после определения значение константы не может быть изменено
Для определения констант используется ключевое слово const, которое указывается перед типом константы:

```
const string NAME = "Bella";
```

Так, в следующем случае мы получим ошибку, так как константе не присвоено начальное значение:

```
const string NAME;  // ! Ошибка - константа NAME не инициализирована
```

Кроме того, мы ее не сможем изменить в процессе работы программы:

```
const string NAME = "Tom";  // определяем константу
NAME = "Bob";   // !Ошибка - у констаты нельзя изменить значение
```

## 1.3 Типы данных

Как и во многих языках программирования, в C# есть своя система типов данных, которая используется для создания переменных. Тип данных определяет внутреннее представление данных, множество значений, которые может принимать объект, а также допустимые действия, которые можно применять над объектом.

В языке C# есть следующие базовые типы данных:
#### bool:
  хранит значение true или false (логические литералы). Представлен системным типом System.Boolean

```
bool alive = true;
bool isDead = false;
```

#### int: 
хранит целое число от -2147483648 до 2147483647 и занимает 4 байта. Представлен системным типом System.Int32. Все целочисленные литералы по умолчанию представляют значения типа int:

```
int a = 10;
int b = 0b101;  // бинарная форма b =5
int c = 0xFF;   // шестнадцатеричная форма c = 255
```

#### float: 
хранит число с плавающей точкой от -3.4*1038 до 3.4*1038 и занимает 4 байта. Представлен системным типом System.Single
  
#### double: 
хранит число с плавающей точкой от ±5.0*10-324 до ±1.7*10308 и занимает 8 байта. Представлен системным типом System.Double

#### decimal: 
хранит десятичное дробное число. Если употребляется без десятичной запятой, имеет значение от ±1.0*10-28 до ±7.9228*1028, может хранить 28 знаков после запятой и занимает 16 байт. Представлен системным типом System.Decimal

#### char: 
хранит одиночный символ в кодировке Unicode и занимает 2 байта. Представлен системным типом System.Char. Этому типу соответствуют символьные литералы:

```
char a = 'A';
char b = '\x5A';
char c = '\u0420';
```

#### string: 
хранит набор символов Unicode. Представлен системным типом System.String. Этому типу соответствуют строковые литералы.

```
string hello = "Hello";
string word = "world";
```

#### object: 
может хранить значение любого типа данных и занимает 4 байта на 32-разрядной платформе и 8 байт на 64-разрядной платформе. Представлен системным типом System.Object, который является базовым для всех других типов и классов .NET.

```
object a = 22;
object b = 3.14;
object c = "hello code";
```

Например, определим несколько переменных разных типов и выведем их значения на консоль:

```
string name = "Tom";
int age = 33;
bool isEmployed = false;
double weight = 78.65;
 
Console.WriteLine($"Имя: {name}");
Console.WriteLine($"Возраст: {age}");
Console.WriteLine($"Вес: {weight}");
Console.WriteLine($"Работает: {isEmployed}");
```

## Использование суффиксов

При присвоении значений надо иметь в виду следующую тонкость: все вещественные литералы (дробные числа) рассматриваются как значения типа double. И чтобы указать, что дробное число представляет тип float или тип decimal, необходимо к литералу добавлять суффикс: F/f - для float и M/m - для decimal.

```
float a = 3.14F;
float b = 30.6f;
 
decimal c = 1005.8M;
decimal d = 334.8m;
```

## Неявная типизация

Однако мы можем использовать и модель неявной типизации:

```
var hello = "Hell to World";
var c = 20;
```

Эти переменные подобны обычным, однако они имеют некоторые ограничения.
Во-первых, мы не можем сначала объявить неявно типизируемую переменную, а затем инициализировать:

```
// этот код работает
int a;
a = 20;
 
// этот код не работает
var c;
c= 20;
```

## 1.4 Арифметические операции языка C#

В C# используется большинство операций, которые применяются и в других языках программирования. Операции представляют определенные действия над операндами - участниками операции. В качестве операнда может выступать переменной или какое-либо значение (например, число). Операции бывают унарными (выполняются над одним операндом), бинарными - над двумя операндами и тернарными - выполняются над тремя операндами. Рассмотрим все виды операций.

Бинарные арифметические операции:
* Операция сложения двух чисел: +
 
```
int x = 10;
int z = x + 12; // 22
```

* Операция вычитания двух чисел: -

```
int x = 10;
int z = x - 6; // 4
```

* Операция умножения двух чисел: *

```
int x = 10;
int z = x * 5; // 50
```

* Oперация деления двух чисел: /

```
int x = 10;
int z = x / 5; // 2
 
double a = 10;
double b = 3;
double c = a / b; // 3.33333333
```

При делении стоит учитывать, что если оба операнда представляют целые числа, то результат также будет округляться до целого числа:

```
double z = 10 /  4; //результат равен 2
```

Для выхода из этой ситуации необходимо определять литералы или переменные, участвующие в операции, именно как типы double или float:

```
double z = 10.0 /  4.0; //результат равен 2.5
```

* Операция получение остатка от целочисленного деления двух чисел: %

```
double x = 10.0;
double z = x % 4.0; //результат равен 2
```

#### Также есть ряд унарных операций, в которых принимает участие один операнд:

Операция инкремента (++)
Инкремент бывает префиксным: ++x - сначала значение переменной x увеличивается на 1, а потом ее значение возвращается в качестве результата операции.

И также существует постфиксный инкремент: x++ - сначала значение переменной x возвращается в качестве результата операции, а затем к нему прибавляется 1.

```
int x1 = 5;
int z1 = ++x1; // z1=6; x1=6
Console.WriteLine($"{x1} - {z1}");
 
int x2 = 5;
int z2 = x2++; // z2=5; x2=6
Console.WriteLine($"{x2} - {z2}");
```

Операция декремента или уменьшения значения на единицу. Также существует префиксная форма декремента (--x) и постфиксная (x--). (--)

```
int x1 = 5;
int z1 = --x1; // z1=4; x1=4
Console.WriteLine($"{x1} - {z1}");
 
int x2 = 5;
int z2 = x2--; // z2=5; x2=4
Console.WriteLine($"{x2} - {z2}");
```

#### Ассоциативность операторов

Как выше было отмечено, операции умножения и деления имеют один и тот же приоритет, но какой тогда результат будет в выражении:

```
int x = 10 / 5 * 2;
```

Стоит нам трактовать это выражение как (10 / 5) * 2 или как 10 / (5 * 2)? Ведь в зависимости от трактовки мы получим разные результаты.

Когда операции имеют один и тот же приоритет, порядок вычисления определяется ассоциативностью операторов. В зависимости от ассоциативности есть два типа операторов:

- Левоассоциативные операторы, которые выполняются слева направо

- Правоассоциативные операторы, которые выполняются справа налево

Все арифметические операторы являются левоассоциативными, то есть выполняются слева направо. Поэтому выражение 10 / 5 * 2 необходимо трактовать как (10 / 5) * 2, то есть результатом будет 4.


### Домашнее задание
1. Programming Taskbook Электронный задачник по программированию
   - Integer2, Integer4 страница 10
   - Boolean3, Boolean5 страница 12   
