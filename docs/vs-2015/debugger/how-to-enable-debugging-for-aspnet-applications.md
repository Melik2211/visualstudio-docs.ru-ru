---
title: Как включить отладку для приложений ASP.NET | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications
- Web.config configuration file, debug mode
- debugging [Visual Studio], ASP.NET
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5726e964a0db2fae1b902f54a14e206dbc03a148
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/20/2020
ms.locfileid: "77477012"
---
# <a name="how-to-enable-debugging-for-aspnet-applications"></a>Практическое руководство. Включение отладки для приложений ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Для включения отладки необходимо включить ее на странице **Свойства проекта** и в файле web.config приложения.  
  
> [!NOTE]  
> В зависимости от установок или выпуска сервера доступные диалоговые окна и команды меню могут отличаться от описанных в справке. Чтобы изменить параметры, выберите **Импорт и экспорт параметров** в меню **Сервис** . Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](/previous-versions/zbhkx167(v=vs.140)).  
  
### <a name="to-enable-aspnet-debugging-in-the-project-properties-visual-basicc"></a>Включение отладки ASP.NET в свойствах проекта (Visual Basic/C#)  
  
1. В окне **Обозреватель решений**правой кнопкой мыши щелкните имя веб-проекта и выберите пункт **Свойства**.  
  
2. На странице свойств проекта перейдите на вкладку **Веб** .  
  
3. В окне **Отладчики**установите флажок **ASP.NET** .  
  
### <a name="to-enable-debugging-in-the-webconfig-file"></a>Включение отладки в файле web.config  
  
1. Откройте файл web.config с использованием любого стандартного текстового редактора или анализатора XML.  
  
    > [!NOTE]  
    > Удаленный доступ к этому файлу с помощью браузера невозможен. Из соображений безопасности настройка служб Microsoft IIS [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] осуществляется ASP.NET таким образом, чтобы предотвратить прямой доступ к файлам Web.config с помощью браузеров. При попытке доступа к файлу конфигурации с помощью браузера будет выдана ошибка доступа HTTP 403.  
  
2. Файл Web.config — это XML-файл, поэтому он содержит вложенные разделы, помеченные тегами. Найдите элемент `configuration/system.web/compilation`. Если элемент compilation не существует, создайте его.  
  
3. Если элемент `compilation` не содержит атрибут `debug` , добавьте этот атрибут к элементу.  
  
4. Убедитесь в том, что значение атрибута `debug` равно `true`.  
  
Файл Web.config должен выглядеть, как следующий пример. Обратите внимание, что между элементами system.web и configuration могут быть другие разделы  
  
- разделы элементов между элементами system.web и configuration  
  
- разделы элементов между элементами system.web и compilation  
  
- Элемент compilation может содержать другие элементы или атрибуты  
  
## <a name="example"></a>Пример  
  
```  
<configuration>  
    ...  
    <system.web>  
        <compilation  
            debug="true"  
            ...  
        >  
        ...  
        </compilation>  
    </system.web>  
</configuration>  
```  
  
## <a name="robust-programming"></a>Отказоустойчивость  
С помощью объекта [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] производится автоматическое обнаружение изменений в файлах Web.config и применяются новые параметры конфигурации. При этом нет необходимости перезагружать компьютер или IIS, чтобы изменения вступили в силу.  
  
Веб-сайт может содержать несколько виртуальных каталогов и подкаталогов. и файлы Web.config могут содержаться в каждом из них. Приложения [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] наследуют параметры от файлов Web.config, находящихся на более высоких уровнях URL-пути. Файлы иерархической конфигурации позволяют изменять параметры различных приложений [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] одновременно, например, для всех приложений, расположенных ниже по иерархии. Однако если атрибут `debug` задан в файле, находящемся ниже по иерархии, то он будет переопределять более высокое значение.  
  
Например, можно указать `debug="true"` в `www.microsoft.com/aaa/Web.config`, а любое приложение в папке AAA или в любой вложенной папке AAA будет наследовать этот параметр. Таким образом, если приложение [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] находится на `www.microsoft.com/aaa/bbb`, оно будет наследовать этот параметр, как и любые [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] приложения в `www.microsoft.com/aaa/ccc`, `www.microsoft.com/aaa/ddd`и т. д. Единственное исключение — случай, когда одно из приложений переопределяет настройку посредством собственного файла Web.config, находящегося ниже по иерархии.  
  
Включение режима отладки сильно отразится на производительности приложения [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] . Режим отладки следует отключить перед развертыванием конечного приложения или перед оценкой его производительности.  
  
## <a name="see-also"></a>См. также:  
[Отладка приложений ASP.NET и AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)  
