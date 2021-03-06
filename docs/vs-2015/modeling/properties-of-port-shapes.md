---
title: Свойства фигур порта | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.port
helpviewer_keywords:
- Domain-Specific Language, port shape
ms.assetid: 9d69c4c1-4f72-4876-96b6-9b846e0495a4
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 906a35f1b564c4e3794d1000f03cb32cda003ca2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671364"
---
# <a name="properties-of-port-shapes"></a>Свойства фигур портов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Фигуры портов можно использовать для представления доменных классов в созданном конструкторе.

 Дополнительные сведения см. [в разделе Определение доменного языка](../modeling/how-to-define-a-domain-specific-language.md). Дополнительные сведения об использовании этих свойств см. [в разделе Настройка и расширение предметно-](../modeling/customizing-and-extending-a-domain-specific-language.md)ориентированного языка.

 Формы портов имеют свойства, перечисленные в следующей таблице.

|свойство;|Описание|Значение по умолчанию|
|--------------|-----------------|-------------|
|Цвет заливки|Цвет заливки этой фигуры.|Белый|
|Режим градиента заливки|Режим градиента заливки этой фигуры.|Горизонтально|
|Объект|Геометрия этой фигуры (прямоугольник, Скругленный прямоугольник, эллипс или окружность).|Прямоугольник|
|Имеет точки соединения по умолчанию|Если `True`, фигура будет использовать верхнюю, нижнюю, левую и правую точки соединения в созданном конструкторе.|False|
|Цвет контура|Цвет контура этой фигуры.|Черный|
|Стиль штриха в контуре|Стиль штриха контура этой фигуры (сплошная, Штрихпунктирная, точка, Дашдот, Дашдотдот или пользовательская).|Сплошная|
|Толщина контура|Толщина контура этой фигуры.|0,03125|
|Цвет текста|Цвет, используемый для декораторов текста, связанных с этой фигурой.|Черный|
|Модификатор доступа|Уровень доступа класса (`public` или `internal`).|Public|
|Настраиваемые атрибуты|Используется для добавления атрибутов в класс исходного кода, созданного из этой фигуры.|\<none>|
|Создает двойное производное|Если `True`, будет сформирован как базовый класс, так и разделяемый класс (для поддержки настройки с помощью переопределений). Дополнительные сведения см. [в разделе Переопределение и расширение созданных классов](../modeling/overriding-and-extending-the-generated-classes.md) .|False|
|Имеет настраиваемый конструктор|Если `True`, в исходном коде будет предоставлен пользовательский конструктор. Дополнительные сведения см. [в разделе Переопределение и расширение созданных классов](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Модификатор наследования|Описывает тип наследования класса исходного кода, созданного из порта (`none`, `abstract` или `sealed`).|Нет|
|Базовый порт|Базовый класс этой фигуры.|(нет)|
|Название|Имя этой фигуры.|Текущее имя|
|Пространство имен|Пространство имен, связанное с этой фигурой.|Текущее пространство имен|
|Тип всплывающей подсказки|Как определена подсказка (фиксированная, переменная или нет). Если параметр является фиксированным, то в качестве подсказки используется значение свойства `Fixed Tooltip Text`. Если переменная, то подсказка определяется в пользовательском коде.|Нет|
|Примечания|Неформальные примечания, связанные с этой фигурой.|\<none>|
|Начальная высота|Начальная высота этой фигуры в дюймах.|1|
|Начальная ширина|Начальная ширина этой фигуры в дюймах.|1,5|
|Предоставленный цвет заливки как свойство<br /><br /> Предоставленный режим градиента заливки<br /><br /> Раскрытие цвета контура как свойства<br /><br /> Раскрытие стиля штриха в качестве свойства<br /><br /> Доступная толщина контура в качестве свойства<br /><br /> Отображение цвета текста|Если `True`, пользователь может задать указанное свойство фигуры. Чтобы установить это, щелкните правой кнопкой мыши определение фигуры и выберите пункт **добавить предоставленный**.|False|
|Описание|Используется для документирования созданного конструктора.|\<none>|
|Отображаемое имя|Имя, которое будет отображаться в созданном конструкторе для этой фигуры.|\<none>|
|Исправленный текст подсказки для инструментов|Текст, используемый для фиксированной подсказки.|\<none>|
|Ключевое слово Help|Ключевое слово, используемое для индексации справки F1 для этой фигуры.|\<none>|

## <a name="see-also"></a>См. также раздел
 [Глоссарий средств предметно-ориентированных языков](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
