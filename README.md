# Написать программу генерации m - последовательностей 0 и 1, удовлетворяющих обоим требованиям :
1) число единиц должно быть нечётно(включая 0 единиц);
2) число нулей должно быть меньше числа единиц. (читать как число едениц больше числа нулей)

## Немного сути:
Как сказано в методичке:
Генерация m-последовательностей 0 и 1.
Для решения можно использовать алгоритм генерации размещений с повторениями, где xi = 0 и yi = 1.
Однако если в условии задано ограничение на количество 0 или 1, то при таком подходе заведомо будут генерироваться лишние последовательности.
В этом случае лучше использовать алгоритм генерации сочетаний без повторений для номеров мест, на которые будут расставляться 0 или 1. 
При получении каждой сгенерированной комбинации номеров мест для 1 (0) в массиве С, нужно обнулить (заполнить 1) массив А требуемых m-последовательностей, 
а затем расставить в нём на места из массива С единицы (нули).

# Что я делаю:
Есть функция Sochet_BP, которая будет генерировать места на которые расставляем 1.
Они представляют собой массив с номерами, на которые расставляем 1.
После генерации очередного такого массива, вызывается функция CreateSequence,
которая создает конечную последовательность 0 и 1 и вызывает функцию для печати ее на экран.
Последовательноть создается очень просто:
На вход был подан массив с позициями для 1
Просто создаем массив длиной m (длина последовательности) и на места,
указаные во входном массиве ставим 1
Потом просто выводим этот массив на экран
Чтобы последовательноть подходила под условия:

1) число единиц должно быть нечётно(включая 0 единиц);
2) число нулей должно быть меньше числа единиц. (читать как число единиц больше числа нулей)

Будем делать следующее в функции main:
m - длина последовательности
В цикле for:
n - кол-во едениц в конечной последовательности
Чтобы оно удовлетворяло условию 2, нужно чтобы число единиц (то есть переменная n) была больше половины всей последовательности
Поэтому цикл начинается с n = m / 2 + 1 и идет до m
Чтобы оно удовлетворяло условию 1, перед вызовом функции Sochet_BP проверяем условие n % 2 != 0, которое выполнится,
если чило n - нечетное (то, что нам и нужно)
