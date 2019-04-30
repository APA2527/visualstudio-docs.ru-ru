---
title: Подписывание пакетов VSIX | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9fabe2931310b97f0c0864ea77ceef024f0e57cd
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447207"
---
# <a name="signing-vsix-packages"></a>Подписывание пакетов VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Расширения сборки не обязательно должны быть подписаны, прежде чем они могут работать в Visual Studio, но рекомендуется сделать это.  
  
 Если вы хотите защитить ваше расширение и убедитесь, что оно не было изменено, можно добавить цифровую подпись в пакет VSIX. При подписании VSIX, установщик VSIX отобразит сообщение о том, что он подписан, а также дополнительные сведения о сама подпись. Если содержимое VSIX были изменены, а VSIX снова не подписана, установщик VSIX покажет, что подпись не является допустимым. Установка не прекращается, но пользователь получает предупреждение.  
  
> [!IMPORTANT]
> Начиная с 2015 пакетов VSIX, подписываются с использованием ничего, кроме SHA256 шифрования будет определяться как имеющий недопустимую подпись. Установка VSIX не блокируется, но пользователь отображается предупреждение.  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>Подписи VSIX с VSIXSignTool  
 SHA256 шифрование, подписи средство, доступное из [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) на сайте nuget.org в [VsixSignTool](http://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).  
  
#### <a name="to-use-the-vsixsigntool"></a>Чтобы использовать VSIXSignTool  
  
1. Добавление в проект VSIX.  
  
2. Щелкните правой кнопкой мыши узел проекта в обозревателе решений, выбрав **добавить &#124; управление пакетами NuGet**.  Дополнительные сведения о NuGet и добавлении NuGet пакетов см. в разделе [Обзор NuGet](http://docs.nuget.org/) и [управление пакетами NuGet с помощью диалогового окна](http://docs.nuget.org/Consume/Package-Manager-Dialog).  
  
3. Поиск VSIXSignTool из VisualStudioExtensibility и установите пакет NuGet.  
  
4. Теперь можно запустить VSIXSignTool из расположения локальные пакеты проекта. См. справку командной строки средства для подписывания сценария (VSIXSignTool.exe /?).  
  
   Например подписать с помощью сертификата, защищенный файл пароля:  
  
   VSIXSignTool.exe sign /f \<certfile> /p \<password> \<VSIXfile>  
  
## <a name="see-also"></a>См. также  
 [Доставка расширений Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
