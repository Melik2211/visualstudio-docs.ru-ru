---
title: Как создать команду SharePoint | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3c07d541dc4f68f33d48e7cb41b6bc3923b2ea52
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189229"
---
# <a name="how-to-create-a-sharepoint-command"></a>Как создать команду SharePoint
  Если вы хотите использовать объектную модель сервера в расширении инструментов SharePoint, необходимо создать пользовательскую *команду SharePoint* для вызова API. Команда SharePoint определяется в сборке, которая может напрямую вызывать серверную объектную модель.

 Дополнительные сведения о назначении команд SharePoint см. в разделе [Вызов объектных моделей SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

### <a name="to-create-a-sharepoint-command"></a>Создание команды SharePoint

1. Создайте проект библиотеки классов со следующей конфигурацией:

    - Предназначен для .NET Framework 3,5. Дополнительные сведения о выборе требуемой версии .NET Framework см. в разделе [как выбрать целевую версию .NET Framework](../ide/visual-studio-multi-targeting-overview.md).

    - Нацелен на платформу AnyCPU или x64. По умолчанию целевой платформой для проектов библиотек классов является AnyCPU. Дополнительные сведения о выборе целевой платформы см. в разделе [руководство. Настройка проектов для целевых платформ](../ide/how-to-configure-projects-to-target-platforms.md).

    > [!NOTE]
    > Нельзя реализовать команду SharePoint в том же проекте, который определяет расширение "инструменты SharePoint", так как команды SharePoint предназначены для расширений .NET Framework 3,5 и инструментов SharePoint, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Необходимо определить все команды SharePoint, используемые вашим расширением в отдельном проекте. Дополнительные сведения см. [в статье Развертывание расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

2. Добавьте ссылки на следующие сборки:

    - Microsoft. VisualStudio. SharePoint. Commands

    - Microsoft. SharePoint

3. В классе в проекте создайте метод, определяющий команду SharePoint. Метод должен соответствовать следующим рекомендациям:

    - Он может иметь один или два параметра.

         Первый параметр должен быть <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>ным объектом. Этот объект предоставляет узел Microsoft. SharePoint. a или Microsoft. SharePoint. SPWeb, в котором выполняется команда. Он также предоставляет объект <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger>, который можно использовать для записи сообщений в окно **вывода** или **Список ошибок** окно в Visual Studio.

         Вторым параметром может быть выбранный вами тип, но этот параметр является необязательным. Этот параметр можно добавить в команду SharePoint, если необходимо передать данные из расширения инструментов SharePoint в команду.

    - Он может иметь возвращаемое значение, но это необязательно.

    - Второй параметр и возвращаемое значение должны быть типом, который может быть сериализован Windows Communication Foundation (WCF). Дополнительные сведения см. в разделе [типы, поддерживаемые сериализатором контрактов данных](/dotnet/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer) , и [использование класса XmlSerializer](/dotnet/framework/wcf/feature-details/using-the-xmlserializer-class).

    - Метод может иметь любую видимость (**открытый**, **внутренний**или **частный**) и может быть статическим или не статическим.

4. Примените <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> к методу. Этот атрибут задает уникальный идентификатор для команды. Этот идентификатор не обязательно должен совпадать с именем метода.

     При вызове команды из расширения инструментов SharePoint необходимо указать тот же уникальный идентификатор. Дополнительные сведения см. [в разделе инструкции. выполнение команды SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md).

## <a name="example"></a>Пример
 В следующем примере кода демонстрируется команда SharePoint с идентификатором `Contoso.Commands.UpgradeSolution`. Эта команда использует интерфейсы API в серверной модели объектов для обновления до развернутого решения.

 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#5)]

 Помимо неявного параметра first <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>, эта команда также имеет пользовательский строковый параметр, содержащий полный путь к WSP-файлу, который обновляется на сайте SharePoint. Чтобы просмотреть этот код в контексте более крупного примера, см. раздел [Пошаговое руководство. Создание настраиваемого шага развертывания для проектов SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="compiling-the-code"></a>Компиляция кода
 Для этого примера требуются ссылки на следующие сборки:

- Microsoft. VisualStudio. SharePoint. Commands

- Microsoft. SharePoint

## <a name="deploying-the-command"></a>Развертывание команды
 Чтобы развернуть команду, включите сборку команды в тот же пакет расширения [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] (*VSIX*) с сборкой расширения, которая использует команду. Кроме того, необходимо добавить запись для сборки команды в файл Extension. vsixmanifest. Дополнительные сведения см. [в статье Развертывание расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>См. также
- [Вызов объектных моделей SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Инструкции: выполнение команды SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [Пошаговое руководство. расширение обозреватель сервера для показа веб-частей](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
