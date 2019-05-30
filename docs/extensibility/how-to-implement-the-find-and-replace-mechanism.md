---
title: Практическое руководство. Реализация поиска и замены механизм | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 478d3e155486aa146d28c6c9c9b9246fd5d69569
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351949"
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>Практическое руководство. Реализовать найти и заменить механизм

Visual Studio предоставляет два способа реализации поиска и замены. Рекомендуется передать образ текста в оболочку и позвольте ей выполнить поиск, выделение и замену текста. Это позволяет пользователям указывать несколько текстовых диапазонов. Кроме того пакет VSPackage может контролирует эти функциональные возможности, сам. В обоих случаях необходимо уведомить оболочки о текущего целевого объекта и целевые объекты для всех открытых документах.

## <a name="to-implement-findreplace"></a>Для реализации поиска и замены

1. Реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> интерфейса на одном из объектов, возвращенных свойства рамки <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocView> или <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocData>. Если вы создаете настраиваемый редактор, следует реализовать этот интерфейс как часть класса настраиваемого редактора.

2. Используйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A> метод для указания параметров, которые ваш редактор поддерживает и указать, реализует ли поиск образа.

   Если ваш редактор поддерживает поиск изображений, реализовать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>.

   В противном случае реализация <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>.

3. Если вы реализуете <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> методы, чтобы упростить поиск задач путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> интерфейс.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>