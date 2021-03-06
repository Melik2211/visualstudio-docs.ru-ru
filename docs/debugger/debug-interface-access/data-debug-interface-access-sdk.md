---
title: Данные (SDK для доступа к интерфейсу отладки) | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- global variables [C++], as symbols
- local variables [C++], as symbols
- class members [C++], as symbols
- Data symbol
ms.assetid: 0f17e96a-2e06-42c9-a877-3e5e670ee0ef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94e1be7a1809c52683be045f71fcc681a6b270a8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745301"
---
# <a name="data-debug-interface-access-sdk"></a>Data (SDK для доступа к интерфейсу отладки)
Все переменные, такие как параметры, локальные переменные, глобальные переменные и члены класса, идентифицируются `SymTagData` символами. Константные значения (`LocIsConstant`) также определяются этим типом.

## <a name="properties"></a>Свойства
 В следующей таблице показаны свойства, которые являются допустимыми для этого типа символов.

|свойство;|Тип данных|Описание|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|Если поле, то одно из значений [перечисления CV_access_e](../../debugger/debug-interface-access/cv-access-e.md).|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Смещение части расположения; Дополнительные сведения см. в описании [перечисления локатионтипе](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Часть расположения; Дополнительные сведения см. в описании [перечисления локатионтипе](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_addressTaken](../../debugger/debug-interface-access/idiasymbol-get-addresstaken.md)|`BOOL`|`TRUE`, если на этот адрес данных ссылается другой символ.|
|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)|`DWORD`|Битовая позиция расположения; Дополнительные сведения см. в описании [перечисления локатионтипе](../../debugger/debug-interface-access/locationtype.md) (не поддерживается в пакете SDK для Dia версии 8.0).|
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Символ для класса, если это поле структуры, объединения или класса.|
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|Идентификатор родительского символа класса.|
|[IDiaSymbol::get_compilerGenerated](../../debugger/debug-interface-access/idiasymbol-get-compilergenerated.md)|`BOOL`|`TRUE`, если данные были созданы компилятором.|
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE`, если данные помечены как постоянные.|
|[IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)|`DWORD`|Одно из значений [перечисления Kind](../../debugger/debug-interface-access/datakind.md) .|
|[IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)|`BOOL`|`TRUE`, являются ли данные частью агрегированного типа данных (только в пакете SDK версии 8.0 и более поздних версиях DIA).|
|[IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)|`BOOL`|`TRUE`, если данные разбиваются на совокупность нескольких символов (только в пакете SDK версии 8.0 и более поздних версиях DIA).|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Длина битового массива; Дополнительные сведения см. в описании [перечисления локатионтипе](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Символ для включающего компилируемого объекта, функции или блока.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Идентификатор лексического родителя символа.|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Любой допустимый тип расположения; Дополнительные сведения см. в разделе [расположения символов](../../debugger/debug-interface-access/symbol-locations.md) .|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Имя переменной.|
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Смещение от содержимого регистров; Дополнительные сведения см. в описании [перечисления локатионтипе](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|`DWORD`|Регистрация обозначения расположения; Дополнительные сведения см. в описании [перечисления локатионтипе](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Относительное расположение данных внутри блока.|
|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|`DWORD`|Возвращает номер слота данных.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Идентификатор индекса символа.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Возвращает `SymTagData` (одно из значений [перечисления симтаженум](../../debugger/debug-interface-access/symtagenum.md) ).|
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|`DWORD`|Маркер метаданных, представляющий данные.|
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Символ для типа переменной.|
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ИДЕНТИФИКАТОР символа типа переменной.|
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE`, если данные не согласованы.|
|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|`VARIANT`|Значение константных данных.|
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Расположение данных в исполняемом файле.|
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE`, если данные помечены как временные.|

## <a name="see-also"></a>См. также
- [Перечисление CV_access_e](../../debugger/debug-interface-access/cv-access-e.md)
- [Перечисление DataKind](../../debugger/debug-interface-access/datakind.md)
- [Лексическая иерархия символьных типов](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [Перечисление LocationType](../../debugger/debug-interface-access/locationtype.md)
- [Местоположения символов](../../debugger/debug-interface-access/symbol-locations.md)