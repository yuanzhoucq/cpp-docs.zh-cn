---
title: 编译器警告 （等级 2） C4156
ms.date: 11/04/2016
f1_keywords:
- C4156
helpviewer_keywords:
- C4156
ms.assetid: 9adf3acb-c0fe-42a8-a4db-5822b1493f77
ms.openlocfilehash: 7d9a4ed09f026267e2c0f37fbbe4550ecd668dfc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514421"
---
# <a name="compiler-warning-level-2-c4156"></a>编译器警告 （等级 2） C4156

删除数组表达式而无需使用数组形式的 'delete';数组形式被替代

非数组形式的**删除**不能删除数组。 编译器转换**删除**到数组形式。

仅在 Microsoft 扩展 (/Ze) 下出现此警告。

## <a name="example"></a>示例

```
// C4156.cpp
// compile with: /W2
int main()
{
   int (*array)[ 10 ] = new int[ 5 ][ 10 ];
   delete array; // C4156, changed by compiler to "delete [] array;"
}
```