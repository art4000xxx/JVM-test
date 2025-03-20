# Анализ работы кода JvmComprehension.java

## Метод main

### Строка 4: `int i = 1;`
*   В стеке метода `main` выделяется место для локальной переменной `i` типа `int`.
*   Значение `1` сохраняется в стеке.
*   Сборщик мусора не задействован.

### Строка 5: `Object o = new Object();`
*   В хипе создается новый объект типа `Object`.
*   В стеке метода `main` выделяется место для локальной переменной `o` типа `Object`.
*   В переменной `o` сохраняется ссылка на созданный объект в хипе.
*   Объект становится кандидатом на сборку мусора, когда на него больше не будет ссылок.

### Строка 6: `Integer ii = 2;`
*   В хипе создается новый объект типа `Integer` (автоупаковка).
*   В стеке метода `main` выделяется место для локальной переменной `ii` типа `Integer`.
*   В переменной `ii` сохраняется ссылка на созданный объект в хипе.
*   Объект становится кандидатом на сборку мусора, когда на него больше не будет ссылок.

### Строка 7: `printAll(o, i, ii);`
*   Создается новый фрейм в стеке для метода `printAll`.
*   Параметр `o` передается по ссылке (копируется ссылка на объект в хипе).
*   Параметр `i` передается по значению (копируется значение `1`).
*   Параметр `ii` передается по ссылке (копируется ссылка на объект в хипе).

## Метод printAll

### Строка 11: `Integer uselessVar = 700;`
*   В хипе создается новый объект типа `Integer` (автоупаковка).
*   В стеке метода `printAll` выделяется место для локальной переменной `uselessVar` типа `Integer`.
*   В переменной `uselessVar` сохраняется ссылка на созданный объект в хипе.
*   Объект становится кандидатом на сборку мусора, когда на него больше не будет ссылок.

### Строка 12: `System.out.println(o.toString() + i + ii);`
*   Вызывается метод `o.toString()`, который возвращает строковое представление объекта `Object`.
*   Происходит конкатенация строк.
*   Результат передается в метод `System.out.println()`, который выводит строку на консоль.

## После завершения программы

*   Локальные переменные `i`, `o`, `ii` (в методе `main`) и `uselessVar` (в методе `printAll`) уничтожаются.
*   Объекты `Object` и `Integer`, созданные в хипе, становятся кандидатами на сборку мусора.
