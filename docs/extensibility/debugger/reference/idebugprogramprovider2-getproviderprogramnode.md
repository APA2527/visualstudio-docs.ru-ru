---
title: IDebugProgramProvider2::GetProviderProgramNode | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 594fef8a83c01b4bad4d47fdb206d64e445ad515
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65459019"
---
# <a name="idebugprogramprovider2getproviderprogramnode"></a>IDebugProgramProvider2::GetProviderProgramNode
Возвращает узел, программы для конкретной программы.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetProviderProgramNode(
   PROVIDER_FLAGS       Flags,
   IDebugDefaultPort2*  pPort,
   AD_PROCESS_ID        processId,
   REFGUID              guidEngine,
   UINT64               programId,
   IDebugProgramNode2** ppProgramNode
);
```

```csharp
int GetProviderProgramNode(
   enum_PROVIDER_FLAGS    Flags,
   IDebugDefaultPort2     pPort,
   AD_PROCESS_ID          ProcessId,
   ref Guid               guidEngine,
   ulong                  programId,
   out IDebugProgramNode2 ppProgramNode
);
```

## <a name="parameters"></a>Параметры
 `Flags`\

 [in] Сочетание флагов из [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) перечисления. Для этого вызова типичны следующие флаги:

|Flag|Описание|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|Вызывающий объект выполняется на удаленном компьютере.|
|`PFLAG_DEBUGGEE`|Вызывающий объект находится в состоянии отладки (Дополнительные сведения о маршалинга будет возвращаться для каждого узла).|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Вызывающий объект был подключен к, но не запускается в отладчике.|

 `pPort`\

 [in] Порт вызывающий процесс выполняется на.

 `processId`\

 [in] [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) структуру, содержащую рассматриваемый идентификатор процесса, в которой находится программа.

 `guidEngine`\

 [in] Идентификатор GUID модуля отладки, к которой подключен программы (если таковые имеются).

 `programId`\

 [in] Идентификатор программы, для которого необходимо получить узел программы.

 `ppProgramNode`\

 [out] [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) объект, представляющий узел запрошенной программы.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)