---
title: Практическое руководство. Добавление маркеров стандартного текста | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 912d5d7a225520fc825d832bf73f5cfc733a9486
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436019"
---
# <a name="how-to-add-standard-text-markers"></a>Практическое руководство. Добавление маркеров стандартного текста
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Используйте следующую процедуру для создания одного из типов маркеров текст по умолчанию, в состав [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] базовым редактором.  
  
### <a name="to-create-a-text-marker"></a>Для создания текстового маркера  
  
1. В зависимости от того, используется ли один или два - мерный системы координат, вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> метод или <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> метод для создания нового текстового маркера.  
  
     При таком вызове метода, укажите тип маркера, диапазон текста, чтобы создать маркер и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейс. Затем этот метод возвращает указатель на только что созданный текстового маркера. Типы маркеров, взяты из <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> перечисления. Укажите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейс, если вы хотите быть в курсе событий маркера.  
  
    > [!NOTE]
    > Создайте текстовые метки на только основной поток пользовательского интерфейса. Базовый редактор зависит от содержимого текстового буфера для создания меток текста и текстовый буфер не является потокобезопасным.  
  
## <a name="adding-a-custom-command"></a>Добавление пользовательской команды  
 Реализация `IVsTextMarkerClient` интерфейс и передачи указателя на него из маркера улучшает поведение метки несколькими способами. Во-первых это позволяет обеспечить советы для метку и для выполнения команд. Это также позволяет получать уведомления о событиях для отдельных маркеров и для создания пользовательского контекстного меню через маркер. Используйте следующую процедуру для добавления пользовательской команды в контекстное меню маркера.  
  
#### <a name="to-add-a-custom-command-to-the-context-menu"></a>Добавление пользовательской команды в контекстное меню  
  
1. Перед отображением контекстного меню, среда вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> метода и передает проблема указатель на текстовый маркер и номер элемента команды в контекстном меню.  
  
     Примеры, характерные для точки останова команды в контекстном меню: **удалить точку останова** через **новую точку останова**, как показано на следующем снимке экрана.  
  
     ![Маркер контекстного меню](../extensibility/media/vsmarkercontextmenu.gif "vsMarkercontextmenu")  
  
2. Передайте некоторый текст, определяющее имя пользовательской команды. Например **удалить точку останова** может быть пользовательской команды, если среды не уже предоставил его. Можно также передать обратно ли команда поддерживается, доступна и включена, и/или переключить Вкл / Выкл. Среда использует эти сведения для отображения пользовательской команды в контекстном меню в правильный способ использования.  
  
3. Чтобы выполнить команду, среда вызывает метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> метод, передав указатель для текстового маркера и количество команда, выбранная в контекстном меню.  
  
     Используйте эти сведения из этого вызова для выполнения, определяет вашей пользовательской команды нужные действия текстового маркера.  
  
## <a name="see-also"></a>См. также  
 [С помощью меток текста с помощью API прежних версий](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Практическое руководство. Реализовать маркеры ошибок](../extensibility/how-to-implement-error-markers.md)   
 [Практическое руководство. Создание настраиваемых текстовых маркеров](../extensibility/how-to-create-custom-text-markers.md)   
 [Практическое руководство. Использование текстовых маркеров](../extensibility/how-to-use-text-markers.md)
