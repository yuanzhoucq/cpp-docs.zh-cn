---
title: 编译器警告（等级2） C4156
ms.date: 11/04/2016
f1_keywords:
- C4156
helpviewer_keywords:
- C4156
ms.assetid: 9adf3acb-c0fe-42a8-a4db-5822b1493f77
ms.openlocfilehash: 95605aa29e1faba449e19dcf20e6895d31cc5874
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052135"
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