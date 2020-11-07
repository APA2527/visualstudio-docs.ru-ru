---
title: Настройка зоны безопасности (приложение ClickOnce)
description: Сведения о настройке разрешений управления доступом для кода для приложения ClickOnce, которое начинается с базового набора разрешений в конструкторе проектов.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, security settings
- code access security, ClickOnce applications
- security zones, ClickOnce applications
ms.assetid: d3dac454-518a-44d7-a76e-ccb7b9c3a150
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d2e8b49f833b5dd91dc6379d2a015d41a9679afe
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349780"
---
# <a name="how-to-set-a-security-zone-for-a-clickonce-application"></a>Практическое руководство. Установка зоны безопасности для ClickOnce-приложения
При установке разрешений управления доступом для кода для приложения ClickOnce необходимо начать с базового набора разрешений на странице **Безопасность****конструктора проектов**.

 В большинстве случаев вы также можете выбрать зону **Интернет** , содержащую ограниченный набор разрешений, или зону **Локальная интрасеть** , содержащую более обширный набор разрешений. Если приложению требуются настраиваемые разрешения, можно предоставить их, выбрав зону безопасности **Настраиваемая** . Дополнительные сведения о задании настраиваемых разрешений см. в разделе [How to: Set Custom Permissions for a ClickOnce Application](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).

### <a name="to-set-a-security-zone"></a>Задание зоны безопасности

1. Выбрав проект в **Обозреватель решений** , в меню **проект** выберите пункт **Свойства**.

2. Перейдите на вкладку **Безопасность** .

3. Установите флажок **Включить параметры безопасности ClickOnce-приложений** .

4. Выберите переключатель **Это приложение с частичным доверием** .

     Элементы управления в разделе **Параметры безопасности ClickOnce-приложений** включены.

5. В раскрывающемся списке **Зона, из которой приложение будет установлено** выберите зону безопасности.

## <a name="see-also"></a>См. также
- [Как задать пользовательские разрешения для приложения ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Защита приложений ClickOnce](../deployment/securing-clickonce-applications.md)
- [Управление доступом для кода для приложений ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
