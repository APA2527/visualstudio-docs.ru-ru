---
title: '&lt;publisherIdentity&gt; элемент (развертывание ClickOnce) | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publisherIdentity Element [ClickOnce deployment manifest], introduction
- required element for signed manifests [ClickOnce], publisherIdentity Element
- publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 995b002784c1e76ceed36e51edb1ae893448f448
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62927543"
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;publisherIdentity&gt; элемент (развертывание ClickOnce)
Содержит сведения об издателе, подписавшем этот манифест развертывания.

## <a name="syntax"></a>Синтаксис

```xml
<publisherIdentity
   name
   issuerKeyHash
/>
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 `publisherIdentity` Элемент является обязательным для манифестов с подписью. В следующей таблице показаны атрибуты, `publisherIdentity` поддерживает элемент.

|Атрибут|Описание|
|---------------|-----------------|
|`name`|Обязательный. Описывает удостоверение стороны, публикации этого приложения.|
|`issuerKeyHash`|Обязательный. Содержит хэш SHA-1 открытого ключа издателя сертификата.|

#### <a name="parameters"></a>Параметры

## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение

## <a name="exceptions"></a>Исключения

## <a name="remarks"></a>Примечания

## <a name="requirements"></a>Требования

## <a name="subhead"></a>Подзаголовок