---
title: 编译器警告（等级2） C4156
ms.date: 11/04/2016
f1_keywords:
- C4156
helpviewer_keywords:
- C4156
ms.assetid: 9adf3acb-c0fe-42a8-a4db-5822b1493f77
ms.openlocfilehash: b9add4af0fddf8d68bbba0293530f2bb0ce3800d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162083"
---
# <a name="compiler-warning-level-2-c4156"></a>编译器警告（等级2） C4156

未使用数组形式的 "delete" 删除数组表达式;替换数组形式

**删除**的非数组形式无法删除数组。 编译器将**delete**转换为数组形式。

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
