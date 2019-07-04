---
title: Список тэгов
---

# Список тэгов

| Тэг 				| Параметры 			| Область 	   | Описание 
|-------------------|-----------------------|--------------|-------------------------------------------------------------------------------
| Range             | source, horizontal	| range 	   | С помощью параметра `source` можно указать источник данных для области, отличный от имени области. Применяя параметр `horizontal` вы можете указать, что область должна строиться по горизонтали.
| Sort              | asc, desc             | rangeCol     | Сортирует область по столбцу, для которого он указан. Параметры `Desc` и `Asc` (Asc – по умолчанию) указывают порядок сортировки. Возможна одновременная сортировка по нескольким столбцам. Сортировка происходит справа налево, то есть сначала сортируется самый правый столбец, затем следующий слева и т.д. Тэг `<sort>` работает как для отдельно расположенных областей, так и для вложенных (нижнего уровня вложенности).
| Asc               |                       | rangeCol     | То же, что и `<sort desc>`
| Desc              |                       | rangeCol     | То же, что и `<sort asc>`
| Group             | Collapse<br>Desc<br>Asc<br>MergeLabels=[Merge1&#124; Merge2&#124; Merge3]<br>PlaceToColumn=n<br>WithHeader<br>Disablesubtotals<br>DisableOutline<br>PageBreaks| rangeCol     | Создает промежуточные итоги по столбцам, в которых указаны тэги итогов (`<sum>` и т.д.), группируя их по столбцу, для которого он указан. Предварительно область сортируется по всем столбцам, для которых указаны тэги Group, Sort, Desc и Asc. Порядок сортировки для тэга `<group>` указывается дополнительным параметром - `Desc` или `Asc` (Asc по умолчанию). Параметр `Collapse` вызывает сворачивание промежуточных итогов до уровня, на котором расположена тэг `<group>` с этим параметром. Работа тэга полностью соответствует методу Subtotal объекта Range. Так же, в случае, если тэг `<group>` указан для нескольких столбцов, промежуточные итоги группируются по всем этим столбцам. Группировка происходит справа налево, то есть сначала итоги группируются по крайнему справа столбцу, для которого указан тэг `<group>`, затем по столбцу с опцией `<group>` слева от него и т.д. Для форматирования строк промежуточных итогов используется форматирование служебной строки области. После создания промежуточных итогов служебная строка удаляется из области. Тэг может использоваться без итоговых функций. В этом случае, данные группируются без промежуточных итогов. Для форматирования строк промежуточных итогов и заголовков групп используется форматирование служебной строки области. <br>Параметр `MergeLabels` вызывает объединение ячеек группы в группируемом столбце. <br>Параметр `PlaceToColumn` позволяет указать столбец, в который будет помещен заголовок группы. <br>Параметр `DisableSubtotals` позволяет отключить создание промежуточных итогов для столбца. <br>Параметр `DisableOutline` выключает создание Outline view для группируемого столбца. <br>Параметр `PageBreaks` позволяет поместить каждую группу на отдельную страницу. <br>Параметр `WithHeader` позволяет создавать заголовок группы при использовании промежуточных итогов. В случае если обнаружен тэг `<SummaryAbove>` (см. ниже), промежуточные итоги размещает над данными.<br>Подробнее в разделе [Группировка](Grouping)
| SummaryAbove      | 						| range 	   | Вспомогательный тэг для тэга `<group>`. `<SummaryAbove>` используется для того, чтобы разместить итоги по группам над данными. Подробнее в разделе [Группировка](Grouping)
| DisableGrandTotal | 						| range 	   | Запрещает создание всех общих итогов при использовании группировки области с промежуточными итогами. Подробнее в разделе [Группировка](Grouping)
| Pivot             | Name<br>Dst<br>RowGrand<br>ColumnGrand<br>NoPreserveFormatting<br>CaptionNoFormatting<br>MergeLabels<br>ShowButtons<br>TreeLayout<br>AutofitColumns<br>NoSort                  |              | Вызывает создание сводной таблицы по области, для которой она указана. Структура сводной таблицы определяется согласно опциям полей сводной таблицы (описаны ниже). Область, по которой строится сводная таблица, должна быть списком данных Excel. Над областью обязательно должен присутствовать заголовок таблицы.<br> Тэг `<pivot>` требует обязательного указания параметра `Name`, определяющего имя создаваемой сводной таблицы. Имя должно быть допустимым в Excel. <br>Параметр `Dst` позволяет указать точное местоположение левого верхнего угла сводной таблицы (включая поля страниц). В качестве значения этого параметра могут быть указаны формулы ссылки на ячейку в стилях A1 или R1C1. Допускается указание в этой формуле имени листа, на котором необходимо поместить сводную таблицу. Например, `Dst=Лист1!D8`. В случае если параметр `Dst` не указан, для каждой сводной таблицы отчета создается новый лист с именем этой таблицы. <br>Параметры `RowGrand` и `ColumnGrand` включают соответствующие свойства сводной таблицы, позволяя получить общие итоги по строкам и, соответственно, столбцам таблицы. <br>`MergeLabels` включает соответствующее свойство сводной таблицы, вызывая объединение ячеек в области строк и столбцов. <br>По умолчанию все форматирование исходной области переносится в соответствующие области заголовков и данных. В случае указания параметра `NoPreserveFormatting`, форматирование не переносится. <br>Параметр `ShowButtons` позволяет показать кнопку expand/collapse. <br>`TreeLayout` - устанавливает режим сводной таблицы в виде дерева. <br>`AutofitColumns` - включает автоподбор ширины колонок сводной таблицы. <br>`NoSort` - запрещает автоматическую сортировку сводной таблицы. <br><br>Для описания структуры сводной таблицы используются тэги полей сводной таблицы (Page, Row, Column, Data), определяющие области сводной таблицы, в которые эти поля помещаются. В сочетании с ними используются итоговые тэги, описывающие типы итогов, которые необходимо получить по этим полям. Столбцы, для которых не указаны тэги полей сводной таблицы, включаются в сводную таблицу в качестве скрытых. В процессе работы с готовым отчетом с помощью стандартных средств Excel возможно изменение структуры сводной таблицы конечным пользователем. Структура сводной таблицы должна учитывать ограничения на сводные таблицы, которые описаны в документации к конкретной версии Excel. Подробное описание методики расчета этих ограничений можно найти в MSDN. <br><br> Подробнее в разделе [Сводные таблицы](Pivot-tables)
| Page              |                       | rangeCol     | Этот тэг размещает столбец, для которого он указан, в область полей страниц сводной таблицы. В качестве метки поля используется значение ячейки из заголовка таблицы над областью-источником
| Row               |                       | rangeCol     | Этот тэг размещает столбец, для которого он указан, в область строк сводной таблицы. В качестве метки поля используется значение ячейки из заголовка таблицы над областью-источником. Excel автоматически группирует элементы внутреннего поля для каждого элемента внешнего поля строк и, если необходимо, создает промежуточные итоги. Тип промежуточных итогов определяется дополнительным указанием тэга итогов для столбца с тэгом `<row>`. Например, указание тэгов `<row><sum><count>` создаст сумму и количество в промежуточных итогах по полю сводной таблицы, источником для которого служит столбец с этими тэгами.
| Column, Col       |                       | rangeCol     | Этот тэг размещает столбец, для которого он указан, в область столбцов сводной таблицы. В качестве метки поля используется значение ячейки из заголовка таблицы над областью-источником. По полям столбцов можно получать один или несколько промежуточных итогов. Их тип определяется дополнительным указанием тэга итогов для столбца с тэгом `<col>`. Например, указание опций `<col><sum><count>` создаст сумму и количество в промежуточных итогах по полю сводной таблицы, источником для которого служит столбец с этими тэгами.
| Data              |                       | rangeCol     | Этот тэг размещает столбец, для которого он указан, в область данных сводной таблицы. В качестве метки поля используется значение ячейки из заголовка таблицы над областью-источником. К полям данных по умолчанию применяется функция `sum`. Чтобы переключиться на любую другую итоговую функцию в поле данных, совместно с тэгом `<data>` допустимо использование тэгов итогов.
| SUM<br>AVG<br>AVERAGE<br>COUNT<br>COUNTNUMS<br>MAX<br>MIN<br>PRODUCT<br>STDEV<br>STDEVP<br>VAR<br>VARP<br> | over="expression"<br>over="expression"<br>over="expression"<br>over="expression"<br>over="expression"<br>over="expression"<br>over="expression"<br>over="expression"<br>over="expression"<br>over="expression"<br>over="expression"<br>over="expression"<br> | rangeCol | Это тэги итогов. Указание его для столбца вызывает подведение итога по столбцу. Итог вычисляется соответствующей функцией Excel. Итоги размещаются в служебном столбце области. По столбцу можно получить только один вид итога (например, сумму или только среднее). В случае если указано несколько итоговых опций, вычисляется только последний указанный итог. Параметр `over` позволяет делать вычисления используя мощь .NET и LINQ. В выражежениях применяется синтаксис выражений C#. С помощью переменной `items` вы можете получить доступ к списку элементов таблицы. 
| OnlyValues        |                       | worksheet<br>range<br>rangeCol<br>cell | Заменяет все формулы на листе, в области, столбце области или в ячейке, где он указана, на значения этих формул.
| AutoFilter        |                       | range        | Включает автофильтр в области, для которой он указана.
| Protected         | Password="password"   | workbook<br>worksheetrange<br>cell<br>rangeCol<br> | В случае если указан для отчета, вызывает защиту всех листов и защиту самой книги. В случае если указан для листа, защищает этот лист. Аналагично применяется к области, определённой колонке области и к отдельной ячейке. Параметр `Password` является необязательным. Если пароль не задан, он будет сгенерирован случайным образом.
| ColsFit			|                       | workbook<br>worksheet<br>worksheetCol<br>range<br>rangeCol<br>cell | Вызывает автоматическое выравнивание ширины столбцов по значению в ячейках столбцов всего отчета (если указан для отчета), листа (если указан для листа), колонке всего листа (если указан в первой строке листа), области (если указан для области), колонке области (если указан в строке опций) либо для одной ячейки. В случае если указан для листа и для области на этом листе, вызывается только для листа. Тот же принцип от большего к меньшему применяется и для остальных случаев.
| RowsFit           |                       | workbook<br>worksheet<br>worksheetRow<br>range<br>rangeCol<br>cell | Вызывает автоматическое выравнивание высоты строк по значению в ячейках строк всего отчета (если указан для отчета), листа (если указан для листа), колонке всего листа (если указан в первой строке листа), области (если указан для области), колонке области (если указан в строке опций) либо для одной ячейки. В случае если указан для листа и для области на этом листе, вызывается только для листа. Тот же принцип от большего к меньшему применяется и для остальных случаев.
| Hidden, Hide      |                       | worksheet    | Скрывает лист, для которого он указана. В случае отладки отчета, производит «мягкое» скрытие, позволяющее сделать лист видимым.
| Delete            |                       | worksheet<br>worksheetRow<br>worksheetCol<br>rangeCol | Удаляет лист, строку/колонку листа либо колонку области, в зависимости от того, где тэг расположен.
| PageOptions       | Wide=`<int>`<br>Tall=`<int>`<br>Landscape | workbook<br>worksheet | Задаёт параметры страницы при печати, настраивая ширину листа параметром `Wide`, высоту листа параметром `Tall` и ориентацию листа параметром `Landscape`