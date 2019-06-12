---
title: CA1063. Правильно реализуйте IDisposable
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 932805f938e9d96cd944230fcc8aa82a4710da31
ms.sourcegitcommit: 51dad3e11d7580567673e0d426ab3b0a17584319
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/10/2019
ms.locfileid: "66820633"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063. Правильно реализуйте IDisposable

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

<xref:System.IDisposable?displayProperty=nameWithType> Интерфейс реализован неверно. Возможные причины:

- <xref:System.IDisposable> является воссозданы в классе.

- Завершение подготовки является reoverridden.

- Переопределяется Dispose().

- Метод Dispose() не является общим, [запечатанный](/dotnet/csharp/language-reference/keywords/sealed), или с именем **Dispose**.

- Dispose(bool) не защищенный виртуальный и незапечатанный.

- В незапечатанных типов Dispose() необходимо вызвать Dispose(true).

- Для незапечатанных типов реализации Finalize не вызывает один или оба Dispose(bool) или метод завершения базового класса.

Нарушение любого из этих шаблонов активирует предупреждение ca1063 следует.

Каждый незапечатанный тип, который объявляет и реализует <xref:System.IDisposable> интерфейс необходимо предоставить собственный `protected virtual void Dispose(bool)` метод. `Dispose()` необходимо вызвать `Dispose(true)`, а также вызывать метод завершения `Dispose(false)`. При создании незапечатанный тип, который объявляет и реализует <xref:System.IDisposable> интерфейс, необходимо определить `Dispose(bool)` и вызывать его. Дополнительные сведения см. в разделе [очистки неуправляемых ресурсов (руководство по .NET)](/dotnet/standard/garbage-collection/unmanaged) и [удаляемости](/dotnet/standard/design-guidelines/dispose-pattern).

По умолчанию это правило считывает только типы, видимые извне, но это [можно настроить](#configurability).

## <a name="rule-description"></a>Описание правила

Все <xref:System.IDisposable> типы должны реализовывать [шаблон Dispose](/dotnet/standard/design-guidelines/dispose-pattern) правильно.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Проверьте код и определить, какой из указанных ниже способов устранения нарушения:

- Удалить <xref:System.IDisposable> из списка интерфейсов, которые реализуются вашей типом и вместо него переопределите реализацию базового класса Dispose.

- Удалите метод завершения из типа, переопределите Dispose (bool disposing) и поместите логику завершения в ветвь кода, где значение «disposing» равно false.

- Переопределите Dispose (bool disposing) и поместите логику освобождения в ветвь кода, где «disposing» равно true.

- Убедитесь, что Dispose() объявлен как открытый и [запечатанный](/dotnet/csharp/language-reference/keywords/sealed).

- Переименуйте метод dispose для **Dispose** и убедитесь, что он объявлен как открытый и [запечатанный](/dotnet/csharp/language-reference/keywords/sealed).

- Убедитесь в том, что Dispose(bool) объявлен как защищенный, виртуальный и незапечатанный.

- Изменить Dispose() так, чтобы он вызывал Dispose(true), затем вызывает <xref:System.GC.SuppressFinalize%2A> для текущего экземпляра объекта (`this`, или `Me` в Visual Basic), а затем возвращает.

- Измените метод завершения, таким образом, чтобы он вызывал Dispose(false) и затем возвращает.

- При создании незапечатанный тип, который объявляет и реализует <xref:System.IDisposable> интерфейсом, убедитесь, что реализация <xref:System.IDisposable> соответствует шаблону, который описан ранее в этом разделе.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Для этого правила отключать вывод предупреждений не следует.

## <a name="configurability"></a>Возможность настройки

Если у вас это правило из [анализаторы FxCop](install-fxcop-analyzers.md) (а не с помощью функций анализа статического кода), можно настроить, какие части вашей базы кода, чтобы применить это правило, в зависимости от их доступности. Например чтобы указать, что правило должно выполняться только для рабочей области не являющийся открытым API, добавьте следующую пару "ключ значение" файла editorconfig в проект:

```ini
dotnet_code_quality.ca1063.api_surface = private, internal
```

В этой категории (структуры) можно настроить этот параметр для только что это правило, для всех правил или для всех правил. Дополнительные сведения см. в разделе [анализаторы FxCop, Настройка](configure-fxcop-analyzers.md).

## <a name="pseudo-code-example"></a>Пример псевдокода

Следующий псевдокод представлен общий пример реализации Dispose(bool) в класс, использующий управляемые и машинные ресурсы.

```csharp
public class Resource : IDisposable
{
    private IntPtr nativeResource = Marshal.AllocHGlobal(100);
    private AnotherResource managedResource = new AnotherResource();

    // Dispose() calls Dispose(true)
    public void Dispose()
    {
        Dispose(true);
        GC.SuppressFinalize(this);
    }

    // NOTE: Leave out the finalizer altogether if this class doesn't
    // own unmanaged resources, but leave the other methods
    // exactly as they are.
    ~Resource()
    {
        // Finalizer calls Dispose(false)
        Dispose(false);
    }

    // The bulk of the clean-up code is implemented in Dispose(bool)
    protected virtual void Dispose(bool disposing)
    {
        if (disposing)
        {
            // free managed resources
            if (managedResource != null)
            {
                managedResource.Dispose();
                managedResource = null;
            }
        }
        // free native resources if there are any.
        if (nativeResource != IntPtr.Zero)
        {
            Marshal.FreeHGlobal(nativeResource);
            nativeResource = IntPtr.Zero;
        }
    }
}
```

## <a name="see-also"></a>См. также

- [Удалить шаблон (рекомендации по разработке framework)](/dotnet/standard/design-guidelines/dispose-pattern)
- [Очистка неуправляемых ресурсов (руководство по .NET)](/dotnet/standard/garbage-collection/unmanaged)