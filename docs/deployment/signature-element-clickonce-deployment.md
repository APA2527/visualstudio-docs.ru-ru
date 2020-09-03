---
title: '&lt;&gt;Элемент Signature (развертывание ClickOnce) | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <Signature> element [ClickOnce deployment manifest]
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b6f07e2649d6f41e77f453f64c5838c746f22ad0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85835424"
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;&gt;Элемент Signature (развертывание ClickOnce)
Содержит сведения, необходимые для того, чтобы подписать этот манифест развертывания с помощью цифровой подписи.

## <a name="syntax"></a>Синтаксис

```xml

<Signature> 
   XML signature information 
</Signature>
```

## <a name="remarks"></a>Remarks
 Подпись манифеста развертывания с помощью подписи конверта является необязательной, но рекомендуется. Дополнительные сведения о подписывании XML-файлов см. в разделе консорциум W3C рекомендации «синтаксис XML-подписи и обработка», описанная в статье [http://www.w3.org/TR/xmldsig-core/](https://www.w3.org/TR/xmldsig-core/) .

 Если вы хотите подписать манифест, необходимо предоставить хэши для всех файлов. Манифест с файлами, которые не хэшируются, не может быть подписан, так как пользователи не могут проверить содержимое нехэшированных файлов.

## <a name="example"></a>Пример
 В следующем примере кода показан `Signature` элемент в манифесте развертывания, который используется в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертывании.

```xml
<Signature xmlns="http://www.w3.org/2000/09/xmldsig#">
  <SignedInfo>
    <CanonicalizationMethod Algorithm=
           "http://www.w3.org/TR/2001/REC-xml-c14n-20010315" />
    <SignatureMethod Algorithm=
           "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />
    <Reference URI="">
      <Transforms>
        <Transform Algorithm=
           "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />
      </Transforms>
      <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
      <DigestValue>d2z5AE...</DigestValue>
    </Reference>
  </SignedInfo>
  <SignatureValue>
4PHj6SaopoLp...
  </SignatureValue>
  <KeyInfo>
    <X509Data>
      <X509Certificate>
MIIHnTCCBoWgAwIBAgIKJY9+nwAHAAB...
      </X509Certificate>
    </X509Data>
  </KeyInfo>
</Signature>
```

## <a name="see-also"></a>См. также раздел
- [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)
