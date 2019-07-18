---
title: Добавление каталогов, чтобы добавить новый элемент-диалоговое окно | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f370d208cb8f7aad88f806983983ccee9f584625
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203928"
---
# <a name="adding-directories-to-the-add-new-item-dialog-box"></a>Добавление каталогов в диалоговое окно "Добавить новый элемент"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В следующем примере кода показано, как зарегистрировать новый набор каталогов для **Добавление нового элемента** диалоговое окно. Каталоги для **Добавление нового элемента** диалоговое окно отличаются для каждого проекта. Таким образом, зарегистрированных в подразделе Projects, в каталоги \<HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects >:  
  
## <a name="the-registry-script"></a>Скрипт реестра  
  
```  
NoRemove Projects  
{  
  NoRemove %GUID_Project%  
  {  
    NoRemove AddItemTemplates  
    {  
      NoRemove TemplateDirs  
      {  
        ForceRemove %CLSID_Package%  
        {  
      ForceRemove /1 = s '#%Folder_Label_ResID%'  
          {  
            val TemplatesDir = s '%Template_Path%'     
            val SortPriority = d 2000  
          }  
        }  
      }  
    }  
  }  
}  
```  
  
 Значение Template_Path указывает полный путь к каталогу, содержащему шаблоны проектов. Эти шаблоны могут быть VSZ-файлы или файлы описания шаблонов для клонирования.  
  
 Значение SortPriority указывает приоритет сортировки.  
  
## <a name="adding-items-to-an-existing-project"></a>Добавление элементов в существующий проект  
 Можно также добавить элементы в существующий проект. Например, для [!INCLUDE[csprcs](../../includes/csprcs-md.md)] проекта, можно добавить элементы к \<корневой > Папка \VC#\CSharpProjectItems\LocalProjectItems \Program Files\Microsoft Visual Studio. В этом случае `%GUID_Project%` – идентификатор GUID для проекта C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).  
  
 Также можно расширить существующий проект запрограммировав подтипа проекта. Подтип проекта вы можете расширить проект без написания нового типа проекта. Дополнительные сведения о подтипов проекта, см. в разделе [подтипов проекта](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>См. также  
 [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Добавление элементов, чтобы добавить новый элемент диалоговые окна](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Добавление каталогов в диалоговое окно "Создание проекта"](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
