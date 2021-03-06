---
title: Отладка или отключение кода проекта в конструкторе XAML | Документация Майкрософт
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: ac600581-8fc8-49e3-abdf-1569a3483d74
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e7de0b3985e09f61fd0c63d1764304b150503883
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657932"
---
# <a name="debugging-or-disabling-project-code-in-xaml-designer"></a>Отладка или отключение кода проекта в конструкторе XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Во многих случаях необработанные исключения в конструкторе XAML могут вызываться попыткой кода проекта получить доступ к свойствам или методам, которые возвращают другие значения или работают по-другому, если приложение выполняется в конструкторе. Можно устранить эти исключения, отладив код проекта в другом экземпляре Visual Studio, или временно предотвратить их путем отключения кода проекта в конструкторе.

 Код проекта включает следующие объекты:

- настраиваемые элементы управления и пользовательские элементы управления;

- библиотеки классов;

- преобразователи значений;

- привязки данных времени разработки, созданные из кода проекта.

  При отключении кода проекта Visual Studio будет отображать заполнители, такие как имя свойства для привязки, где данные больше не доступны, или заполнитель для элемента управления, который больше не выполняется.

  ![Диалоговое окно необработанного исключения](../designers/media/xaml-unhandledexception.png "XAML_UnhandledException")

#### <a name="to-determine-if-project-code-is-causing-an-exception"></a>Как определить, вызвано ли исключение кодом проекта

1. В диалоговом окне необработанного исключения нажмите ссылку **Щелкните здесь для перезагрузки конструктора** .

2. В строке меню последовательно выберите пункты **Отладка**и **Начать отладку** , чтобы выполнить сборку приложения и запустить его.

     Если сборка и запуск приложения выполнились успешно, исключение времени разработки могло быть вызвано кодом проекта, запущенного в конструкторе.

#### <a name="to-debug-project-code-running-in-the-designer"></a>Отладка кода проекта, запущенного в конструкторе

1. В диалоговом окне необработанного исключения нажмите ссылку **Щелкните здесь для отключения работающего кода проекта и перезагрузки конструктора** .

2. В диспетчере задач Windows нажмите кнопку **Завершить задачу** , чтобы закрыть все экземпляры конструктора XAML Visual Studio, работающие в данный момент.

     ![Экземпляры конструктора XAML в TaskManager](../designers/media/xaml-taskmanager.png "XAML_TaskManager")

3. В Visual Studio откройте страницу XAML, содержащую код или элемент управления, который требуется отладить.

4. Откройте новый экземпляр Visual Studio, а затем второй экземпляр вашего проекта.

5. Установите точку останова в коде проекта.

6. В новом экземпляре Visual Studio в строке меню последовательно выберите пункты **Отладка**и **Присоединение к процессу**.

7. В диалоговом окне **Присоединение к процессу** выберите процесс **XDesProc.exe** в списке **Доступные процессы**и нажмите кнопку **Присоединиться** .

     ![Процесс конструктора XAML](../designers/media/xaml-attach.png "XAML_Attach")

     Это процесс для конструктора XAML в первом экземпляре Visual Studio.

8. В первом экземпляре Visual Studio в строке меню последовательно выберите пункты **Отладка**и **Начать отладку**.

     Теперь можно выполнить пошаговую отладку кода, работающего в конструкторе.

#### <a name="to-disable-project-code-in-the-designer"></a>Отключение кода проекта в конструкторе

- В диалоговом окне необработанного исключения нажмите ссылку **Щелкните здесь для отключения работающего кода проекта и перезагрузки конструктора** .

- Или же можно нажать кнопку **Отключить код проекта** в панели инструментов в конструкторе XAML.

     ![Кнопка "отключить код проекта"](../designers/media/xaml-disablecode.png "XAML_DisableCode")

     Вы можете нажать эту кнопку еще раз, чтобы включить код проекта.

    > [!NOTE]
    > Для проектов, предназначенных для процессоров ARM или X64, Visual Studio не может запустить код проекта в конструкторе, поэтому кнопка **Отключить код проекта** в конструкторе будет неактивна.

- Оба варианта приведут к перезагрузке конструктора, а затем будет отключен весь код для соответствующего проекта.

    > [!NOTE]
    > Отключение кода проекта может привести к потере данных времени разработки. Другой путь заключается в отладке кода, выполняемого в конструкторе.

## <a name="see-also"></a>См. также раздел
 [Разработка XAML в Visual Studio и Blend для Visual Studio](../designers/designing-xaml-in-visual-studio.md)
