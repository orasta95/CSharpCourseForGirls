## Создание методов и применение областей видимости

### Содержание
- Определение метода
- Вызов методов
- Сокращенная запись методов
- Соответствие параметов и аргументов по типу данных
- Необязательные параметры
- Возвращение значения и оператор return
- Массив в качестве параметра


Если переменные хранят некоторые значения, то методы содержат собой набор инструкций, которые выполняют определенные действия. По сути метод - это именованный блок кода, который выполняет некоторые действия.

Общее определение методов выглядит следующим образом:

```
[модификаторы] тип_возвращаемого_значения название_метода ([параметры])
{
    // тело метода
}
```

Модификаторы и параметры необязательны.

Ранее мы уже использовали как минимум один метод - Console.WriteLine(), который выводит информацию на консоль. Теперь рассмотрим, как мы можем создавать свои методы.

### Определение метода

Определим один метод:

```
void SayHello()
{
    Console.WriteLine("Hello");
}
```

Здесь определен метод SayHello, который выводит некоторое сообщение. К названиям методов предъявляются в принципе те же требования, что и к названиям переменных. Однако, как правило, названия методов начинаются с большой буквы.

Перед названием метода идет возвращаемый тип данных. Здесь это тип void, который указыает, что фактически ничего не возвращает, он просто производит некоторые действия.

После названия метода в скобках идет перечисление параметров. Но в данном случае скобки пустые, что означает, что метод не принимает никаких параметров.

После списка параметров в круглых скобках идет блок кода, который представляет набор выполняемых методом инструкций. В данном случае блок метода SayHello содержит только одну инструкцию, которая выводит строку на консоль:

```
Console.WriteLine("Hello");
```

Но если мы запустим данный проект, то мы не увидим никакой строки, которую должен выводить метод SayHello. Потому что после определения метод еще надо вызвать, чтобы он выполнил свою работу.

### Вызов методов

Чтобы использовать метод SayHello, нам надо его вызвать. Для вызова метода указывается его имя, после которого в скобках идут значения для его параметров (если метод принимает параметры).

```
название_метода (значения_для_параметров_метода);
```

Например, вызов метода SayHello будет выглядеть следующим образом:

```
SayHello();
```

Поскольку метод не принимает никаких параметров, то после названия метода идут пустые скобки.

Объединим определение и вызов метода:

```
void SayHello()
{
    Console.WriteLine("Hello");
}
 
SayHello(); // Hello
SayHello(); // Hello
```

Преимуществом методов является то, что их можно повторно и многократно вызывать в различных частях программы. Например, в примере выше два раза вызывается метод SayHello.

При этом в данном случае нет разницы, сначала определяется метод, а потом вызывается или наоборот. Например, мы могли бы написать и так:

```
SayHello(); // Hello
SayHello(); // Hello
 
void SayHello()
{
    Console.WriteLine("Hello");
}
```

Определим и вызовем еще несколько методов:

```
ivoid SayHelloRu()
{
    Console.WriteLine("Привет");
}
void SayHelloEn()
{
    Console.WriteLine("Hello");
}
void SayHelloFr()
{
    Console.WriteLine("Salut");
}
 
 
string language = "en";
 
switch (language)
{
    case "en": 
        SayHelloEn();
        break;
    case "ru":
        SayHelloRu();
        break;
    case "fr":
        SayHelloFr();
        break;
}
```

Здесь определены три метода SayHelloRu(), SayHelloEn() и SayHelloFr(), которые также имеют тип void, не принимают никаких параметров и также выводит некоторую строку на консоль. Условно говоря, они выводят приветствие на определенном языке.

В конструкции switch проверяется значение переменной language, которая условно хранит код языка, и в зависимости от ее значения вызывается определенный метод. Так, в данном случае на консоль будет выведено.

### Сокращенная запись методов

Если метод в качестве тела определяет только одну инструкцию, то мы можем сократить определение метода. Например, допустим у нас есть метод:

```
void SayHello()
{
    Console.WriteLine("Hello");
}
```

