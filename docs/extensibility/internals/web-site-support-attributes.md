---
title: Атрибуты поддержки веб-сайта | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 07486ea3a962bcb81f65ad0b61ea2e41b3248678
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721609"
---
# <a name="web-site-support-attributes"></a>Атрибуты поддержки веб-сайтов
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проект веб-сайта можно расширить, чтобы обеспечить поддержку языков веб-программирования. Язык должен быть зарегистрирован в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] поэтому шаблоны проектов могут отображаться в диалоговом окне **новый веб-сайт** при выборе языка.

Образец IronPython Studio включает в себя поддержку веб-сайтов. Пример содержит следующие классы атрибутов для регистрации IronPython в качестве языка CodeBehind для новых веб-проектов.

## <a name="websiteprojectattribute"></a>вебситепрожектаттрибуте
 Этот атрибут размещается в проекте языка. Он добавляет язык в список языков веб-программирования в списке **язык** диалогового окна **новый веб-сайт** . Например, следующий код добавляет IronPython в список:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Этот атрибут также задает путь к шаблонам для указания на папку Templates. Дополнительные сведения о расположении папки Templates см. в разделе [шаблоны поддержки веб-сайтов](../../extensibility/internals/web-site-support-templates.md).

## <a name="websiteprojectrelatedfilesattribute"></a>вебситепрожектрелатедфилесаттрибуте
 Этот атрибут размещается в проекте языка. Он позволяет проекту веб-сайта вкладывать один тип файла (связанный) в другой тип файла (основной) в **Обозреватель решений**.

 Например, следующий код указывает, что файл фонового кода IronPython связан с файлом. aspx. При создании новой веб-страницы. aspx в решении веб-сайта IronPython создается новый исходный файл с расширением «копировать», который отображается как дочерний узел страницы. aspx.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>провидеинтеллисенсепровидераттрибуте
 Этот атрибут размещается в пакете языкового проекта. Он выбирает поставщик IntelliSense для языка.

 Например, следующий код указывает, что экземпляр Писонинтеллисенсепровидер, который реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, должен быть создан по запросу для предоставления языковых служб.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 Реализация Ивсинтеллисенсепрожект обрабатывает ссылки и вызывает компилятор языка, когда веб-страница с кодом запрашивается, но не кэшируется.

## <a name="see-also"></a>См. также
- [Поддержка веб-сайтов](../../extensibility/internals/web-site-support.md)