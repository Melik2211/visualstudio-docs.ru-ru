---
title: Задача XmlPoke | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPoke task [MSBuild]
- MSBuild, XmlPoke task
ms.assetid: 6ba1953c-be3b-4df8-8561-e133408f8270
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1ba57c1578bd69d71ed0abdac45907d937b89ecb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68198972"
---
# <a name="xmlpoke-task"></a>Задача XmlPoke
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Задает в XML-файле значения, указанные в запросе XPath.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `XmlPoke` .  
  
|Параметр|ОПИСАНИЕ|  
|---------------|-----------------|  
|`Namespaces`|Необязательный параметр `String` .<br /><br /> Задает пространства имен для префиксов запроса XPath.|  
|`Query`|Необязательный параметр `String` .<br /><br /> Указывает запрос XPath.|  
|`Value`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Задает выходной файл.|  
|`XmlInputPath`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Указывает входные данные XML в виде пути к файлу.|  
  
## <a name="remarks"></a>Примечания  
 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
