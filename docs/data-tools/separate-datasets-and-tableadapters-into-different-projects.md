---
title: Разделение наборов данных и TableAdapter на разные проекты
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 8df444646512ecd4dba866fccf6da5fdf7a8bab3
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586228"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Разделение наборов данных и TableAdapter на разные проекты
Типизированные наборы данных были улучшены, чтобы классы [TableAdapter](create-and-configure-tableadapters.md) и наборы данных могли быть созданы в отдельных проектах. Это позволяет быстро разделять уровни приложений и создавать n-уровневые приложения для данных.

В следующей процедуре описывается процесс использования **Конструктор наборов данных** для создания кода набора данных в проекте, отдельном от проекта, содержащего созданный код адаптера таблицы.

## <a name="separate-datasets-and-tableadapters"></a>Отделение наборов данных и адаптеров таблиц
При разделении кода набора данных из кода TableAdapter проект, содержащий код набора данных, должен находиться в текущем решении. Если этот проект не находится в текущем решении, он не будет доступен в списке **проект набора данных** в окне **свойства** .

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-separate-the-dataset-into-a-different-project"></a>Отделение набора данных от другого проекта

1. Откройте решение, содержащее набор данных (*XSD* -файл).

    > [!NOTE]
    > Если решение не содержит проект, в котором нужно разделить код набора данных, создайте проект или добавьте существующий проект в решение.

2. Дважды щелкните файл типизированного набора данных ( *XSD* -файл) в **Обозреватель решений** , чтобы открыть набор данных в **Конструктор наборов данных**.

3. Выберите пустую область **Конструктор наборов данных**.

4. В окне **Свойства** выберите узел **проекта набора данных** .

5. В списке **проект набора данных** выберите имя проекта, в котором нужно создать код набора данных.

     После выбора проекта, в котором необходимо создать код набора данных, свойство **файла набора данных** заполняется именем файла по умолчанию. При необходимости это имя можно изменить. Кроме того, если вы хотите создать код набора данных в определенном каталоге, можно задать для свойства **папки проекта** имя папки.

    > [!NOTE]
    > При разделении наборов данных и адаптеров таблиц (с помощью свойства **Project DataSet** ) существующие классы частичного набора данных в проекте не перемещаются автоматически. Существующие классы частичного набора данных необходимо вручную переместить в проект набора данных.

6. Сохраните набор данных.

     Код набора данных создается в выбранном проекте в свойстве **проекта набора данных** , а код **TableAdapter** создается в текущем проекте.

По умолчанию после разделения набора данных и кода TableAdapter результатом будет отдельный файл класса в каждом проекте. Исходный проект содержит файл с именем *DataSetName. Designer. vb* (или *DataSetName.Designer.CS*), который содержит код адаптера таблицы. Проект, указанный в свойстве **проекта набора данных** , имеет файл с именем *DataSetName. DataSet. Designer. vb* (или *DataSetName.DataSet.Designer.CS*), содержащий код набора данных.

> [!NOTE]
> Чтобы просмотреть созданный файл класса, выберите набор данных или проект TableAdapter. Затем в **Обозреватель решений**выберите пункт **Показывать все файлы**.

## <a name="see-also"></a>См. также:

- [Общие сведения об n-уровневых приложениях](../data-tools/n-tier-data-applications-overview.md)
- [Пошаговое руководство. Создание n-уровневого приложения для работы с данными](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Иерархическое обновление](../data-tools/hierarchical-update.md)
- [Доступ к данным в Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [ADO.NET](/dotnet/framework/data/adonet/index)
