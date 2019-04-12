---
title: Для каждого монитора Awareness support для средств расширения Visual Studio
titleSuffix: ''
description: Дополнительные сведения о новой поддержки расширителя для каждого monitor-awareness доступны в Visual Studio 2019.
ms.date: 04/09/2019
helpviewer_keywords:
- Visual Studio, PMA, per-monitor-awareness, extenders, Windows Forms
- Per-Monitor Awareness support for extenders
ms.assetid: ''
author: rub8n
ms.author: rurios
manager: anthc
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: reference
ms.workload:
- multiple
ms.openlocfilehash: 42de73a29e053066c0fbeca72ca3511b58b2fa7e
ms.sourcegitcommit: 0a2fdc23faee77187e10a1c19665ba5a1ac68e72
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2019
ms.locfileid: "59477692"
---
# <a name="per-monitor-awareness-support-for-visual-studio-extenders"></a>Для каждого монитора Awareness support для средств расширения Visual Studio

Версий, предшествующих Visual Studio 2019 было присвоено виду системы, а не для каждого монитора DPI виду (PMA) контекста awareness точек на ДЮЙМ. В системе, awareness завершилась в ограниченном графический пользовательский интерфейс (например нечетким шрифты или значков) каждый раз, когда Visual Studio у для подготовки к просмотру на мониторах с отличающимися масштабами факторов или удаленное подключение компьютеров с помощью различных конфигурациях (например, разная Windows масштабирование).

Контексте awareness DPI 2019 г. Visual Studio — набор, как и в виду, что позволяет Visual Studio для подготовки к просмотру в соответствии с конфигурацией области отображения, в котором она размещена на монитор, а не универсального определенные конфигурации. В конечном счете перевод на четкое пользовательского интерфейса для зон, которые реализуют PMA поддержки.

