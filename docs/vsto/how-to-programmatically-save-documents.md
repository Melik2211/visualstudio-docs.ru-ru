---
title: Практическое руководство. Программное сохранение документов
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving
- Word [Office development in Visual Studio], saving documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b4fbf8e4cb67d5216dc17c325911bb243fae6e1c
ms.sourcegitcommit: 5b34052a1c7d86179d7898ed532babb2d9dad4a3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/15/2019
ms.locfileid: "69490611"
---
# <a name="how-to-programmatically-save-documents"></a>Практическое руководство. Программное сохранение документов

Существует несколько способов сохранения Microsoft Office документов Word. Документ можно сохранить, не изменяя имя документа, или можно сохранить документ с новым именем.

[!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="save-a-document-without-changing-the-name"></a>Сохранение документа без изменения имени

### <a name="to-save-the-document-associated-with-a-document-level-customization"></a>Сохранение документа, связанного с настройкой на уровне документа

1. Вызовите метод <xref:Microsoft.Office.Tools.Word.Document.Save%2A> класса <xref:Microsoft.Office.Tools.Word.Document> . Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` в своем проекте.

     [!code-vb[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#7)]

### <a name="to-save-the-active-document"></a>Чтобы сохранить активный документ

1. Вызовите <xref:Microsoft.Office.Interop.Word._Document.Save%2A> метод для активного документа. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` или `ThisAddIn` в своем проекте.

    [!code-vb[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#8)]
    [!code-csharp[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#8)]

   Если вы не уверены, что документ, который нужно сохранить, является активным документом, его можно указать по имени.

### <a name="to-save-a-document-specified-by-name"></a>Сохранение документа, указанного по имени

1. Используйте имя документа в качестве аргумента для <xref:Microsoft.Office.Interop.Word.Documents> коллекции. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` или `ThisAddIn` в своем проекте.

     [!code-vb[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#9)]
     [!code-csharp[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#9)]

## <a name="save-a-document-with-a-new-name"></a>Сохранение документа с новым именем

`SaveAs` Используйте метод, чтобы сохранить документ с новым именем. Этот метод <xref:Microsoft.Office.Tools.Word.Document> ведущего элемента можно использовать в проекте Word уровня документа или в собственном <xref:Microsoft.Office.Interop.Word.Document> объекте любого проекта Word. Для этого метода требуется указать новое имя файла, но другие аргументы являются необязательными.

> [!NOTE]
> Если диалоговое окно **SaveAs** отображается внутри <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> обработчика `ThisDocument` событий и для параметра *Cancel* задано значение **false**, приложение может неожиданно завершить работу. Если для параметра *Cancel* задано **значение true**, появится сообщение об ошибке, указывающее, что автосохранение отключено.

### <a name="to-save-the-document-associated-with-a-document-level-customization-with-a-new-name"></a>Сохранение документа, связанного с настройкой на уровне документа, с новым именем

1. Вызовите `ThisDocument` метод класса в проекте, используя полный путь и имя файла. `SaveAs` Если файл с таким именем уже существует в этой папке, он будет перезаписан без запроса подтверждения. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` .

    > [!NOTE]
    > `SaveAs` Метод создает исключение, если целевой каталог не существует или при сохранении файла возникли другие проблемы. Рекомендуется использовать`try...catch` блок `SaveAs` вокруг метода или внутри вызывающего метода.

     [!code-vb[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#10)]

### <a name="to-save-a-native-document-with-a-new-name"></a>Сохранение собственного документа с новым именем

1. Вызовите <xref:Microsoft.Office.Interop.Word.Document> метод объекта, который необходимо сохранить, используя полный путь и имя файла. <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> Если файл с таким именем уже существует в этой папке, он будет перезаписан без запроса подтверждения.

     В следующем примере кода активный документ сохраняется с новым именем. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` или `ThisAddIn` в своем проекте.

    > [!NOTE]
    > <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> Метод создает исключение, если целевой каталог не существует или при сохранении файла возникли другие проблемы. Рекомендуется использовать метод **try... блок catch** вокруг <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> метода или внутри вызывающего метода.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#10)]

## <a name="compile-the-code"></a>Компиляция кода

Для этого примера кода требуется следующее.

- Чтобы сохранить документ по имени, документ с именем *невдокумент. doc* должен находиться в каталоге с именем *Test* на диске C.

- Чтобы сохранить документ с новым именем, на диске C должен существовать каталог с именем *Test* .

## <a name="see-also"></a>См. также

- [Практическое руководство. Программное закрытие документов](../vsto/how-to-programmatically-close-documents.md)
- [Практическое руководство. Открытие существующих документов программным способом](../vsto/how-to-programmatically-open-existing-documents.md)
- [Ведущий элемент документа](../vsto/document-host-item.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
