---
title: Поддержка веб-сайтов | Документация Майкрософт
description: Сведения о системах проектов веб-сайтов, которые создаются путем добавления шаблонов и атрибутов регистрации в существующую систему проектов.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 141e4acf7db61130de859f38891670e69d3bd640
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940026"
---
# <a name="web-site-support"></a>Поддержка веб-сайтов
Система проектов веб-сайтов — это система проектов, которая создает веб-проекты. Веб-проекты, в свою очередь, создают веб-приложения. Проект веб-сайта создает один исполняемый файл для каждой веб-страницы, имеющей связанный код. Дополнительные исполняемые файлы создаются из файлов исходного кода в папке/App_Code.

 Системы проектов веб-сайтов создаются путем добавления шаблонов и атрибутов регистрации в существующую систему проектов. Один из этих атрибутов выбирает поставщик IntelliSense для языка. Реализация поставщика IntelliSense обрабатывает ссылки и вызывает компилятор языка при запросе смарт-страницы, которая не кэшируется.

 Компилятор языка, используемый для компиляции веб-страниц, должен быть зарегистрирован в [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)] . Можно использовать [ \<compiler> элемент](/dotnet/framework/configure-apps/file-schema/compiler/compiler-element) в файле Web.config для регистрации компилятора, как показано в следующем примере:

```
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>
```

## <a name="in-this-section"></a>В этом разделе
- [Шаблоны поддержки веб-сайтов](../../extensibility/internals/web-site-support-templates.md)

 Список шаблонов, которые можно использовать для создания новых проектов веб-сайтов и связанных элементов.

- [Атрибуты поддержки веб-сайтов](../../extensibility/internals/web-site-support-attributes.md)

 Представляет атрибуты регистрации, соединяющие проект веб-сайта с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)] .

## <a name="related-sections"></a>Связанные разделы
- [Веб-проекты](../../extensibility/internals/web-projects.md)

 Содержит обзор двух типов веб-проектов, проектов веб-сайтов и проектов веб-приложений.
