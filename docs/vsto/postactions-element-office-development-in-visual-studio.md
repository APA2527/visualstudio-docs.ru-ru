---
title: '&lt;&gt;элемент «действия» (разработка решений Office)'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postActions> element
- postActions element
- <postActions> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: da0c3ee640d7ae4ec1b61df7a60893a7e1428cd2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879440"
---
# <a name="ltpostactionsgt-element-office-development"></a>&lt;&gt;элемент «действия» (разработка решений Office)
  Элемент `postActions` пространства имен `vstav3` содержит все элементы `postAction` , описывающие действия после развертывания, которые выполняются после установки решений Office.

## <a name="syntax"></a>Синтаксис

```xml
<postActions>
  <postAction>
    <entryPoint>
    </entryPoint>
    <postActionData>
    </postActionData>
  </postAction>
</postActions>
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 Элемент `postActions` является необязательным и находится в пространстве имен `vstav3` . В манифесте приложения определен только один элемент `postActions` .

 У элемента `postActions` нет атрибутов.

 Объект`postActions` имеет следующий элемент.

### <a name="postaction"></a>postAction
 Необязательный элемент. Роль `postAction` элемента в `vstav3` пространстве имен определена в [ элементе&#60;&#62; действия &#40;разработки Office в Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md).

## <a name="post-deployment-action-example"></a>Пример действия, выполняемого после развертывания

### <a name="description"></a>Описание
 В приведенном ниже примере кода показан элемент `postActions` манифеста приложения для решения Office, развертываемого с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Этот пример кода является частью большого примера, приведенного в разделе [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Код

```xml
<vstav3:postActions>
  <vstav3:postAction>
    <vstav3:entryPoint
      class="PostDeploymentAction.PostDeploymentActionSample">
      <assemblyIdentity
        name="PostDeploymentAction"
        version="1.0.0.0"
        language="neutral"
        processorArchitecture="msil" />
    </vstav3:entryPoint>
    <vstav3:postActionData>
    </vstav3:postActionData>
  </vstav3:postAction>
</vstav3:postActions>
```

## <a name="see-also"></a>См. также

- [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)
- [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)
