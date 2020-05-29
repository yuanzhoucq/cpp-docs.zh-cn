---
title: '&lt;codecvt&gt; 枚举'
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_mode
ms.assetid: 46a8b073-01bc-46d3-b3d3-a8540f9422c1
helpviewer_keywords:
- std::codecvt_mode
ms.openlocfilehash: e67290d8de0b8251191c4a93b66b7e19a293ed61
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371946"
---
# <a name="ltcodecvtgt-enums"></a>&lt;codecvt&gt; 枚举

## <a name="codecvt_mode-enumeration"></a><a name="codecvt_mode"></a>codecvt_mode枚举

指定 [locale](../standard-library/locale-class.md) facet 的配置信息。

```cpp
enum codecvt_mode {
    consume_header = 4,
    generate_header = 2,
    little_endian = 1
};
```

### <a name="remarks"></a>备注

枚举定义了三个常量，这些常量向[\<codecvt>](../standard-library/codecvt.md)中声明的区域设置面提供配置信息。 非重复值为：

- `consume_header`，在读取多字节序列时使用初始标头序列，并确定要读取的后续多字节序列的字节顺序

- `generate_header`，在写入多字节序列时生成初始标头序列，以播发要编写的后续多字节序列的字节顺序

- `little_endian`，在 little-endian 顺序中，而不是在默认 big endian 顺序中生成多字节序列

这些常量可以任意组合并用“OR”连在一起。

## <a name="see-also"></a>另请参阅

[\<编码>](../standard-library/codecvt.md)
