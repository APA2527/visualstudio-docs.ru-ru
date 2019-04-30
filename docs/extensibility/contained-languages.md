---
title: Содержащихся языков | Документация Майкрософт
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e45fb303c840ec66655e3900dcea3d57b75c7da7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62891372"
---
# <a name="contained-languages"></a>Содержащихся языков

*Содержащихся языков* языков, которые содержатся в других языках. Например, HTML в [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] страницы могут содержать [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] или [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] сценариев. Архитектура двумя языка является обязательным для *.aspx* возможностях редактор файлов для обеспечения IntelliSense, выделение цветом и редактирования HTML и язык сценариев.

## <a name="implementation"></a>Реализация

Наиболее важным интерфейс необходимо реализовать для содержащихся языков <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> интерфейс. Этот интерфейс реализуется в любом языке, могут размещаться в основной язык. Он предоставляет доступ к службе языка палитры, фильтр представления текста и идентификатор службы основного языка. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> Позволяет создавать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> интерфейс. Ниже показано, как реализовать содержащегося языка:

1. Используйте `QueryService()` для получения языка, код службы и идентификатор интерфейса <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>.

2. Чтобы создать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> интерфейс, вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> метод. Передайте <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> интерфейса, один или несколько [элементов идентификаторы](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>)и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> интерфейс.

3. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> Интерфейс, который является объектом координатора буфера текста, предоставляет основные службы, которые необходимы для сопоставления расположения в первичный файл в буфер вторичного языка.

     Например, в одном *.aspx* файл, первичный файл содержит ASP, HTML и весь код, который содержится. Однако вторичный буфер включает содержащийся внутри код вместе с определений классов для создания файла допустимый код вторичный буфер. Координатор буфера выполняет работу по координации изменений из одного буфера в другой.

4. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> Метод, который является основным языком, сообщает координатор буфера текста внутри содержащего его буфера сопоставляется соответствующий текст во вторичном буфере.

     Язык передает массив <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> структуру, которая в настоящее время включает только основной и дополнительный диапазон.

5. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> Метод и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> метод предоставления сопоставление из первичного буфера во вторичный и наоборот.