Мы можем его сократить следующим образом:

```
void SayHello() => Console.WriteLine("Hello");
```

То есть после списка параметров ставится оператор =>, после которого идет выполняемая инструкция.

Параметры позволяют передать в метод некоторые входные данные. Параметры определяются через заятую в скобках после названия метода в виде:

```
тип_метода имя_метода (тип_параметра1 параметр1, тип_параметра2 параметр2, ...)
{
    // действия метода
}
```

Определение параметра состоит из двух частей: сначала идет тип параметра и затем его имя.

Например, определим метод PrintMessage, который получает извне выводимое сообщение:

```
void PrintMessage(string message)
{
    Console.WriteLine(message);
}
 
PrintMessage("Hello work");           // Hello work
PrintMessage("Hello METANIT.COM");    // Hello METANIT.COM
PrintMessage("Hello C#");             // Hello C#
```

Здесь метод PrintMessage() принимает один параметр, который называется message и имеет тип string.

Чтобы выполнить метод, который имеет параметры, при вызове после имени метода в скобках ему передаются значения для его параметров, например:

```
PrintMessage("Hello work");
```

Здесь параметру message передается строка "Hello work". Значения, которые передаются параметрам, еще называются аргументами. То есть передаваемая строка "Hello work" в данном случае является аргументом.

Иногда можно встретить такие определения как формальные параметры и фактические параметры. Формальные параметры - это собственно параметры метода (в данном случае message), а фактические параметры - значения, которые передаются формальным параметрам. То есть фактические параметры - это и есть аргументы метода.

Определим еще один метод, который складывает два числа:

```
void Sum(int x, int y)
{
    int result = x + y;
    Console.WriteLine($"{x} + {y} = {result}");
}
 
Sum(10, 15);    // 10 + 15 = 25
```

Метод Sum имеет два параметра: x и y. Оба параметра представляют тип int. Поэтому при вызове данного метода нам обязательно надо передать на место этих параметров два числа. Внутри метода вычисляется сумма переданных чисел и выводится на консоль.

При вызове метода Sum значения передаются параметрам по позиции. Например, в вызове Sum(10, 15) число 10 передается параметру x, а число 15 - параметру y.

Также параметры могут использоваться в сокращеной версии метода:

```
void Sum(int x, int y) => Console.WriteLine($"{x} + {y} = { x + y }");
 
Sum(10, 15);    // 10 + 15 = 25
```

Передаваемые параметру значения могут представлять значения переменных или результат работы сложных выражений, которые возвращают некоторое значение:

```
void Sum(int x, int y) => Console.WriteLine($"{x} + {y} = { x + y }");
 
int a = 10, b = 15, c = 6;
Sum(a, b);                  // 10 + 15 = 25
Sum(3, c);                  // 3 + 6 = 9
Sum(14, 4 + c);             // 14 + 10 = 24
```

Если параметрами метода передаются значения переменных, то таким переменным должно быть присвоено значение. Например, следующая программа не скомпилируется:

```
void Sum(int x, int y)
{
    Console.WriteLine($"{x} + {y} = { x + y }");
}
 
int a;
int b = 15;
Sum(a, b);  // ! Ошибка
```

### Соответствие параметов и аргументов по типу данных

При передаче значений параметрам важно учитывать тип параметров: между аргументами и параметрами должно быть соответствие по типу. Например:

```
void PrintPerson(string name, int age)
{
    Console.WriteLine($"Name: {name}  Age: {age}");
}
 
PrintPerson("Tom", 24); // Name: Tom  Age: 24
```

В данном случае первый параметр метода PrintPerson() представляет тип string, поэтому при вызове метода мы должны передать этому параметру значение типа string, то есть строку. Второй параметр представляет тип int, поэтому должны передать ему целое число, которое соответствует типу int.

```
PrintPerson("Tom", 24);
```

Также мы можем передать параметрам значения тех типов, которые автоматически могут быть преобразованы в тип параметров. Например:

