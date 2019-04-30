---
title: Начало шрифт и цвет шрифта для цветовое выделение текста | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8f03b23076b1eea203166bb0322f05927480a278
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63417163"
---
# <a name="get-font-and-color-information-for-text-colorization"></a>Получить данные шрифта и цвета для цветовое выделение текста
Процесс, который выполняет визуализацию или отображает цветом текста в элементы пользовательского интерфейса (UI) зависит от типа проекта, технологий и разработчиков предпочтений. **Шрифты и цвета** страницу свойств сохраняет параметры.

 Большинство реализаций, которые отображают цветом текст требуется <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> и связанные интерфейсы для параметры отображения представления, получение и сохранение текста.

> [!NOTE]
> При настройке базового редактора (который поддерживает **EditorCategory текст**), рекомендуется использовать технологию выделение цветом в языковой службе. Дополнительные сведения см. в разделе [Общие сведения о шрифте и цвете](../extensibility/font-and-color-overview.md).

## <a name="get-default-font-and-color-information"></a>Получить данные шрифта и цвета по умолчанию
 Все **шрифты и цвета** следует указать параметры окна, отображающие текст в **отображаемые элементы** одного **категории**. Дополнительные сведения см. в разделе [шрифты и цвета, среда, диалоговое окно «Параметры»](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).

Для выделения цветом, VSPackage должен получить текущий **шрифты и цвета** параметры. Пакет VSPackage можно получить текущие параметры следующими способами, в зависимости от его потребностей.

- Используйте механизм сохраняемости шрифта и цвета для получения хранимой или в текущем состоянии. Дополнительные сведения см. в разделе [доступа хранятся параметры шрифта и цвета](../extensibility/accessing-stored-font-and-color-settings.md).

- Используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> интерфейс службы, который предоставляет данные шрифта и цвета для получения экземпляра <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>, если пакет VSPackage не также поставщика шрифта или цвета.

- Реализовать интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>.

Чтобы убедиться, что результаты, полученные путем опроса, актуальные, часто бывает полезно использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> интерфейс, чтобы определить, требуется ли обновление до вызова методов извлечения <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейс.

После получения данные шрифта и цвета, синтаксический анализ текста, отображаемого для идентификации элементов, требующих выделение цветом. Отобразите текст в окне, используя соответствующие шрифты и цвета.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>
- [Использовать шрифты и текст](/dotnet/framework/winforms/advanced/using-fonts-and-text)
- [Работать с цветом](/cpp/windows/working-with-color-image-editor-for-icons)
- [GDI (интерфейс графических устройств)](https://msdn.microsoft.com/library/7e1d4540-bb2e-4257-8eee-eee376acba83)