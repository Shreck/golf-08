# Perl Golf

_Perl Golf --- это соревнование по поиску Perl-кода наименьшего размера (меньше
всего символов), который решает поставленную задачу._

По мотивам проведённого на YAPC::Eurore 2013 соревнования по Perl Golf,
устроенного компанией Reg.ru, которое привлекло множество людей к решению
головоломки, возникла идея публиковать задания в журнале, собирать решения в
течение месяца и делать в последующем номере обзор решений с объявлением
победителя соревнования.

## Цифры

Наверняка многие из вас в школьные годы играли в игру под названием «Цифры» (или
«Числа»). Суть игры такова: на тетрадный лист выписываются цифры, каждая цифра
записывается в отдельную клеточку, слева направо, по девять цифр в ряд.
Начальная последовательность зафиксирована:

    123456789
    111213141
    516171819

Задача состоит в том, чтобы зачёркивать две соседние цифры (по горизонтали или
по вертикали), которые имеют одинаковое значение или их сумма равна десяти.
Соседними считаются те цифры, между которыми нет других цифр или все
промежуточные цифры зачёркнуты. Кроме того считается, что последняя цифра ряда,
является соседней с первой цифрой последующего ряда (т.е. следующий ряд является
продолжением предыдущего по горизонтали).

Пример удаления цифр:

    123456789   _23456789   _2345678_
    111213141 → _11213141 → __1213141
    516171819   516171819   516171819

Сначала удаляются две цифры `1`, которые расположены вертикально, на следующем
шаге удаляются `9` и `1`, которые являются соседними, поскольку между ними нет
других цифр (промежуточная `1` была удалена на предыдущем шаге).

Количество вариантов для удаления может быть несколько, и в этом и заключается
интерес игры, подобрать такие сочетания, чтобы удалить максимальное число цифр.

Как только все доступные для удаления цифры были вычеркнуты, ряд цифр, сразу
после последней записанной позиции, дополняется последовательностью, состоящей
из оставшихся на поле цифр. Например:

    1234567__   1234567__
    ____1314_ → ____1314_
    51617181_   51617181_
                123456713
                145161718
                1

После чего процесс повторяется до бесконечности. Задача играющего --- попытаться
удалить с поля как можно больше цифр.

## Задание

Задание для создаваемой программы:

- Получить на `STDIN` последовательность из цифр по девять символов в ряд, ряды
  цифр разделены символом переноса строки `\n`. Позиция удалённого символа
  обозначается пробелом.
- Программа должна выдать на `STDOUT` последовательность, в которой удалены все
  возможные сочетания цифр по правилам игры (эти цифры заменяются символом
  пробела). Вывод идёт также по девять символов в ряд с символом переноса строки
  для разделения рядов.
- Если после удаления цифр один или несколько рядов оказались пустыми, то эти
  ряды должны быть удалены из вывода.

Понятно, что для одних и тех же входных данных может существовать несколько
вариантов вывода. Но решением будет признаваться любое корректное решение, в
котором не осталось возможных комбинаций для удаления и не пропали цифры,
которые не могли быть удалены согласно правилам.

Как обычно в Perl Golf, в длину решения не входит первая строка, в которой
указан _шебанг_ для вызова perl и переданных ему параметров:

    #!/usr/bin/perl -n

Нельзя использовать какие-либо модули и вызывать внешние программы.

Чтобы убедиться, что задача имеет решение, я написал свой вариант, который
кажется работает. Указывать его размер не буду, чтобы ~~не позориться~~ была
интрига.

Для участия в соревновании сделайте форк репозитория
[golf-08](https://github.com/PragmaticPerl/golf-08), создайте в директории
`script` файл `your_github_login.pl` с вашим вариантом решения. Проверьте, что
ваш вариант проходит тесты (с помощью команды `prove`) и сделайте pull request в
основной репозиторий.

Дерзайте! Победителя ждёт, как обычно, уважение и почёт.

■ _Владимир Леттиев_
