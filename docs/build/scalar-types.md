---
title: 标量类型
ms.date: 11/04/2016
ms.assetid: 07c9195e-b6c7-4083-8ef0-8a93032e4d1e
ms.openlocfilehash: 0c2fa18022763564a29b6a96f8ce719039dcd216
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492050"
---
# <a name="scalar-types"></a>标量类型

尽管数据的访问可能源于任何的对齐方式，但建议数据在其自然边界，以避免性能损失 （或的多个） 上对齐。 枚举是常量整数，而是被视为 32 位整数。 因为这与使用以下的对齐值的对齐方式下, 表介绍用于它的类型定义和建议的存储：

- 8 位字节

- Word 的 16 位

- 双字的 32 位

- 四核 Word 的 64 位

- 八 Word-128 位

|||||
|-|-|-|-|
|标量类型|C 数据类型|存储大小 （以字节为单位）|建议的对齐方式|
|**INT8**|**char**|1|Byte|
|**UINT8**|**unsigned char**|1|Byte|
|**INT16**|**short**|2|字|
|**UINT16**|**unsigned short**|2|字|
|**INT32**|**int**，**长**|4|双字|
|**UINT32**|**无符号的整型、 无符号长**|4|双字|
|**INT64**|**__int64**|8|四字|
|**UINT64**|unsigned __int64|8|四字|
|**FP32 （单精度）**|**float**|4|双字|
|**FP64 （双精度）**|**double**|8|四字|
|**指针**|<strong>\*</strong>|8|四字|
|**__m64**|**结构 __m64**|8|四字|
|**__m128**|**结构 __m128**|16|Octaword|

## <a name="see-also"></a>请参阅

[类型和存储](../build/types-and-storage.md)