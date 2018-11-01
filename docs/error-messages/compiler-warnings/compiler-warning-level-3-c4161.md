---
title: 编译器警告（等级 3）C4161
ms.date: 08/27/2018
f1_keywords:
- C4161
helpviewer_keywords:
- C4161
ms.assetid: 03d3be61-83f1-4009-8310-8758ab67055f
ms.openlocfilehash: e1bbc949c298a7cfb6c3a3a061616db3dc4730f4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555826"
---
# <a name="compiler-warning-level-3-c4161"></a>编译器警告（等级 3）C4161

> #<a name="pragma-pragmapop--more-pops-than-pushes"></a>杂注*杂注*（要...）： 比入栈的多个

## <a name="remarks"></a>备注

因为对于 *pragma*，源代码中出栈比入栈多一个，堆栈可能无法正常工作。 若要避免此警告，请确保出栈数不超过入栈数。

## <a name="example"></a>示例

下面的示例生成 C4161:

```cpp
// C4161.cpp
// compile with: /W3 /LD
#pragma pack(push, id)
#pragma pack(pop, id)
#pragma pack(pop, id)   // C4161, an extra pop

#pragma bss_seg(".my_data1")
int j;

#pragma bss_seg(push, stack1, ".my_data2")
int l;

#pragma bss_seg(pop, stack1)
int m;

#pragma bss_seg(pop, stack1)   // C4161
```