Ссылаться на [высокий уровень разработки приложений рабочего стола DPI в Windows](https://docs.microsoft.com/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) Дополнительные сведения об условиях и общий сценарий, рассматриваемые в данном документе.

## <a name="quickstart"></a>Краткое руководство
- Убедитесь, Visual Studio выполняется в режиме PMA (см. в разделе **Включение PMA**)

- Успешно проходят проверку вашего расширения работает через ряд распространенных сценариев (см. в разделе **тестирование расширений для проблемы PMA**)

- Если вы обнаружили проблемы, вы должны добавить новый пакет ценная PMA диагностировать, а устранение проблем с помощью стратегии и рекомендации, описанные в этом документе

## <a name="enabling-pma"></a>Включение PMA
Чтобы включить PMA в Visual Studio, следует соблюдать следующие требования:
1)  Windows 10 апреля 2018 г. обновление (v1803 RS4) или более поздней версии
2)  .NET framework 4.8 RTM или более поздней версии (в настоящее время поставляется как автономный Предварительный просмотр или пакета с последнего Windows Insider сборок)
3)  Visual Studio 2019 с [«Оптимизация отрисовки для экранов с различным плотности»](https://docs.microsoft.com/visualstudio/ide/reference/general-environment-options-dialog-box?view=vs-2019) параметр включен

Если эти требования выполняются, Visual Studio автоматически включит PMA всех этапах процесса.

## <a name="testing-your-extensions-for-pma-issues"></a>Тестирование расширений для PMA проблемы

Visual Studio официально поддерживает платформы WPF, Windows Forms, Win32 и пользовательского интерфейса HTML/JS. Когда Visual Studio переключается в режим PMA, различных стеков пользовательского интерфейса будет работать по-разному. Таким образом независимо от платформы пользовательского интерфейса, рекомендуется, чтобы убедиться, что элементы пользовательского интерфейса является совместимым с PMA выполняется тестового прохода.

Независимо от платформы пользовательского интерфейса поддерживает расширения, рекомендуется проверить следующие распространенные сценарии:

1. Изменение коэффициент масштабирования среды одного монитора, пока приложение находится выполнения *
    - Этот сценарий позволяет проверить, что пользовательского интерфейса отвечает на динамическое изменение точек на ДЮЙМ Windows

2. Стыковка и Отстыковка портативного компьютера, где присоединенного монитора установлен в первичную и присоединенного монитора имеет другой масштаб, чем у основного, во время работы приложения.
    - Этот сценарий позволяет проверить, что пользовательского интерфейса отвечает на экран изменения DPI, а также обработка отображает динамически добавления или удаления

3. Наличие несколько мониторов с отличающимися масштабами факторов и перемещение приложения между ними.
    - Этот сценарий позволяет проверить, что пользовательского интерфейса отвечает на изменения DPI отображения
    
4. Удаленное взаимодействие на компьютер при локальном и удаленном компьютерах у различных масштаба для основного монитора.
    - Этот сценарий позволяет проверить, что пользовательского интерфейса отвечает на динамическое изменение точек на ДЮЙМ Windows

Это удобно предварительные проверить ли пользовательского интерфейса могут возникнуть проблемы является ли код использует либо *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper* или *Microsoft.VisualStudio.PlatformUI.DpiHelper* классы. Эти старые DpiHelper классы поддерживают только системы поддержка dpi и не всегда правильно функционировать, когда процесс является PMA.

Типичное применение этих DpiHelpers выглядят следующим образом:

```cs
Point screenTopRight = logicalBounds.TopRight.LogicalToDeviceUnits();

POINT screenIntTopRight = new POINT
{
    x = (int)screenTopRIght.X,
    y = (int)screenTopRIght.Y
}

IntPtr monitor = NativeMethods.MonitorFromPoint(screenIntTopRight, NativeMethods.Monitor_DEFAULTTONEARST);
```

В предыдущем примере прямоугольник, представляющий логические границы окна преобразуется в единицы устройства, таким образом, можно передать собственный метод MonitorFromPoint, ожидает, что координаты устройства для возвращения назад указатель точные монитора.

### <a name="classes-of-issues"></a>Классы проблем

При включении PMA для Visual Studio пользовательского интерфейса может реплицировать проблемы стандартными способами. Многие, если не все эти проблемы может произойти в любой из поддерживаемых платформ пользовательского интерфейса Visual Studios. Кроме того, эти проблемы может произойти, даже когда части UI размещается в смешанном режиме разрешение DPI, сценарии (см. Windows [документации](https://docs.microsoft.com/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) для получения дополнительных сведений). 

#### <a name="win32-window-creation"></a>Создание окна Win32
При создании windows с помощью CreateWindow() или CreateWindowEx(), распространенный подход создать окно с координатами 0,0 (левый верхний угол основного монитора), затем переместите ее его последняя позиция. Тем не менее это может привести к окна, чтобы активировать на ДЮЙМ изменить сообщение или событие, которое можно повторно активируйте другие сообщения пользовательского интерфейса или события и со временем привести к нежелательным поведением или подготовки отчетов.

#### <a name="wpf-element-placement"></a>Размещение элемента WPF
При перемещении элементов WPF, с помощью старого Microsoft.VisualStudio.Utilities.Dpi.DpiHelper, координаты верхнего левого может не быть вычислена правильно всякий раз, когда элементы в случае вторичного точек на ДЮЙМ.

#### <a name="serialization-of-ui-element-sizes-or-positions"></a>Сериализация размерами элементов пользовательского интерфейса или позиции
Каждый раз, когда пользовательский Интерфейс размера или положения восстанавливается в другом контексте точек на ДЮЙМ, чем он был сохранен на, он будет расположен и размера неправильно. Это происходит, так как логические границы окна, преобразуются в единицы устройства, таким образом, его можно передать в метод Win32 MonitorFromPoint, ожидает, что координаты устройства для возвращения назад указатель точные монитор.

#### <a name="incorrect-scaling"></a>Неправильное масштабирование
Элементы пользовательского интерфейса, созданные на основной точек на ДЮЙМ масштабируется правильно, однако при перемещении на дисплей с другим значением DPI, они не изменить масштаб, и таким образом, их содержимое в конечном итоге слишком велико или слишком мало.

#### <a name="incorrect-bounding"></a>Неправильный ограничивающего прямоугольника
Аналогичным образом для проблемы масштабирования, элементы пользовательского интерфейса вычислит их границы правильно на их основного контекста точек на ДЮЙМ, однако при перемещении на неосновной DPI, они не будут правильно вычислить новые границы. Таким образом окно содержимого оказывается слишком мало или слишком велико по сравнению с размещения пользовательского интерфейса, что приводит к пустого пространства или обрезки.

#### <a name="drag--drop"></a>Перетаскивание
Каждый раз, когда внутри сценариев DPI смешанного режима (например различные элементы пользовательского интерфейса визуализации в контексте DPI основного и вторичного) путем перетаскивания координаты может быть неверно вычисленных, полученный в результате позиции окончательный перетаскивания вверх неправильный.

#### <a name="out-of-process-ui"></a>Out-of-process пользовательского интерфейса
Пользовательский Интерфейс создается вне процесса и при создании внешнего процесса в другой режим awareness точек на ДЮЙМ, чем в Visual Studio, это может вызвать любой из предыдущих проблемы отрисовки.

#### <a name="windows-forms-controls-images-or-windows-not-displaying"></a>Элементы управления Windows Forms, изображения или windows, которые не отображаются
Одной из причин этой проблемы является разработчиков, пытающихся изменение родительского объекта элемента управления или окно с одной DpiAwarenessContext в другое окно DpiAwarenessContext. 

На следующих рисунках показаны текущими ограничениями операционной системы Windows в родительские связи windows, если поток, размещение поведение явно изменен:

![Снимок экрана поведение правильный родительские связи](../../extensibility/ux-guidelines/media/PMA-parenting-behavior.PNG)

Таким образом Если родительско дочернее отношение между неподдерживаемые режимы, его не удастся, и элемент управления или окно может не отображаться должным образом.

### <a name="diagnosing-issues"></a>Диагностика проблем
Существует много факторов, которые следует учитывать при определении проблем, связанных с PMA: 

1. Пользовательский Интерфейс или API ожидается логическое или значения устройства.
    - Пользовательского интерфейса WPF и API-интерфейсы обычно используют логические значения (но не всегда)
    - Пользовательского интерфейса Win32 и API-интерфейсы обычно используют значения устройства

2. Откуда приходят значения?
    - При получении значений из другой пользовательский Интерфейс или API, это устройство передачи или логические значения.
    - При получении значений из нескольких источников, все используйте/ожидают, что же типы значений или преобразования требуется комбинировать и сопоставлять?

3. Такое константы пользовательского интерфейса используются и какие формы являются ли они в

4. Является потоком в правильном контексте DPI для значений получает?
    - Изменения, чтобы включить CLMM обычно следует помещать путей кода в правильном контексте, тем не менее, может выполнить работу за пределами потока событий или цикла основного сообщения из неправильного контекста точек на ДЮЙМ.

5. Значения выходить за границы контекста DPI?
    - Перетаскивание – это распространенная ситуация, где координаты может пересекать контекстов точек на ДЮЙМ. Окно пытается стать выполнено правильно, но в некоторых случаях пользовательского интерфейса ведущего приложения может потребоваться выполнить преобразование работу, чтобы обеспечить соответствующий границ контекста.

### <a name="pma-nugget-package"></a>Ценная PMA пакета
Новые библиотеки DpiAwarness можно найти в пакете Microsoft.VisualStudio.DpiAwareness NuGet.

### <a name="recommended-tools"></a>Рекомендованные средства
Следующие средства могут помочь при отладке проблем, связанных с PMA через ряд различных стеков пользовательского интерфейса, поддерживается в Visual Studio.

#### <a name="snoop"></a>Snoop
Snoop является средством отладки XAML, которое имеет некоторые дополнительные функциональные возможности, не имеет встроенные средства Visual Studio XAML. Кроме того Snoop не активно отладки Visual Studio, чтобы иметь возможность просмотреть и настроить его пользовательского интерфейса WPF. Двумя основными способами Snoop могут быть полезными для диагностики проблем PMA для проверки координат логическое расположение и размер границы, и для проверки пользовательского интерфейса имел правой точек на ДЮЙМ.
 
#### <a name="visual-studio-xaml-tools"></a>Инструменты Visual Studio XAML
Как и Snoop средства XAML в Visual Studio может помочь в выявлении проблем PMA. После нахождения скорее всего выяснилось, можно установить точки останова и использовать окна динамического визуального дерева, а также окнах отладки, для изучения границы пользовательского интерфейса и текущего точек на ДЮЙМ.

## <a name="strategies-for-fixing-pma-issues"></a>Стратегии устранения проблем PMA

### <a name="replacing-dpihelper-calls"></a>Замена вызовов DpiHelper
В большинстве случаев Устранение проблем пользовательского интерфейса в PMA сводится к замена вызовов в управляемом коде старый: *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper* и *Microsoft.VisualStudio.PlatformUI.DpiHelper* классам с вызовов к новому *Microsoft.VisualStudio.Utilities.DpiAwareness* вспомогательный класс. 

Для машинного кода, его придется заменив вызовы старого *VsUI::CDpiHelper* класс с вызовами к новому *VsUI::CDpiAwareness* класса. Новые классы DpiAwareness и CDpiAwareness предлагают же вспомогательные функции преобразования, как классы DpiHelper, но требуется дополнительный входной параметр: элемент пользовательского интерфейса для использования в качестве ссылки для операции преобразования. 

Управляемый класс DpiAwareness предлагает вспомогательные функции WPF и визуальных элементов, элементы управления Windows Forms и дескрипторы Win32 HWND HMONITORs (как в виде IntPtrs), при собственного CDpiAwareness предложения HWND и HMONITOR вспомогательные классы.

### <a name="windows-forms-dialogs-windows-or-controls-displayed-in-the-wrong-dpiawarenesscontext"></a>Диалоговые окна Windows Forms, windows или элементами управления, отображаемыми в неправильный DpiAwarenessContext
Даже после успешного родительские связи Windows с разных DpiAwarenessContext (из-за windows по умолчанию), пользователи по-прежнему могут видеть масштабирование проблемы в разных окнах DpiAwarenessContext масштабировании по-разному. Таким образом пользователи могут видеть нечеткого/выравнивание текста или возникновения проблем с образом в пользовательском Интерфейсе.

Решение является установка области DpiAwarenessContext для всех окон и элементов управления в приложении.

### <a name="tlmm-dialogs"></a>Диалоговые окна TLMM
При создании окон верхнего уровня, например создания дочерних модальных диалогов, важно убедиться, что поток находится в правильном состоянии до создания HWND. Поток могут быть помещены в awareness системы, используя вспомогательный метод CDpiScope в машинный код или управляемый вспомогательный модуль DpiAwareness.EnterDpiScope. (TLMM обычно можно использовать для диалоговых окон отличных от WPF или windows.)

### <a name="child-level-mixed-mode-clmm"></a>Дочерний уровень смешанный режим (CLMM)

По умолчанию дочерние окна получают один и тот же режим поддержки определения DPI, как их родительские элементы. Тем не менее можно использовать SetThreadDpiHostingBehavior переопределить его, и дочерние окна выполнялись в другой режим масштабирования, чем их родительской или серверной.


#### <a name="clmm-issues"></a>Проблемы CLMM
Большая часть операций вычисления пользовательского интерфейса, как часть главной обмена сообщениями цикла или событие цепочки должны работать в правильном контексте точек на ДЮЙМ. Тем не менее если координаты или изменения размера вычисления выполняются за пределами этих основных рабочих процессов (например, во время выполнения задачи бездействия или вне потока пользовательского интерфейса, затем может быть неправильным, что ведет к потери портативного компьютера пользовательского интерфейса или неверно изменения размера проблемы контекст текущего точек на ДЮЙМ. Размещение потока в правильном состоянии для пользовательского интерфейса рабочего обычно решает проблему.
 
#### <a name="opting-out-of-clmm"></a>Отказ от CLMM
Если окно инструментов отличных от WPF переносится для полной поддержки PMA, его необходимо отказаться от CLMM. Чтобы сделать это, должен быть реализован новый интерфейс: IVsDpiAware.

C#:
```cs
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
public interface IVsDpiAeware
{
    [ComAliasName("Microsoft.VisualStudio.Shell.Interop.VSDPIMode")]
    uint Mode {get;}
}
```
 
C++:
```cplusplus
IVsDpiAware : public IUnknown
{
    public:
        HRRESULT STDMETHODCALLTYPE get_Mode(__RCP__out VSDPIMODE *dwMode);
};
```
 

Для управляемых языков — лучшее место для реализации этого интерфейса в том же классе, который является производным от *Microsoft.VisualStudio.Shell.ToolWindowPane*. Для C++, лучше всего для реализации этого интерфейса — в том же классе, который реализует *IVsWindowPane* из vsshell.h.

Значение, возвращенное свойство Mode в интерфейсе является __VSDPIMODE (и приведение к целое число без знака в управляемого):

```cs
enum __VSDPIMODE
    {
        VSDM_Unaware    = 0x01,
        VSDM_System     = 0x02,
        VSDM_PerMonitor = 0x03,
    }
```

- Означает, что окно инструментов должен обрабатывать 96 точек на ДЮЙМ, Windows будет обрабатывать, его масштабирования для всех других DPI. Полученный на содержимое, нечетко.
- Окно инструментов должен обрабатывать DPI для сервера-источника систем означает отображения точек на ДЮЙМ. Любой дисплей с помощью сопоставления точек на ДЮЙМ будет выглядеть четкое, но если DPI отличается или изменяется во время сеанса, Windows будет обрабатывать масштабирование, и оно станет нечетко.
- PerMonitor означает, что окно инструментов должен обрабатывать все DPI на все устройства отображения и при каждом изменении значения DPI.

**Примечание**. Visual Studio поддерживает PerMonitorV2 awareness только в том случае, поэтому значение перечисления PerMonitor преобразуется в значение Windows DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2.

## <a name="known-issues"></a>Известные проблемы

### <a name="windows-forms"></a>Windows Forms

Чтобы оптимизировать для новых сценариев смешанного режима, Windows Forms изменен способ создания элементов управления и окон всякий раз, когда родительского элемента не было задано явно. Ранее, элементы управления без явной родительского использовать внутренний «парковки окно» как временный родительский элемент для элемента управления или создания окна. 

«Парковки окно» получает его DpiAwarenessContext из процесса, в которой выполняется приложение. Элемент управления наследует же DpiAwarenessContext окно парковки и бы переподчиняются родителю или ожидаемой исходный разработчиком приложения.  Это не сработает, если предполагаемого родительского элемента управления не же DpiAwarenessContext качестве создаваемого элемента управления.

Начиная с .NET 4.8 Если родительский не задан явно в элемент управления или в окне, Windows Forms будет запрашивать парковки окно, которое соответствует DpiAwarenessContext потока, в котором запрашивается Создание элемента управления или окно и использовать его в качестве временных родителя. Другими словами при создании элемента управления теперь создается с предполагаемым DpiAwarenessContext. Элемент управления или окно будет затем быть изменен порядок наследования ожидаемый родителю разработчиком приложения.