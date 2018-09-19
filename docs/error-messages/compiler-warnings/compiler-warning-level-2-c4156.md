---
title: 编译器警告 （等级 2） C4156 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4156
dev_langs:
- C++
helpviewer_keywords:
- C4156
ms.assetid: 9adf3acb-c0fe-42a8-a4db-5822b1493f77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eddce0944152fe95aa4ef2fd98ec30a793a90978
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084492"
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