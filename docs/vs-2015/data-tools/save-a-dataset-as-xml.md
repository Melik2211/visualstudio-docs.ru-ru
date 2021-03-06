---
title: Сохранение набора данных в формате XML | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e64c3c17934e5cdc5d6ca1f510c7164b86a77c1a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652865"
---
# <a name="save-a-dataset-as-xml"></a>Сохранение набора данных в формате XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Доступ к XML-данным в наборе данных можно получить, вызвав доступные методы XML в наборе данных. Чтобы сохранить данные в формате XML, можно вызвать либо метод <xref:System.Data.DataSet.GetXml%2A>, либо метод <xref:System.Data.DataSet.WriteXml%2A> <xref:System.Data.DataSet>.

 Вызов метода <xref:System.Data.DataSet.GetXml%2A> возвращает строку, содержащую данные из всех таблиц данных в наборе данных, отформатированном как XML.

 При вызове метода <xref:System.Data.DataSet.WriteXml%2A> данные в формате XML отправляются в указанный файл.

### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Сохранение данных в наборе данных в виде XML-файла в переменную

- Метод <xref:System.Data.DataSet.GetXml%2A> возвращает <xref:System.String>. Это означает, что вы объявили переменную типа <xref:System.String> и назначите ей результаты метода <xref:System.Data.DataSet.GetXml%2A>.

     [!code-csharp[VbRaddataSaving#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#12)]
     [!code-vb[VbRaddataSaving#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#12)]

### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Сохранение данных в наборе данных в виде XML-файла

- Метод <xref:System.Data.DataSet.WriteXml%2A> имеет несколько перегрузок. В следующем примере кода показано, как сохранить данные в файл. Объявите переменную и присвойте ей допустимый путь для сохранения файла.

     [!code-csharp[VbRaddataSaving#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#13)]
     [!code-vb[VbRaddataSaving#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#13)]

## <a name="see-also"></a>См. также раздел
 [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)
