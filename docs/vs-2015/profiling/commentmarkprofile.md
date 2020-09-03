---
title: CommentMarkProfile | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- CommentMarkProfile
- CommentMarkProfileA
ms.assetid: 33ccff45-c33a-4672-b41f-5b317b848cd1
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 750ce3cbcae593aee315998ec8b205a71e004d41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543054"
---
# <a name="commentmarkprofile"></a>CommentMarkProfile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Функция `CommentMarkProfile` вставляет числовую метку и текстовую строку в VSP-файл. Чтобы вставить метку и комментарий, необходимо включить профилирование для потока, содержащего функцию `CommentMarkProfile`.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkProfile(  
                                   long lMarker,   
                                   LPCTSTR szComment);  
```  
  
#### <a name="parameters"></a>Параметры  
 `lMarker`  
  
 Вставляемая числовая метка. Метка должна быть больше или равна нулю (0).  
  
 `szComment`  
  
 Указатель на вставляемую текстовую строку. Длина строки не должна превышать 256 символов, включая маркер конца строки NULL.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Функция информирует об успехе или неудаче с помощью перечисления **PROFILE_COMMAND_STATUS**. Может возвращаться одно из следующих значений:  
  
|Перечислитель|Описание|  
|----------------|-----------------|  
|MARK_ERROR_MARKER_RESERVED|Значение параметра меньше или равно нулю. Эти значения зарезервированы. Метка и комментарий не записываются.|  
|MARK_ERROR_MODE_NEVER|На момент вызова функции был установлен режим профилирования NEVER. Метка и комментарий не записываются.|  
|MARK_ERROR_MODE_OFF|На момент вызова функции был установлен режим профилирования OFF. Метка и комментарий не записываются.|  
|MARK_ERROR_NO_SUPPORT|В данном контексте метки не поддерживаются. Метка и комментарий не записываются.|  
|MARK_ERROR_OUTOFMEMORY|Недостаточно памяти для записи события. Метка и комментарий не записываются.|  
|MARK_TEXTTOOLONG|Длина строки превышает 256 символов. Строка комментария усекается. Метка и комментарий записываются.|  
|MARK_OK|В случае успеха возвращается MARK_OK.|  
  
## <a name="remarks"></a>Примечания  
 Для потока, содержащего функцию метки профиля, должно быть включено состояние профилирования, чтобы вставить метку и комментарий с помощью команды VSInstr Mark или функций (CommentMarkAtProfile, CommentMarkProfile или MarkProfile).  
  
 Метки профилирования имеют глобальную область видимости. Например, вставленную в любом потоке метку профиля можно использовать для обозначения начала или конца сегмента данных в любом потоке в VSP-файле.  
  
> [!IMPORTANT]
> Метод CommentMarkProfile можно использовать только при профилировании с инструментированием.  
  
## <a name="net-framework-equivalent"></a>Эквивалент .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>Сведения о функции  
  
|Элемент|Значение|  
|-|-|  
|**Заголовок**|Включение VSPerf.h|  
|**Библиотека**|Использование VSPerf.lib|  
|**Юникод**|Функция реализована как `CommentMarkProfileW` (Юникод) и `CommentMarkProfileA` (ANSI).|  
  
## <a name="example"></a>Пример  
 В приведенном ниже коде демонстрируется вызов функции CommentMarkProfile. Предполагается, что в этом примере используется строковый макрос Win32 и параметры компилятора для Юникода, чтобы определить, вызывается ли в коде функция [!INCLUDE[vcpransi](../includes/vcpransi-md.md)].  
  
```  
void ExerciseCommentMarkProfile()  
{  
    // Declare and initalize variables to pass to   
    // CommentMarkProfile.  The values of these   
    // parameters are assigned based on the needs   
    // of the code; and for the sake of simplicity  
    // in this example, the variables are assigned  
    // arbitrary values.  
    long markId = 01;  
    TCHAR * markText = TEXT("Exercising CommentMarkProfile...");  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare MarkOperationResult Enumerator.    
    // Holds return value from call to CommentMarkProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    markResult = CommentMarkProfile(  
        markId,  
        markText);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("CommentMarkProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API профилировщика Visual Studio (native)](../profiling/visual-studio-profiler-api-reference-native.md)
