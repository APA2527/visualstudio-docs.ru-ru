---
title: Контекст документа | Документация Майкрософт
description: Сведения о контексте документа в отладке Visual Studio, которая представляет собой расположение в исходном файле или расположение в исходном документе для контекста кода.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: be2e5e168b232f120a22e7e4b39352008fee7418
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840760"
---
# <a name="document-context"></a>Контекст документа
При [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладке — *контекст документа*:

- Представляет расположение в исходном файле. Для языков, где исходный файл может отсутствовать, контекст документа определяет позицию в документе, обычно создаваемую средой выполнения. Например, обработчик сценариев может создать документ из скрипта. Дополнительные сведения см. в разделе [расположение документа](../../extensibility/debugger/document-position.md).

- Описывает расположение в исходном документе, соответствующее контексту кода. Обработчик символов сопоставляет контекст кода с контекстом документации, используя сведения, созданные компилятором или интерпретатором.

- Реализуется с помощью интерфейса [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) .

## <a name="see-also"></a>См. также раздел
- [Контекст кода](../../extensibility/debugger/code-context.md)
- [Поставщик символов](../../extensibility/debugger/symbol-provider.md)
- [Интерфейсы поставщика символов](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)
