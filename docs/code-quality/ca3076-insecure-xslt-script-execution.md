---
title: CA3076. Выполнение небезопасного скрипта XSLT
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f98b022aef49a4d98ad4864793aa55732f8de6c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541094"
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076. Выполнение небезопасного скрипта XSLT

|||
|-|-|
|TypeName|InsecureXSLTScriptExecution|
|CheckId|CA3076|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

При небезопасном выполнении XSLT в приложениях .NET обработчик может разрешить недоверенные ссылки URI, раскрывающие конфиденциальную информацию злоумышленникам, что приведет к атакам типа "отказ в обслуживании" и межсайтовым атакам. Дополнительные сведения см. в разделе [Considerations(.NET Guide) безопасности XSLT](/dotnet/standard/data/xml/xslt-security-considerations).

## <a name="rule-description"></a>Описание правила

**XSLT** — это стандарт консорциума W3C для преобразования данных XML. XSLT обычно используется для записи таблиц стилей для преобразования данных XML в другие форматы, такие как HTML, текст фиксированной длины, текст с разделителями запятыми или другой формат XML. Хотя эта возможность по умолчанию запрещена, вы можете включить ее для проекта.

Чтобы вам не нужно предоставлять уязвимая зона, это правило активируется каждый раз, когда XslCompiledTransform.<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> Получает небезопасную комбинацию экземпляров <xref:System.Xml.Xsl.XsltSettings> и <xref:System.Xml.XmlResolver>, которая допускает обработку вредоносных скриптов.

## <a name="how-to-fix-violations"></a>Устранение нарушений

- Замените небезопасный аргумент XsltSettings.<xref:System.Xml.Xsl.XsltSettings.Default%2A> или с экземпляром, отключил документа функции и выполнением скриптов.

- Замените аргумент <xref:System.Xml.XmlResolver> на NULL или экземпляр <xref:System.Xml.XmlSecureResolver> .

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Отключайте правило этого предупреждения, только если уверены, что входные данные получены из доверенного источника.

## <a name="pseudo-code-examples"></a>Примеры псевдокода

### <a name="violation-that-uses-xsltsettingstrustedxslt"></a>Нарушение, использующий XsltSettings.TrustedXslt

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
         void TestMethod()
        {
             XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
             var settings = XsltSettings.TrustedXslt;
             var resolver = new XmlUrlResolver();
             xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn
        }
    }
}
```

### <a name="solution-that-uses-xsltsettingsdefault"></a>Решение, использующее XsltSettings.Default

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        void TestMethod()
        {
            XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
            var settings = XsltSettings.Default;
            var resolver = new XmlUrlResolver();
            xslCompiledTransform.Load("testStylesheet", settings, resolver);
        }
    }
}
```

### <a name="violationmdashdocument-function-and-script-execution-not-disabled"></a>Нарушение&mdash;документа функции и выполнением скриптов не отключена

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod(XsltSettings settings)
        {
            try
            {
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
                var resolver = new XmlUrlResolver();
                xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn
            }
            catch { throw; }
            finally { }
        }
    }
}
```

### <a name="solutionmdashdisable-document-function-and-script-execution"></a>Решение&mdash;отключить выполнение функции и скрипт документа

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod(XsltSettings settings)
        {
            try
            {
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
                settings.EnableDocumentFunction = false;
                settings.EnableScript = false;
                var resolver = new XmlUrlResolver();
                xslCompiledTransform.Load("testStylesheet", settings, resolver);
            }
            catch { throw; }
            finally { }
        }
    }
}
```

## <a name="see-also"></a>См. также

- [Рекомендации по безопасности XSLT (руководство по .NET)](/dotnet/standard/data/xml/xslt-security-considerations)