---
title: true （C++） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- true_cpp
dev_langs:
- C++
helpviewer_keywords:
- true keyword [C++]
ms.assetid: 96be2a70-51c3-4250-9752-874d25a5a11e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8e43fbfd9b3cff9ea617238ed7b4cccd08f780cc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018699"
---
# <a name="true-c"></a>true (C++)

## <a name="syntax"></a>语法

```
bool-identifier = true ;
bool-expression logical-operator true ;
```

## <a name="remarks"></a>备注

此关键字是类型的变量的两个值之一[bool](../cpp/bool-cpp.md)或条件表达式 （条件表达式现在是 true 的布尔表达式）。 如果`i`属于类型**bool**，然后语句`i = true;`分配**true**到`i`。

## <a name="example"></a>示例

```cpp
// bool_true.cpp
#include <stdio.h>
int main()
{
    bool bb = true;
    printf_s("%d\n", bb);
    bb = false;
    printf_s("%d\n", bb);
}
```

```Output
1
0
```

## <a name="see-also"></a>请参阅

[关键字](../cpp/keywords-cpp.md)