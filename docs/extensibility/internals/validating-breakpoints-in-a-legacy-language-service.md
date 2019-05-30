---
title: Проверка точек останова в языковой службе прежних версий | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 177b0bb3fddebab6518a851bf8ce4c4d34d43897
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324577"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Проверка точек останова в языковой службе прежних версий
Точка останова указывает, что пока они выполняются в отладчике в определенной точке должен остановить выполнение программы. Пользователя можно установить точку останова в любую строку в исходном файле, поскольку редактор не имеет сведений о того, что составляет является допустимым расположением точки останова. При запуске отладчика, все помеченные точки останова (называемые ожидающих точек останова) привязаны в соответствующее место в выполняющейся программе. В то же время, которые проверяются точки останова, чтобы убедиться, что эти файлы обозначают допустимый код расположения. Например точки останова на комментарий является недопустимым, так как отсутствует код в этом расположении в исходном коде. Отладчик отключает недопустимый точки останова.

 Поскольку служба языка поддерживает отображение исходного кода, он может проверять точки останова перед запуском отладчика. Можно переопределить <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> метод для возврата диапазон, указав допустимое расположение для точки останова. Положение точки останова по-прежнему проверки при запуске отладчика, но пользователь уведомляется недопустимый точек останова, не дожидаясь отладчик должен загружать.

## <a name="implementing-support-for-validating-breakpoints"></a>Реализация поддержки для проверки точек останова

- <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> Метод получает позицию точки останова. Реализация необходимо решить, ли расположение является допустимым и указать это, возвращая диапазон текста, который определяет код, связанный с позицию в строке точку останова.

- Вернуть <xref:Microsoft.VisualStudio.VSConstants.S_OK> Если расположение является допустимым, или <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> если оно является недопустимым.

- Если точка останова задана в допустимый диапазон текста выделяются точки останова.

- Если точка останова является недопустимым, появится сообщение об ошибке в строке состояния.

### <a name="example"></a>Пример
 В этом примере показана реализация <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> метод, который вызывает средство синтаксического анализа, чтобы получить диапазон кода (если таковые имеются) в указанном расположении.

 В этом примере предполагается, что вы добавили `GetCodeSpan` метод <xref:Microsoft.VisualStudio.Package.AuthoringSink> класс, который проверяет диапазон текста и возвращает `true` Если это расположение действительной точке останова.

```csharp
using Microsoft VisualStudio;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    class TestLanguageService : LanguageService
    {
        public override int ValidateBreakpointLocation(IVsTextBuffer buffer,
                                                       int line,
                                                       int col,
                                                       TextSpan[] pCodeSpan)
        {
            int retval = VSConstants.S_FALSE;
            if (pCodeSpan != null)
            {
                // Initialize span to current line by default.
                pCodeSpan[0].iStartLine = line;
                pCodeSpan[0].iStartIndex = col;
                pCodeSpan[0].iEndLine = line;
                pCodeSpan[0].iEndIndex = col;
            }

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
                                                              ParseReason.CodeSpan,
                                                              null);
                        req.Scope = this.ParseSource(req);
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;

                        TextSpan span = new TextSpan();
                        if (sink.GetCodeSpan(out span))
                        {
                            pCodeSpan[0] = span;
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

## <a name="see-also"></a>См. также
- [Функции языковой службы прежних версий](../../extensibility/internals/legacy-language-service-features1.md)