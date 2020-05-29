---
title: 编译器警告（等级1） C4154
ms.date: 11/04/2016
f1_keywords:
- C4154
helpviewer_keywords:
- C4154
ms.assetid: 4511afeb-e893-4cc6-83b6-4c7a0477f76b
ms.openlocfilehash: 07b4c6e0821c925e70ce1bce1d910f184d658982
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163607"
---
# <a name="compiler-warning-level-1-c4154"></a>编译器警告（等级1） C4154

删除数组表达式;转换到提供的指针

不能对数组使用 `delete`，因此编译器将数组转换为指针。

## <a name="example"></a>示例

```cpp
// C4154.cpp
// compile with: /c /W1
int main() {
   int array[ 10 ];
   delete array;   // C4154 can't delete stack object

   int *parray2 = new int [10];
   int (&array2)[10] = (int(&)[10]) parray2;
   delete [] array2;   // C4154

   // try the following line instead
   delete [] &array2;
}
```