```
void PrintPerson(string name, int age)
{
    Console.WriteLine($"Name: {name}  Age: {age}");
}
 
byte b = 37;
PrintPerson("Tom", b); // Name: Tom  Age: 37
```

Здесь параметру типа int передается значение типа byte, но комилятор может автоматически преобразовать значение типа byte к тиу int. Поэтому здесь ошибки не возникнет.
Данные других типов мы передать параметров не можем. Например, следующий вызов метода PrintPerson будет ошибочным:

```
PrintPerson(45, "Bob"); 
```

### Необязательные параметры

По умолчанию при вызове метода необходимо предоставить значения для всех его параметров. Но C# также позволяет использовать необязательные параметры. Для таких параметров нам необходимо объявить значение по умолчанию. Также следует учитывать, что после необязательных параметров все последующие параметры также должны быть необязательными:

```
void PrintPerson(string name, int age = 1, string company = "Undefined")
{
    Console.WriteLine($"Name: {name}  Age: {age}  Company: {company}");
}
```

Здесь параметры age и company являются необязательными, так как им присвоены значения. Поэтому при вызове метода мы можем не передавать для них данные:

```
void PrintPerson(string name, int age = 1, string company = "Undefined")
{
    Console.WriteLine($"Name: {name}  Age: {age}  Company: {company}");
}
 
PrintPerson("Tom", 37, "Microsoft");  // Name: Tom  Age: 37  Company: Microsoft
PrintPerson("Tom", 37);               // Name: Tom  Age: 37  Company: Undefined
PrintPerson("Tom");                   // Name: Tom  Age: 1   Company: Undefined
```

### Именованные параметры
В предыдущих примерах при вызове методов значения для параметров передавались в порядке объявления этих параметров в методе. То есть аргументы передавались параметрам по позиции. Но мы можем нарушить подобный порядок, используя именованные параметры:

```
void PrintPerson(string name, int age = 1, string company = "Undefined")
{
    Console.WriteLine($"Name: {name}  Age: {age}  Company: {company}");
}
 
PrintPerson("Tom", company:"Microsoft", age: 37);  // Name: Tom  Age: 37  Company: Microsoft
PrintPerson(age:41, name: "Bob");          // Name: Bob  Age: 41  Company: Undefined
PrintPerson(company:"Google", name:"Sam"); // Name: Sam  Age: 1   Company: Google
```

Для передачи значений параметрам о имени при вызове метода указывается имя параметра и через двоеточие его значение: name:"Tom"

### Возвращение значения и оператор return

Метод может возвращать значение, какой-либо результат. В примере выше были определены два метода, которые имели тип void. Методы с таким типом не возвращают никакого значения. Они просто выполняют некоторые действия.

Но методы также могут возвращать некоторое значение. Для этого применяется оператор return, после которого идет возвращаемое значение:

```
return возвращаемое значение;
```

Например, определим метод, который возвращает значение типа string:

```
string GetMessage()
{
    return "Hello";
}
```

Метод GetMessage имеет тип string, следовательно, он должен возвратить строку. Поэтому в теле метода используется оператор return, после которого указана возвращаемая строка.

При этом методы, которые в качестве возвращаемого типа имеют любой тип, кроме void, обязательно должны использовать оператор return для возвращения значения. Например, следующее определение метода некорректно:

```
string GetMessage()
{
    Console.WriteLine("Hello");
}
```

Также между возвращаемым типом метода и возвращаемым значением после оператора return должно быть соответствие. Например, в следующем случае возвращаемый тип - string, но метод возвращает число (тип int), поэтому такое определение метода некорректно:

```
string GetMessage()
{
    return 3;   // Ошибка! Метод должен возвращать строку, а не число
}
```

Результат методов, который возвращают значение, мы можем присвоить переменным или использовать иным образом в программе:

```
string GetMessage()
{
    return "Hello";
}
 
string message = GetMessage();  // получаем результат метода в переменную message
Console.WriteLine(message);     // Hello
```

Метод GetMessage() возвращает значение типа string. Поэтому мы можем присвоить это значение какой-нибудь переменной типа string: string message = GetMessage();

