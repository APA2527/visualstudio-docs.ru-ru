---
title: Поддержка окно видимых переменных в языковой службе прежних версий | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2842cb7a11765f0d460681dee0187c62ff31061c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309830"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Поддержка окна видимых переменных в языковой службе прежних версий
**"Видимые"** окне отображаются выражения, такие как переменные и параметры, которые находятся в области, при приостановке отлаживаемой программы (из-за точки останова или исключение). Выражения могут включать переменные, локальные или глобальные и параметры, которые были изменены в локальной области. **"Видимые"** окна можно также включить экземпляров класса, структуры или другого типа. Все, что позволяет оценить вычислитель выражений потенциально могут быть отображены в **"Видимые"** окна.

 Managed package framework (MPF) не поддерживает прямую поддержку **"Видимые"** окна. Тем не менее если переопределить <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> метод, может возвращать список выражений должен обязательно присутствовать в **"Видимые"** окна.

## <a name="implementing-support-for-the-autos-window"></a>Реализация поддержки для окна "Видимые"
 Все что нужно сделать для поддержки **"Видимые"** окно заключается в реализации <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> метод в <xref:Microsoft.VisualStudio.Package.LanguageService> класса. Реализация необходимо решить, заданную расположением в исходном файле, которые должны отображаться выражения в **"Видимые"** окна. Метод возвращает список строк, в которых каждая строка представляет одно выражение. Возвращаемое значение, равное <xref:Microsoft.VisualStudio.VSConstants.S_OK> указывает, что список содержит выражения, хотя <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> указывает, что отсутствуют выражения для отображения.

 Фактический выражений, возвращенных являются имена переменных или параметров, которые отображаются в этом расположении, в коде. Эти имена передаются средству оценки выражений для получения значения и типы, которые затем отображаются в **"Видимые"** окна.

### <a name="example"></a>Пример
 В следующем примере показана реализация <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> метод, который возвращает список выражений из <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод, используя причину синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason>. Каждое из выражений упаковывается как `TestVsEnumBSTR` , реализующий <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> интерфейс.

 Обратите внимание, что `GetAutoExpressionsCount` и `GetAutoExpression` методы являются пользовательские методы на `TestAuthoringSink` объекта и были добавлены для поддержки в этом примере. Они представляют один из способов, в какие выражения, добавляемые `TestAuthoringSink` объекта средством синтаксического анализа (путем вызова <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> метода) можно использовать за пределами средство синтаксического анализа.

```csharp
using Microsoft.VisualStudio;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override int GetProximityExpressions(IVsTextBuffer buffer,
                                                    int line,
                                                    int col,
                                                    int cLines,
                                                    out IVsEnumBSTR ppEnum)
        {
            int retval = VSConstants.E_NOTIMPL;
            ppEnum = null;
            if (buffer != null)
            {
                IVsTextLines textLines = buffer as IVsTextLines;
                if (textLines != null)
                {
                    Source src = this.GetSource(textLines);
                    if (src != null)
                    {
                        TokenInfo tokenInfo = new TokenInfo();
                        string text = src.GetText();
                        ParseRequest req = CreateParseRequest(src,
                                                              line,
                                                              col,
                                                              tokenInfo,
                                                              text,
                                                              src.GetFilePath(),
                                                              ParseReason.Autos,
                                                              null);
                        req.Scope = this.ParseSource(req);
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;

                        retval = VSConstants.S_FALSE;
                        int spanCount = sink.GetAutoExpressionsCount();
                        if (spanCount > 0) {
                            TestVsEnumBSTR bstrList = new TestVsEnumBSTR();
                            for (int i = 0; i < spanCount; i++)
                            {
                                TextSpan span;
                                sink.GetAutoExpression(i, out span);
                                string expression = src.GetText(span.iStartLine,
                                                                span.iStartIndex,
                                                                span.iEndLine,
                                                                span.iEndIndex);
                                bstrList.AddString(expression);
                            }
                            ppEnum = bstrList;
                            retval = VSConstants.S_OK;
                        }
                    }
                }
            }
            return retval;
        }
    }
}
```