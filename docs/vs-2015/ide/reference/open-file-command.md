---
title: Команда "Открыть файл" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openfile
helpviewer_keywords:
- Open File command
- File.OpenFile command
- of command
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1c8dcf35e4c045db0d9acd45e2eb307a31ba39f1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671932"
---
# <a name="open-file-command"></a>Команда Open File
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Открывает существующий файл и позволяет указать редактор.

## <a name="syntax"></a>Синтаксис

```
File.OpenFile filename [/e:editorname]
```

## <a name="arguments"></a>Аргументы
 `filename` Обязательный. Полный или частичный путь и имя для открываемого файла. Пути, содержащие пробелы, следует заключить в кавычки.

## <a name="switches"></a>Переключатели
 /e:`editorname` (необязательно). Имя редактора, в котором будет открыт файл. Если аргумент указан, но имя редактора не предоставляется, отображается диалоговое окно **Открыть с помощью**.

 В синтаксической структуре аргумента /e:`editorname` имена редакторов используются в том виде, в каком они отображаются в диалоговом окне "Открыть с помощью", с заключением в кавычки.

 Например, чтобы открыть файл в редакторе исходного кода, нужно ввести для аргумента /e:`editorname` следующую строку:

```
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Примечания
 Когда вы вводите путь, функция автозавершения пытается определить правильный путь и правильное имя файла.

## <a name="example"></a>Пример
 Этот пример открывает файл стилей "Test1.CSS" в редакторе исходного кода.

```
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>См. также
 [Команды Visual Studio ](../../ide/reference/visual-studio-commands.md) [Command окно ](../../ide/reference/command-window.md) [Immediate окно ](../../ide/reference/immediate-window.md) [Find/Command ](../../ide/find-command-box.md) [командные псевдонимы команды Studio](../../ide/reference/visual-studio-command-aliases.md)
