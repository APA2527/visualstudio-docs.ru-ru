---
title: Создание проекта модульного теста
description: Сведения о том, как создать проект модульного теста. Тестовый проект может находиться в том же решении, что и рабочий код, или в отдельном решении.
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: how-to
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: f0d438c05d3c9608c11903c02119d7c3e267a48b
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441850"
---
# <a name="create-a-unit-test-project"></a>Создание проекта модульного теста

Модульные тесты зачастую отражают структуру тестируемого кода. Например, отдельный проект модульного теста может быть создан для каждого проекта в продукте. Тестовый проект может находиться в том же решении, что и рабочий код, или в отдельном решении. В решении может быть несколько проектов модульных тестов.

> [!NOTE]
> Расположение модульных тестов для машинного кода и структура тестового проекта могут отличаться от структуры, описанной в этой статье. Дополнительные сведения см. в разделе [Создание модульных тестов для C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="to-create-a-unit-test-project"></a>Создание проекта модульного теста

1. В меню **Файл** последовательно выберите пункты **Создать** > **Проект** или нажмите клавиши **CTRL**+**SHIFT**+**N**.

::: moniker range="vs-2017"

2. В диалоговом окне **Новый проект** разверните узел **Установлено**, выберите требуемый язык для тестового проекта, а затем **Тест**.

3. Выберите шаблон проекта для желаемой тестовой платформы, например **Тестовый проект MSTest** или **Тестовый проект NUnit**. Задайте для проекта имя и нажмите кнопку **ОК**.

   ![Шаблоны тестовых проектов в Visual Studio 2017](media/test-project-templates.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. В поле поиска на странице **Создание проекта** введите **модульный тест**. Выберите шаблон проекта для желаемой тестовой платформы, например **Тестовый проект MSTest** или **Тестовый проект NUnit**, и нажмите **Далее**.

   ![Шаблоны тестовых проектов в Visual Studio 2019](media/vs-2019/test-project-templates.png)

3. На странице **Настроить новый проект** введите имя для проекта и нажмите кнопку **Создать**.

::: moniker-end

4. В проекте модульного теста добавьте ссылку на тестируемый код. Добавление ссылки на проект кода в этом же решении:

   1. Выберите тестовый проект в **обозревателе решений**.

   2. В меню **Проект** выберите **Добавить ссылку**.

   3. В **диспетчере ссылок** выберите узел **Решение** в разделе **Проекты**. Выберите проект кода, который требуется протестировать, а затем нажмите **ОК**.

   Если код, который требуется протестировать, находится в другом месте, сведения о добавлении ссылок см. в разделе [Управление ссылками в проекте](../ide/managing-references-in-a-project.md).

## <a name="next-steps"></a>Дальнейшие действия

См. один из следующих разделов:

**Создание модульных тестов**

- [Модульное тестирование кода](../test/unit-test-your-code.md)

- [Создание модульных тестов для C/C++](writing-unit-tests-for-c-cpp.md)

- [Использование платформы MSTest в модульных тестах](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

**Выполнение модульных тестов**

- [Выполнение модульных тестов с помощью обозревателя тестов](../test/run-unit-tests-with-test-explorer.md)
