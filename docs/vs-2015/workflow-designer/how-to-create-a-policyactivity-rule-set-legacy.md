---
title: Как создать набор правил PolicyActivity (для прежних версий) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- PolicyActivity activity, creating rule sets
- Rule Set Editor dialog box
- PolicyActivity activity, selecting rule sets
- Select Rule Set dialog box
- rule sets, creating for PolicyActivity
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0f8599348d204d149f3e28d17d681941ddf476b8
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849317"
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>Как создать набор правил PolicyActivity (для прежних версий)
В этом разделе описывается создание набора правил действия политики с помощью средства [!INCLUDE[wfd1](../includes/wfd1-md.md)] прежних версий, ориентированного на работу с [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 После перетаскивания элемента действия **политики** из **области элементов** в рабочую область конструктора рабочих процессов необходимо выбрать существующее правило или создать новый набор правил для действия [PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) . Для выбора существующего набора правил используется [диалоговое окно Выбор набора правил (устаревшая)](../workflow-designer/select-rule-set-dialog-box-legacy.md) , а наборы правил создаются с помощью [диалогового окна Редактор набора правил (прежние версии)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).

> [!NOTE]
> Диалоговое окно [Редактор набора правил (устаревшее)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) можно открыть непосредственно, дважды щелкнув действие [PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) в рабочей области конструктора рабочих процессов.

### <a name="to-select-or-create-a-rule-set-for-a-policyactivity-activity"></a>Выбор или создание набора правил для действия PolicyActivity

1. Щелкните правой кнопкой мыши [PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx)и выберите пункт **свойства** , чтобы открыть окно **Свойства** .

2. Щелкните свойство **рулесетреференце** .

3. Выполните одно из следующих действий.

    - Щелкните **рулесетреференце** многоточие **[...]** , а затем выберите существующий набор правил в [диалоговом окне Выбор набора правил (прежние версии)](../workflow-designer/select-rule-set-dialog-box-legacy.md). Далее перейдите к шагу 10.

         \- или -

    - Введите имя набора правил. Щелкните **рулесетреференце** многоточие **[...]** , а затем выберите **изменить** в [диалоговом окне Выбор набора правил (прежние версии)](../workflow-designer/select-rule-set-dialog-box-legacy.md).

         \- или -

    - Введите имя набора правил. Разверните свойство **рулесетреференце** и выберите многоточие **[...]** в свойстве **Определение набора правил** .

         Откроется [диалоговое окно Редактор набора правил (устаревшая)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) .

4. В [диалоговом окне Редактор набора правил (устаревшая)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)нажмите кнопку **Добавить правило** , чтобы добавить новое правило в набор правил.

5. Введите свойства **имя**, **приоритет**и повторная **Оценка** , либо примите значения по умолчанию.

6. Введите текст **условия**.

7. Введите текст для **действий then** и **else**.

8. Нажмите кнопку **Добавить правило** еще раз, чтобы добавить другое правило.

9. Завершив настройку, нажмите кнопку **ОК**.

## <a name="see-also"></a>См. также раздел
 [Диалоговое окно "](../workflow-designer/rule-set-editor-dialog-box-legacy.md) [PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) [" диалогового окна "Выбор набора правил"](../workflow-designer/select-rule-set-dialog-box-legacy.md) (устаревшее) с использованием [устаревших действий рабочего процесса](../workflow-designer/legacy-workflow-activities.md) [для действия политики](https://msdn2.microsoft.com/library/bb675229.aspx)