Либо даже передать в качестве значения параметру другого метода:

```
string GetMessage()
{
    return "Hello";
}
void PrintMessage(string message)
{
    Console.WriteLine(message);
}
PrintMessage(GetMessage());
```

В вызове PrintMessage(GetMessage()) сначада вызывается метод GetMessage() и его результат передается параметру message метода PrintMessage

После оператора return также можно указывать сложные выражения или вызовы других методов, которые возвращают определенный результат. Например, определим метод, который возвращает сумму чисел:

```
int Sum(int x, int y)
{
    return x + y;
}
 
int result = Sum(10, 15);   // 25
Console.WriteLine(result);   // 25
 
Console.WriteLine(Sum(5, 6));   // 11
```

Метод Sum() имеет тип int, следовательно, он должен возвратить значение типа int - целое число. Поэтому в теле метода используется оператор return, после которого указано возвращаемое число (в данном случае результат суммы переменных x и y).

### Сокращенная версия методов с результатом
Также мы можем сокращать методы, которые возвращают значение:

```
string GetMessage()
{
    return "hello";
}
```

аналогичен следующему методу:

```
string GetMessage() => "hello";
```

А метод

```
int Sum(int x, int y)
{
    return x + y;
}
```

аналогичен следующему методу:

```
int Sum(int x, int y) => x + y;
```

### Выход из метода
Оператор return не только возвращает значение, но и производит выход из метода. Поэтому он должен определяться после остальных инструкций. Например:

```
string GetHello()
{
    return "Hello";
    Console.WriteLine("After return");
}
```

С точки зрения синтаксиса данный метод корректен, однако его инструкция Console.WriteLine("After return") не имеет смысла - она никогда не выполнится, так как до ее выполнения оператор return возвратит значение и произведет выход из метода.

Однако мы можем использовать оператор return и в методах с типом void. В этом случае после оператора return не ставится никакого возвращаемого значения (ведь метод ничего не возвращает). Типичная ситуация - в зависимости от опеределенных условий произвести выход из метода:

```
void PrintPerson(string name, int age)
{
    if(age > 120 || age < 1)
    {
        Console.WriteLine("Недопустимый возраст");
        return;
    }
    Console.WriteLine($"Имя: {name}  Возраст: {age}");
}
 
PrintPerson("Tom", 37);         // Имя: Tom  Возраст: 37
PrintPerson("Dunkan", 1234);    // Недопустимый возраст
```

Здесь метод PrintPerson() в качестве параметров принимает имя и возраст пользователя. Однако в методе вначале мы проверяем, соответствует ли возраст некоторому диапазону (меньше 120 и больше 0). Если возраст находится вне этого диапазона, то выводим сообщение о недопустимом возрасте и с помощью оператора return выходим из метода. После этого метод заканчивает свою работу.

### Передача параметров по значению
Наиболее простой способ передачи параметров представляет передача по значению, по сути это обычный способ передачи параметров:

```
void Increment(int n)
{
    n++;
    Console.WriteLine($"Число в методе Increment: {n}");
}
 
int number = 5;
Console.WriteLine($"Число до метода Increment: {number}");
Increment(number);
Console.WriteLine($"Число после метода Increment: {number}");
```

При передаче аргументов параметрам по значению параметр метода получает не саму переменную, а ее копию и далее работает с этой копией независимо от самой переменной.

Так, выше при вызове метод Increment получает копию переменной number и увеличивает значение этой копии. Поэтому в самом методе Increment мы видим, что значение параметра n увеличилось на 1, но после выполнения метода переменная number имеет прежнее значение - 5. То есть изменяется копия, а сама переменная не изменяется.

Передача параметров по ссылке и модификатор ref
При передаче параметров по ссылке перед параметрами используется модификатор ref:

```
void Increment(ref int n)
{
    n++;
    Console.WriteLine($"Число в методе Increment: {n}");
}
 
int number = 5;
Console.WriteLine($"Число до метода Increment: {number}");
Increment(ref number);
Console.WriteLine($"Число после метода Increment: {number}");
```

