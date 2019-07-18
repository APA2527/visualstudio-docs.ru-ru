---
title: Переименование узлов иерархии проекта (C++) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- HierUtil7 sample [Visual Studio SDK], renaming project nodes
- project nodes, renaming in HierUtil7 sample
ms.assetid: cea5968e-e9f8-41a5-b068-622df542247c
caps.latest.revision: 12
manager: jillfra
ms.openlocfilehash: c7ad43fe1fd0e22cd94194d3079761de812b6ced
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686588"
---
# <a name="renaming-project-hierarchy-nodes-c"></a>Переименование узлов иерархии проекта (C++)
Узел иерархии проекта папку можно переименовать с помощью платформы проекта HierUtil7 для неуправляемого C++. Дополнительные сведения см. в разделе [образец Hierutil7](https://msdn.microsoft.com/29c15184-a70c-4813-86c2-fb1d47442d11).  
  
## <a name="expanding-the-hierarchy-node"></a>Разверните узел «иерархии»  
  
#### <a name="to-expand-the-hierarchy-node-and-rename-the-folder"></a>Чтобы развернуть узел иерархии и переименуйте папку  
  
1. Выберите узел иерархии, используя следующий метод:  
  
    ```  
    IfFailGo(pNode->ExtExpand(EXPF_SelectItem, GUID_MacroExplorer));  
    ```  
  
     `pNode` — это контейнер иерархии, соответствующий папке и `EXPF_SelectItem` из <xref:Microsoft.VisualStudio.Shell.Interop.EXPANDFLAGS> перечисления. `GUID_MacroExplorer` Является константа, представляющая GUID определяется в Vsshell.idl и приведен пример `rguidPersistenceSlot` в сигнатуре функции `ExtExpand`, определенный в Hu_node.h.  
  
    ```  
    HRESULT ExtExpand(EXPANDFLAGS expandflags, REFGUID rguidPersistenceSlot = GUID_SolutionExplorer) const;  
    ```  
  
     Файл Hu_node.h можно найти в папке \<корневой папки установки > \Program Files\VSIP 8.0\EnvSDK\common\hierutil7:  
  
2. Переименовать папку, публикуя команду Переименовать с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.PostExecCommand%2A>  
  
    ```  
    IfFailGo(srpVsUIShell->PostExecCommand(&guidVSStd97, cmdidRename, 0, NULL));  
    ```  
  
     `srpVsUIShell` — <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> указателя: `<IVsUIShell>``srpVsUIShell`. `guiVSStd97` — Это уникальный идентификатор группы команд, к которому команда `cmdidRename` принадлежит, определенные в Vsshlids.h.  
  
## <a name="see-also"></a>См. также  
 [Создание типов проектов](../extensibility/internals/creating-project-types.md)   
 [Примеры VSSDK](../misc/vssdk-samples.md)