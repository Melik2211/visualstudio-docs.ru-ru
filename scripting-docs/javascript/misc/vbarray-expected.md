---
title: Требуется VBArray | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5013
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 467a6ec6ca45f2ea0411e0266163ca23a9e3d594
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572504"
---
# <a name="vbarray-expected"></a>Требуется VBArray
Вы указали объект, который не был Visual Basic safeArray, если он ожидался.  
  
```js
new VBArray(safeArray);  
```  
  
 Объекты VBArray доступны только для чтения и не могут быть созданы напрямую. Аргумент safeArray является значением VBArray и должен получить значение VBArray перед передачей в конструктор `VBArray`. Это можно сделать только путем получения значения из существующего объекта ActiveX или другого объекта.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Убедитесь, что в конструктор **VBArray** передаются только объекты **VBArray** .  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [объекта VBArray](../../javascript/reference/vbarray-object-javascript.md)  
 [Использование массивов](../../javascript/advanced/using-arrays-javascript.md)