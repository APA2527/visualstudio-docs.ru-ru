---
title: IDebugPortEx2::LaunchSuspended | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d554c4906867ca28cfab295ebea80cca15dcc879
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66209019"
---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
Запускает исполняемый файл.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT LaunchSuspended( 
   LPCOLESTR        pszExe,
   LPCOLESTR        pszArgs,
   LPCOLESTR        pszDir,
   BSTR             bstrEnv,
   DWORD            hStdInput,
   DWORD            hStdOutput,
   DWORD            hStdError,
   IDebugProcess2** ppPortProcess
);
```

```csharp
int LaunchSuspended( 
   string             pszExe,
   string             pszArgs,
   string             pszDir,
   string             bstrEnv,
   uint               hStdInput,
   uint               hStdOutput,
   uint               hStdError,
   out IDebugProcess2 ppPortProcess
);
```

## <a name="parameters"></a>Параметры
`pszExe`\
[in] Имя исполняемого файла для запуска. Это может быть полный путь или относительно рабочего каталога, указанного в `pszDir` параметра.

`pszArgs`\
[in] Аргументы для передачи в исполняемый файл. Может иметь значение null, если аргументы не используются.

`pszDir`\
[in] Имя рабочего каталога, используемого исполняемого объекта. Может иметь значение null, если нет рабочего каталога является обязательным.

`bstrEnv`\
[in] Блок среды нулем строк, следуют дополнительные символ конца строки NULL.

`hStdInput`\
[in] Дескриптор альтернативного входного потока. Может быть равен 0, если перенаправление не требуется.

`hStdOutput`\
[in] Дескриптор Альтернативный выходной поток. Может быть равен 0, если перенаправление не требуется.

`hStdError`\
[in] Обработка в поток вывода альтернативного ошибки. Может быть равен 0, если перенаправление не требуется.

`ppPortProcess`\
[out] Возвращает [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) объект, представляющий запущенный процесс.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод должен быть запущен процесс, поэтому он приостанавливается и не выполняет никакой код. [ResumeProcess для](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) вызывается метод, чтобы возобновить процесс.

 Также можно запустить программу из модуля отладки. Дополнительные сведения см. в разделе [запуск программы](../../../extensibility/debugger/launching-a-program.md).

## <a name="see-also"></a>См. также
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)
- [Запуск программы](../../../extensibility/debugger/launching-a-program.md)