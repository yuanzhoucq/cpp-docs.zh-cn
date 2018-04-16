---
title: "编译器警告 （等级 1） C4305 |Microsoft 文档"
ms.custom: 
ms.date: 1/17/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4305
dev_langs:
- C++
helpviewer_keywords:
- C4305
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8fe4b2b420c44584fdd5b4d48b4264bbc7a51bee
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="compiler-warning-level-1-c4305"></a>编译器警告（等级 1）C4305

> *上下文*： 从截断*type1*到*type2*  

## <a name="remarks"></a>备注

当某个值转换为更小的类型进行初始化，或作为构造函数自变量，从而导致信息丢失时，发出此警告。

## <a name="example"></a>示例

此示例演示两种方法可能会看到此警告：

```cpp
// C4305.cpp
// Compile by using: cl /EHsc /W4 C4305.cpp

struct item
{
    item(float) {}
};

int main()
{
    float f = 2.71828;          // C4305 'initializing'
    item i(3.14159);            // C4305 'argument'
    return static_cast<int>(f);
}
```

若要修复此问题，请使用正确的类型的值初始化，或使用显式强制转换为正确的类型。 例如，使用**float**文本而不是 2.71828f 如**double** （浮点文本的默认类型） 来初始化**float**变量，或要传递给构造函数采用**float**自变量。
