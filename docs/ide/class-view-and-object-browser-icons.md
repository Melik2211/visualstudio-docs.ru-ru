---
title: Значки представления классов и обозревателя объектов
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- icons, in Object Browser
- signal icons
- Class View tool, symbols
- graphic symbols
- IntelliSense, icons
- icons, IntelliSense
- symbols, Object Browser icons
- Object Browser, icons in Class View
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6589d40d8f897eb8df7f108f53973af268d1edc9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588399"
---
# <a name="class-view-and-object-browser-icons"></a>Значки представления классов и обозревателя объектов

**Представление классов** и **обозреватель объектов** отображают значки, представляющие сущности кода, например пространства имен, классы, функции и переменные. Эти значки описаны в приведенной ниже таблице.

|Значок|Описание|Значок|Описание|
|----------|-----------------|----------|-----------------|
|![Символ пространства имен](../ide/media/vxnamespace_icon.gif)|Пространство имен|![Символ объявления](../ide/media/vxmethod_icon.gif)|Метод или функция|
|![Значок класса](../ide/media/vxclass_icon.gif)|Класс|![Символ оператора](../ide/media/vxoperator_icon.gif)|Оператор|
|![Символ интерфейса без описания операций](../ide/media/vxinterface_icon.gif)|Интерфейс|![Символ свойства](../ide/media/vxproperty_icon.gif)|Свойство.|
|![Символ структуры](../ide/media/vxstruct_icon.gif)|structure|![Значок поля](../ide/media/vxfield_icon.gif)|Поле или переменная|
|![Символ объединения](../ide/media/vxunion_icon.gif)|Объединение|![Символ события](../ide/media/vxevent_icon.gif)|событие|
|![Символ перечисления](../ide/media/vxenum_icon.gif)|Enum|![Значок константы](../ide/media/vxconstant_icon.gif)|Константа|
|![Символ определения типа](../ide/media/vxtypedef_icon.gif)|TypeDef|![Символ элемента перечисления](../ide/media/vxenumitem_icon.gif)|Элемент перечисления|
|![Символ модуля Visual Studio](../ide/media/vxmodule_icon.gif)|Module|![Символ элемента сопоставления](../ide/media/vxmapitem_icon.gif)|Элемент сопоставления|
|![Символ метода расширения](../ide/media/extensionmethod.gif)|Метод расширения|![Символ объявления](../ide/media/vxmethod_icon.gif)|Внешнее объявление|
|![Символ делегата](../ide/media/vxdelegate_icon.gif)|делегат|![Значок ошибки представления классов и обозревателя объектов](../ide/media/erroricon.gif)|Ошибка|
|![Символ исключения](../ide/media/vxexception_icon.gif)|Исключение|![Символ шаблона](../ide/media/vxtemplate_icon.gif)|Шаблон|
|![Символ сопоставления](../ide/media/vxmap_icon.gif)|Карта|![Символ восклицательного знака при ошибке](../ide/media/vxerror_icon.gif)|Неизвестно|
|![Символ пересылки типов](../ide/media/ob_type_forward.gif)|Перенаправление типов|||

## <a name="signal-icons"></a>Сигнальные значки

Приведенные ниже сигнальные значки применяются ко всем перечисленным выше значкам и указывают их доступность.

|Значок|Описание|
|----------|-----------------|
|\<Без сигнального значка>|Общедоступный. Доступен из любой части этого компонента, а также из любого компонента, который на него ссылается.|
|![Символ Protected](../ide/media/vxsignal_icon_key.gif)|Защищенный. Доступен из содержащего класса или типа, а также из производных от них классов и типов.|
|![Символ Private](../ide/media/vxsignal_icon_lock.gif)|Закрытый. Доступен только в содержащем классе или типе.|
|![Символ Sealed](../ide/media/vxsignal_icon_envelope.gif)|Запечатанный.|
|![Символ Friend/Internal](../ide/media/vxsignal_icon_diamond.gif)|Дружественный/внутренний. Доступен только из проекта.|
|![Значок стрелки](../ide/media/vxsignal_icon_arrow.gif)|Ярлык. Ярлык объекта.|

> [!NOTE]
> Если ваш проект включен в базу данных управления версиями, могут отображаться дополнительные сигнальные значки, указывающие состояние управления версиями, например, возвращено или извлечено.

## <a name="see-also"></a>См. также

- [Просмотр структуры кода](../ide/viewing-the-structure-of-code.md)
