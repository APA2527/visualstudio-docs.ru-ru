---
title: Регистрация генераторов одного файла | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1ced598c2a670cd79d7daeeac90f6807baf7d1dd
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436598"
---
# <a name="registering-single-file-generators"></a>Регистрация генераторов одного файла
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Чтобы сделать доступным в пользовательский инструмент [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], необходимо зарегистрировать его таким образом [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] можно создать его экземпляр, который связывается с определенным типом проекта.  
  
### <a name="to-register-a-custom-tool"></a>Чтобы зарегистрировать пользовательский инструмент  
  
1. Либо зарегистрировать настраиваемый инструмент DLL в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] локальный реестр или в системном реестре, в разделе HKEY_CLASSES_ROOT.  
  
     Например, вот регистрационные данные для управляемого MSDataSetGenerator пользовательский инструмент, который поставляется вместе с [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]:  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]  
    @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"  
    "ThreadingModel"="Both"  
    "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"  
    ```  
  
2. Создайте раздел реестра в нужной [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] hive в разделе генераторы\\*GUID* где *GUID* GUID определяется конкретного языка системы проекта или службы. Имя ключа становится программное имя удаляемого пользовательского средства. Пользовательский инструмент ключ имеет следующие значения:  
  
    - (Значение по умолчанию)  
  
         Необязательный параметр. Понятное описание пользовательского инструмента. Этот параметр является обязательным, но рекомендуется.  
  
    - CLSID  
  
         Обязательный. Задает идентификатор для библиотеки классов из COM-компонент, который реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>.  
  
    - GeneratesDesignTimeSource  
  
         Обязательный. Указывает ли типы из файлов, созданных этим настраиваемым инструментом становятся доступными для визуальных конструкторов. Значение этого параметра должно быть (нуль) 0 для типов, не доступен для визуальных конструкторов или 1 (один) для типов, доступных для визуальных конструкторов.  
  
    > [!NOTE]
    > Необходимо зарегистрировать пользовательский инструмент отдельно для каждого языка, для которого требуется пользовательский инструмент доступен.  
  
     Например MSDataSetGenerator регистрируется один раз для каждого языка:  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{164b10b9-b200-11d0-8c61-00a0c91e29d5}\MSDataSetGenerator]  
    @="Microsoft VB Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{fae04ec1-301f-11d3-bf4b-00c04f79efbc}\MSDataSetGenerator]  
    @="Microsoft C# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{e6fdf8b0-f3d1-11d4-8576-0002a516ece8}\MSDataSetGenerator]  
    @="Microsoft J# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
    ```  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>   
 [Реализация генераторов одного файла](../../extensibility/internals/implementing-single-file-generators.md)   
 [Определение пространства имен по умолчанию проекта](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Предоставление типов конструкторам визуальных элементов](../../extensibility/internals/exposing-types-to-visual-designers.md)   
 [Знакомство с объектом BuildManager](http://msdn.microsoft.com/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