При передаче значений параметрам по ссылке метод получает адрес переменной в памяти. И, таким образом, если в методе изменяется значение параметра, передаваемого по ссылке, то также изменяется и значение переменной, которая передается на его место..

Так, в метод Increment передается ссылка на саму переменную number в памяти. И если значение параметра n в Increment изменяется, то это приводит и к изменению переменной number, так как и параметр n и переменная number указывают на один и тот же адрес в памяти.

Обратите внимание, что модификатор ref указывается как перед параметром при объявлении метода, так и при вызове метода перед аргументом, который передается параметру.

### Выходные параметры. Модификатор out

Выше мы использовали входные параметры. Но параметры могут быть также выходными. Чтобы сделать параметр выходным, перед ним ставится модификатор out:

```
void Sum(int x, int y, out int result)
{
    result = x + y;
}
```

Здесь результат возвращается не через оператор return, а через выходной параметр result. Использование в программе:

```
void Sum(int x, int y, out int result)
{
    result = x + y;
}
 
int number;
 
Sum(10, 15, out number);
 
Console.WriteLine(number);   // 25
```

Причем, как и в случае с ref ключевое слово out используется как при определении метода, так и при его вызове.

Также обратите внимание, что методы, использующие такие параметры, обязательно должны присваивать им определенное значение. То есть следующий код будет недопустим, так как в нем для out-параметра не указано никакого значения:

```
void Sum(int x, int y, out int result)
{
    Console.WriteLine(x + y);
}
```

Прелесть использования подобных параметров состоит в том, что по сути мы можем вернуть из метода не одно значение, а несколько. Например:

```
void GetRectangleData(int width, int height, out int rectArea, out int rectPerimetr)
{
    rectArea = width * height;       // площадь прямоугольника - произведение ширины на высоту
    rectPerimetr = (width + height) * 2; // периметр прямоугольника - сумма длин всех сторон  
}
 
int area;
int perimetr;
 
GetRectangleData(10, 20, out area, out perimetr);
 
Console.WriteLine($"Площадь прямоугольника: {area}");       // 200
Console.WriteLine($"Периметр прямоугольника: {perimetr}");   // 60
```

Здесь у нас есть метод GetRectangleData, который получает ширину и высоту прямоугольника (параметры width и height). А два выходных параметра мы используем для подсчета площади и периметра прямоугольника.

При этом можно определять переменные, которые передаются out-параметрам в непосредственно при вызове метода. То есть мы можем сократить предыдущий пример следующим образом:

```
void GetRectangleData(int width, int height, out int rectArea, out int rectPerimetr)
{
    rectArea = width * height;  
    rectPerimetr = (width + height) * 2; 
}
 
GetRectangleData(10, 20, out int area, out int perimetr);
 
Console.WriteLine($"Площадь прямоугольника: {area}");       // 200
Console.WriteLine($"Периметр прямоугольника: {perimetr}");   // 60
```

При этом, если нам неизвестен тип значений, которые будут присвоены параметрам, то мы можем для их определения использовать оператор var:

```
GetRectangleData(10, 20, out var area, out var perimetr);
 
Console.WriteLine($"Площадь прямоугольника: {area}");       // 200
Console.WriteLine($"Периметр прямоугольника: {perimetr}");   // 60
```

### Массив в качестве параметра
Также этот способ передачи параметров надо отличать от передачи массива в качестве параметра:

```
void Sum(int[] numbers, int initialValue)
{
    int result = initialValue;
    foreach (var n in numbers)
    {
        result += n;
    }
    Console.WriteLine(result);
}
 
int[] nums = { 1, 2, 3, 4, 5};
Sum(nums, 10);
 
// Sum(1, 2, 3, 4);     // так нельзя - нам надо передать массив
```

Так как метод Sum принимает в качестве параметра массив без ключевого слова params, то при его вызове нам обязательно надо передать в качестве первого параметра массив. Кроме того, в отличие от метода с параметром params после параметра-массива могут располагаться другие параметры.
