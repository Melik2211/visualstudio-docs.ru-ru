---
title: 'Иактивескриптгарбажеколлектор:: Коллектгарбаже | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 75f77c49-2190-4d49-a3e0-9dcf847c502b
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0539ed2cb3540cf33ceaaa15827c3ca08c156698
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573583"
---
# <a name="iactivescriptgarbagecollectorcollectgarbage"></a>IActiveScriptGarbageCollector::CollectGarbage
Сервер активных скриптов вызывает этот метод для запуска сборки мусора.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT CollectGarbage(        SCRIPTGCTYPE scriptgctype    );  
```  
  
#### <a name="parameters"></a>Параметры  
 `scriptgctype`  
 окне [Перечисление скриптгктипе](../../winscript/reference/scriptgctype-enumeration.md) , которое указывает, выполняется ли обычная или исчерпывающая сборка мусора.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение HRESULT.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptGarbageCollector Interface](../../winscript/reference/iactivescriptgarbagecollector-interface.md)