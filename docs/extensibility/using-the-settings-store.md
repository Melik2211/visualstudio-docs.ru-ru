---
title: Использование хранилища параметров | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9c42835e720fd3c33e53d862192e3e2863a4423
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72632597"
---
# <a name="using-the-settings-store"></a>Использование хранилища параметров
Существует два типа хранилищ параметров.

- Параметры конфигурации, доступные только для чтения параметры Visual Studio и VSPackage. Visual Studio объединяет параметры из всех известных файлов pkgdef в это хранилище.

- Параметры пользователя, доступные для записи, такие как параметры, отображаемые на страницах диалогового окна **Параметры** , страницы свойств и некоторые другие диалоговые окна. Расширения Visual Studio могут использовать их для локального хранения небольших объемов данных.

  В этом пошаговом руководстве показано, как считывать данные из хранилища параметров конфигурации. Описание процесса записи в хранилище параметров пользователя см. в статье [запись в хранилище параметров пользователя](../extensibility/writing-to-the-user-settings-store.md) .

## <a name="creating-the-example-project"></a>Создание примера проекта
 В этом разделе показано, как создать простой проект расширения с помощью команды меню для демонстрации.

1. Каждое расширение Visual Studio начинается с проекта развертывания VSIX, который будет содержать ресурсы расширения. Создайте проект [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX с именем `SettingsStoreExtension`. Шаблон проекта VSIX можно найти в диалоговом окне **Новый проект** в разделе **Визуальная C# или расширяемость**.

2. Теперь добавьте пользовательский шаблон элемента команды с именем **сеттингссторекомманд**. В диалоговом окне **Добавление нового элемента** перейдите к элементу  **C# Visual/Extensibility** и выберите пункт **пользовательская команда**. В поле **имя** в нижней части окна измените имя файла команд на **SettingsStoreCommand.CS**. Дополнительные сведения о создании пользовательской команды см. в разделе [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md) .

## <a name="using-the-configuration-settings-store"></a>Использование хранилища параметров конфигурации
 В этом разделе показано, как обнаруживать и отображать параметры конфигурации.

1. В файл SettingsStorageCommand.cs добавьте следующие директивы using:

   ```
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Settings;
   using Microsoft.VisualStudio.Shell.Settings;
   using System.Windows.Forms;
   ```

2. В `MenuItemCallback` удалите текст метода и добавьте следующие строки, чтобы получить хранилище параметров конфигурации:

   ```
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
   ```

    @No__t_0 является управляемым вспомогательным классом для службы <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager>.

3. Теперь Узнайте, установлены ли средства Windows Phone. Код должен выглядеть следующим образом:

   ```
   private void MenuItemCallback(object sender, EventArgs e)
   {
       SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
       SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
       bool arePhoneToolsInstalled = configurationSettingsStore.CollectionExists(@"InstalledProducts\Microsoft Windows Phone Developer Tools");
       string message = "Microsoft Windows Phone Developer Tools: " + arePhoneToolsInstalled;
       MessageBox.Show(message);
   }
   ```

4. Протестируйте код. Выполните сборку решения и запустите отладку.

5. В экспериментальном экземпляре в меню **Сервис** выберите команду **вызвать сеттингссторекомманд**.

    Должно отобразиться окно с сообщением **Microsoft Windows Phone средства для разработчиков:** , за которым следует **значение true** или **false**.

   В Visual Studio хранилище параметров сохраняется в системном реестре.

#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Использование редактора реестра для проверки параметров конфигурации

1. Откройте файл Regedit. exe.

2. Перейдите к HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts \\.

    > [!NOTE]
    > Убедитесь, что вы просматриваете ключ, содержащий \14.0Exp_Config\, а не \14.0_Config \\. При запуске экспериментального экземпляра Visual Studio параметры конфигурации находятся в кусте реестра ««Exp_Config».

3. Разверните узел продукты \Инсталлед \. Если сообщение на предыдущих шагах имеет **значение Microsoft Windows Phone средства для разработчиков установлено: true**, то \инсталлед Products \ должен содержать узел Средства для разработчиков Microsoft Windows Phone. Если сообщение имеет **значение Microsoft Windows Phone средства для разработчиков установлен: false**, то продукты \инсталлед \ не должны содержать узел Средства для разработчиков Microsoft Windows Phone.
