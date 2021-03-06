---
title: Средства Entity Framework
description: Общие сведения о Entity Framework Tools в Visual Studio. Entity Framework Tools предназначены для помощи в создании приложений Entity Framework (EF).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: ee4bb5e56c5ae9ffb5f5266c8ef80804c8e96597
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866987"
---
# <a name="entity-framework-tools-in-visual-studio"></a>Entity Framework Tools в Visual Studio

Entity Framework — это технология объектно-реляционного сопоставления, которая позволяет разработчикам .NET работать с реляционными данными с помощью объектов, относящихся к домену. Это исключает необходимость в большинстве кодов доступа к данным, которые обычно требуется писать разработчикам. Entity Framework — это рекомендуемая технология моделирования объектно-реляционного сопоставления (ORM) для новых приложений .NET.

Entity Framework Tools предназначены для помощи в создании приложений Entity Framework (EF). Полная документация по Entity Framework: [Обзор-EF 6](/ef/ef6/).

  > [!NOTE]
  > Entity Framework Tools, описанные на этой странице, используются для создания *EDMX* -файлов, которые не поддерживаются в EF Core. Сведения о создании модели EF Core из существующей базы данных см. в разделе [реконструирование — EF Core](/ef/core/managing-schemas/scaffolding). Дополнительные сведения о различиях между EF 6 и EF Core см. в разделе [Сравнение EF 6 и EF Core](/ef/efcore-and-ef6/).

С помощью Entity Framework Tools можно создать *концептуальную модель* на основе существующей базы данных, а затем графически визуализировать и изменить концептуальную модель. Либо можно сначала создать концептуальную модель с помощью графических средств, а затем создать базу данных, которая поддерживает эту модель. В любом случае можно автоматически обновлять модель при изменении основной базы данных и автоматически создавать код объектного уровня для приложения. Процессы создания базы данных и создания кода объектного уровня допускают настройку.

Средства Entity Framework устанавливаются как часть рабочей нагрузки **хранения и обработки данных** в Visual Studio Installer. Их также можно установить как отдельный компонент в категории **SDK, библиотеки и платформы** .

Ниже приведены специальные средства, которые составляют средства Entity Framework в Visual Studio.

- [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] Конструктор** (**Entity Designer**) можно использовать для визуального создания и изменения сущностей, ассоциаций, сопоставлений и отношений наследования. **Entity Designer** также создает [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)] [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] код уровня объектов или.

- С помощью **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] мастера** можно создать концептуальную модель на основе существующей базы данных и добавить в приложение сведения о подключении к базе данных.

- Сначала можно создать концептуальную модель с помощью **мастера создания базы данных** , а затем создать базу данных, которая поддерживает эту модель.

- **Мастер обновления моделей** можно использовать для обновления концептуальной модели, модели хранения и сопоставлений при внесении изменений в основную базу данных.

  > [!NOTE]
  > Начиная с Visual Studio 2010 средства Entity Framework не поддерживают [!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)] .

Средства создают или изменяют *EDMX* файл. Этот *EDMX* файл содержит сведения, описывающие концептуальную модель, модель хранения и сопоставления между ними. Дополнительные сведения см. в разделе [EDMX](/ef/ef6/).

[Entity Framework Power Tools](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4) помогает создавать приложения, использующие EDM. Power Tools может создать концептуальную модель, проверить существующую модель, создать файлы исходного кода, содержащие классы объектов на основе концептуальной модели, и создать файлы исходного кода, содержащие представления, создаваемые моделью. Подробные сведения см. в разделе [предварительно созданные представления сопоставления](/ef/ef6/fundamentals/performance/pre-generated-views).

## <a name="related-topics"></a>См. также

| Заголовок | Описание |
| - | - |
| [ADO.NET Entity Framework](/dotnet/framework/data/adonet/ef/index) | Описывает использование [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] средств, [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] предоставляемых, для создания приложений. |
| [EDM (модель данных с использованием сущностей)](/dotnet/framework/data/adonet/entity-data-model) | Содержит ссылки и сведения для работы с данными, которые используются приложениями, основанными на [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] . |
| [Документация по Entity Framework (EF))](/ef/ef6/get-started) | Содержит индекс видео, учебников и расширенную документацию, которая поможет вам максимально эффективно использовать Entity Framework. |
| [Приложение ASP.NET 5 в новую базу данных](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html) | Описание создания нового приложения ASP.NET 5 с помощью Entity Framework 7. |

## <a name="see-also"></a>См. также

- [Visual Studio Data Tools для .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
