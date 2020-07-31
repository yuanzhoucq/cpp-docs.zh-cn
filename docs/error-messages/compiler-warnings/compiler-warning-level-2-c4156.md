---
title: 编译器警告（等级2） C4156
ms.date: 11/04/2016
f1_keywords:
- C4156
helpviewer_keywords:
- C4156
ms.assetid: 9adf3acb-c0fe-42a8-a4db-5822b1493f77
ms.openlocfilehash: 279ab5d9de738fb4e2aa6dece4bb16353eca031b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87206479"
---
# <a name="compiler-warning-level-2-c4156"></a>编译器警告（等级2） C4156

未使用数组形式的 "delete" 删除数组表达式;替换数组形式

的非数组形式 **`delete`** 无法删除数组。 编译器已转换 **`delete`** 为数组形式。

此警告仅在 Microsoft 扩展（/Ze）下出现。

## <a name="example"></a>示例

```cpp
// C4156.cpp
// compile with: /W2
int main()
{
   int (*array)[ 10 ] = new int[ 5 ][ 10 ];
   delete array; // C4156, changed by compiler to "delete [] array;"
}
```
