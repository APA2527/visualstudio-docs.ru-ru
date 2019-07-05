---
title: Использование RDT_ReadLock | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c11cee4c1f8c150fc8bcf42b3dbc1a193d3441a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341359"
---
# <a name="rdtreadlock-usage"></a>Использование RDT_ReadLock

[_VSRDTFLAGS. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) флаг, предоставляющий логику для блокировка документа на в выполняющихся документа таблицы (RDT), который является список всех документов, открытых в настоящий момент в Интегрированной среде разработки Visual Studio. Этот флаг определяет при открытии документов и является ли документ видимым в пользовательском интерфейсе или принудительное незаметно в памяти.

Как правило, используется [_VSRDTFLAGS. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) когда верно одно из следующих:

- Требуется открыть документ незаметно и только для чтения, но он еще не установлено, что <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> должны отвечать за его.

- Предоставить пользователю будет предложено сохранить документ, который незаметно был открыт, прежде чем пользователь, он отображается в пользовательском Интерфейсе и затем была предпринята попытка закрыть его.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Как управлять видимым и невидимым документов

Когда пользователь открывает документ в пользовательском Интерфейсе <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> владелец документа должно быть установлено и [_VSRDTFLAGS. RDT_EditLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_EditLock>) должен быть установлен флаг. Если не <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> владелец может быть установлено, а затем документа не будут сохранены, когда пользователь щелкает **сохранить все** или закрытии интегрированной среды разработки. Это означает, что если документ открыт незаметно там, где он изменен в памяти, и пользователю будет предложено сохранить документ при завершении работы или при сохранении Если **сохранить все** выбирается, а затем `RDT_ReadLock` нельзя использовать. Вместо этого необходимо использовать `RDT_EditLock` и зарегистрируйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> при [__VSREGDOCLOCKHOLDER. RDLH_WeakLockHolder](<xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER.RDLH_WeakLockHolder>) флаг.

## <a name="rdteditlock-and-document-modification"></a>RDT_EditLock и изменение документа

Предыдущие упоминалось флаг указывает, что даст невидимым Открытие документа его `RDT_EditLock` при открытии документа пользователем в видимом **DocumentWindow**. В таких случаях пользователю предоставляется **Сохранить** приглашение по видимых **DocumentWindow** закрыт. `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel` реализаций, использующих <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> служба изначально работать, только если `RDT_ReadLock` берется (т. е. когда документ открыт незаметно для анализа информации о). Позже, если необходимо изменить его, затем блокировки будет обновлена до слабую **RDT_EditLock**. Если пользователь затем открывает документ в видимом **DocumentWindow**, `CodeModel`на слабый `RDT_EditLock` освобождается.

Если пользователь закрывает **DocumentWindow** и выбирает **нет** когда будет предложено сохранить открытый документ, то `CodeModel` реализация удаляет всю информацию в документе и заново не откроет документ с диска незаметно в следующий раз дополнительные информация необходима для документа. Тонкость такое поведение является экземпляром, где пользователь открывает **DocumentWindow** невидимым открытого документа, его изменение, закрывает его и затем выбирает **нет** когда будет предложено сохранить документ. В данном случае, если документ имеет `RDT_ReadLock`, затем документ фактически не закрывается, и измененный документ остается открытым незаметно в памяти, несмотря на то, что пользователь выбрал не сохранять документ.

Если невидимым Открытие документа использует слабую `RDT_EditLock`, то он возвращает его блокировки, когда пользователь открывает документ, визуально и нет других блокировки удерживаются. Когда пользователь закрывает **DocumentWindow** и выбирает **нет** при появлении запроса на сохранение документа, затем документ должен быть закрыт из памяти. Это означает, что невидимый клиента должны прослушивать события RDT для отслеживания этого экземпляра. В следующий раз документа является обязательным, его нужно открыть заново.