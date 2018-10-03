---
title: Вариант создания MIP карты | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3b4b3583-0b01-4f5d-aacb-3f96d19111d9
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4805aee80cb298088109a166ecf1a417c9a854aa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560751"
---
# <a name="mip-map-generation-variant"></a>Вариант создания MIP-карты
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [вариант создания Mip карты](https://docs.microsoft.com/visualstudio/debugger/graphics/mip-map-generation-variant).  
  
Включает MIP-карты для текстур, не являющихся целевыми объектами отрисовки.  
  
## <a name="interpretation"></a>Интерпретация  
 MIP-карты используются в первую очередь для устранения артефактов сглаживания в текстурах, для которых выполняется минификация, путем предварительного расчета уменьшенных версий текстуры. Хотя эти дополнительные текстуры занимают память GPU (приблизительно на 33 процента больше, чем исходная текстура), они более эффективны, так как большая часть их поверхности размещается в кэше текстур GPU, а содержимое этого кэша имеет более высокую степень использования.  
  
 Мы рекомендуем использовать MIP-карты для трехмерных сцен, если имеется достаточно памяти для хранения дополнительных текстур, так как они повышают как производительность отрисовки, так и качество изображения.  
  
 Если этот вариант дает значительный прирост производительности, это указывает на то, что текстуры используются без включенных MIP-карт, и поэтому кэш текстур используется не самым эффективным образом.  
  
## <a name="remarks"></a>Примечания  
 MIP-карты создаются принудительно при каждом вызове метода `ID3D11Device::CreateTexture2D`, который создает исходную текстуру. В частности, MIP-карты создаются, если объект D3D11_TEXTUR2D_DESC, передаваемый в параметре `pDesc`, описывает неизменяемый ресурс шейдера, то есть:  
  
-   Для члена BindFlags установлен только флаг D3D11_BIND_SHADER_RESOURCE.  
  
-   Для члена Usage установлен флаг D3D11_USAGE_DEFAULT или D3D11_USAGE_IMMUTABLE.  
  
-   Член CPUAccessFlags имеет значение 0 (нет доступа к ЦП).  
  
-   Для члена SampleDesc член Count имеет значение 1 (многовыборочное сглаживание (MSAA) не применяется).  
  
-   Член MipLevels имеет значение 1 (MIP-карта не существует).  
  
 Когда исходные данные предоставляются приложением, формат текстур должен поддерживать автоматическое создание MIP-карт (определяется флагом D3D11_FORMAT_SUPPORT_MIP_AUTOGEN), если только не используется формат BC1, BC2 или BC3. В противном случае при предоставлении исходных данных текстура не изменяется, и MIP-карты не создаются.  
  
 Если для текстуры были автоматически созданы MIP-карты, вызовы метода `ID3D11Device::CreateShaderResourceView` изменяются во время воспроизведения так, что при дискретизации текстуры используется MIP-цепочка.  
  
## <a name="example"></a>Пример  
 **Mip-карты** можно воспроизвести с помощью следующего кода:  
  
```  
D3D11_TEXTURE2D_DESC texture_description;  
  
// ...  
  
texture_description.MipLevels = 0; // generate a full mipchain  
  
std::vector<D3D11_SUBRESOURCE_DATA> initial_data(num_mips);  
  
for (auto&& mip_level : initial_data)  
{  
    // fill mip_level with the application-supplied initial data  
}  
  
d3d_device->CreateTexture2D(&texture_description, initial_data.data(), &texture)  
```  
  
 Чтобы создать текстуру с полной MIP-цепочкой, задайте для свойства `D3D11_TEXTURE2D_DESC::MipLevels` значение 0. Количество уровней mip в полной mip цепочки является floor(log2(n) + 1), где n — это наибольший размер текстуры.  
  
 Помните, что при предоставлении исходных данных методу `CreateTexture2D` необходимо предоставить объект D3D11_SUBRESOURCE_DATA для каждого уровня MIP.  
  
> [!NOTE]
>  Если вы хотите предоставить собственное содержимое уровня MIP вместо автоматического его создания, вам необходимо создать текстуры с помощью редактора изображений, который поддерживает текстуры с MIP-картами, а затем загрузить файл и передать уровни MIP в `CreateTexture2D`.  
  
## <a name="see-also"></a>См. также  
 [Вариант размера текстур: половина/четверть](../debugger/half-quarter-texture-dimensions-variant.md)


