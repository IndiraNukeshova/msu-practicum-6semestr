### A ФАЛ
Реализуйте класс BooleanFunction, представляющей ФАЛ в виде таблицы истинности, позволяющий вычислять значение на двоичных наборах, а также допускающий операции из базиса Жегалкина (XOR, AND).

Конструктор принимает на вход таблицу истинности — список из значений 0 и 1. Чтобы удобно выполнять проверку типов, определите заранее тип BooleanVector = list[Literal[0, 1]]. Если длина списка, переданного в конструктор, не является степенью двойки, породите исключение ValueError с текстом ошибки "Truth table length is not a power of two".

У класса должен быть метод __str__, возвращающий строковое представление функции в формате "f(x1, x2) = (0, 0, 0, 1)". Количество переменных определяется исходя из длины таблицы истинности.

У класса должен быть метод __call__, принимающий один аргумент — список значений переменых x1, x2, ..., и возвращающий значение функции на данном наборе. Если длина списка не равна арности функции, выкиньте исключение ValueError с текстом ошибки "Arity mismatch".

Также перегрузите операторы + и * так, чтобы они реализовывали над двумя ФАЛ операции XOR и AND соответственно. Данные операции возвращают объекты класса BooleanFunction. Если арности функций не совпадают, вызовите ValueError("Arity mismatch").

Данная задача тестируется путём выполнения кода, записанного во входном файле теста. Для работы этих тестов в функции main вызовите exec(sys.stdin.read()).

### B Симулятор COVID-19
Реализуйте класс-итератор CovidSimulator, симулирующий протекание болезни COVID-19. В конструктор класса передаётся два числа: продолжительность заболевания в днях и изменение температуры в градусах (число с плавающей точкой с точностью до одного знака после запятой).

Симулятор должен работать следующим образом. В первый и последний день заболевания итератор возвращает температуру 36.6. В начале периода температура повышается каждый день на указанное количество градусов, а затем опускается до нормальной температуры. При этом температура не может превысить значение 40 градусов. Таким образом, при некоторых значениях продолжительности заболевания и изменения температуры сначала происходит увеличение температуры тела, затем она несколько дней держится, а потом опускается до нормального значения.

Кроме возвращаемой температуры класс CovidSimulator должен содержать поле current_day — текущий день болезни.

Для большего понимания, как должен работать класс CovidSimulator, смотрите примеры тестов ниже.

Данная задача тестируется путём выполнения кода, записанного во входном файле теста. Для работы этих тестов в функции main вызовите exec(sys.stdin.read()).
### C Найди Ложкина
Реализуйте метакласс FindLozhkin, который находит в создаваемом классе атрибут lozhkin и производит с ним некоторые манипуляции.

Если атрибут lozhkin не найден, вызовите исключение TypeError("Очень плохой класс, в нём нет Ложкина").

Если атрибут lozhkin является методом класса, примените к нему декоратор, печатающий перед выполнением данного метода строку "Так сказать".

Если атрибут lozhkin является целым числом, то оно не должно быть меньше 10^9. Если оно всё-таки меньше, присвойте этому атрибуту значение 10^9.

Если атрибут lozhkin является строкой, добавьте к ней префикс "Так сказать, ".

Во всех остальных случаях не трогайте Ложкина.

Данная задача тестируется путём выполнения кода, записанного во входном файле теста. Для работы этих тестов в функции main вызовите exec(sys.stdin.read()).

### D Успеваемость
Учебная часть прислала вам данные со средними баллами студентов и попросила быстро посчитать средние баллы по кафедрам. Разберитесь с форматом входных данных и выведите средние баллы по кафедрам в алфавитном порядке (но сами названия кафедр выводить не нужно, только баллы).

Требования к решению:
1. Заведите 2 датакласса, соответствующих двум типам записей во входных данных. При чтении данных преобразуйте их в датаклассы и сохраняйте в списки.
2. Создайте класс Stats для расчёта выборочного среднего. В этом классе должен быть конструктор без параметров, метод добавления числа add, принимающий значение типа float, а также property average, возвращающий среднее выборочное значение.
3. В качестве словаря, ключом которого является название кафедры, а значением — Stats, используйте defaultdict. Этот словарь вам несомненно понадобится, когда вы будете итерироваться по оценкам студентов и распределять их по кафедрам.
4. Не забывайте про аннотации типов!

Замечание: конечно, для нахождения средних баллов можно было написать код попроще, но основная цель этой задачи — попрактиковаться в ООП.

### E ШуплецовКредитБанк
Вы проходите собеседование в финансовую организацию ПАО "ШуплецовКредитБанк" на должность стажёра-разработчика на языке Python с окладом 50 000 ₽ в месяц. На техническом интервью вас попросили решить следующую задачу.

Напишите класс банковского вклада BankDeposit, обладающий следующими свойствами:
1. В конструктор передаётся начальное количество денежных средств и ставка по вкладу. Оба этих числа являются целыми.
2. Текущий баланс можно получить через атрибут "balance". Атрибут должен быть доступен только для чтения, присвоить значение этому атрибуту нельзя.
3. Ставку по вкладу можно получить через атрибут "deposit_rate". Но, в отличие от баланса, этот атрибут должен быть изменяемым. Тем не менее, при попытке привоить ему отрицательное значение должно быть выброшено исключение ValueError с текстом ошибки "Deposit rate cannot be less than zero".
4. В классе должна быть функция capitalization, начисляющая проценты на вклад. Начисленные проценты — это всегда целое число, дробная часть округляется вниз.

Данная задача тестируется путём выполнения кода, записанного во входном файле теста. Для работы этих тестов в функции main вызовите exec(sys.stdin.read()).
Подсказка: в задаче следует использовать декоратор @property, иначе вы не получите должность в ПАО "ШуплецовКредитБанк".
