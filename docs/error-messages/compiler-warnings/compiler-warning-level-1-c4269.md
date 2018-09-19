---
title: 编译器警告 （等级 1） C4269 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4269
dev_langs:
- C++
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6dc986c98028530b8a5d4d25047305fd1a8effef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027267"
---
# <a name="compiler-warning-level-1-c4269"></a>编译器警告（等级 1）C4269

identifier： 用编译器生成默认构造函数初始化 const 自动数据产生不可靠的结果

一个**const**使用编译器生成的默认构造函数初始化的一个重要的类的自动实例。

## <a name="example"></a>示例

```
// C4269.cpp
// compile with: /c /LD /W1
class X {
public:
   int m_data;
};

void g() {
   const X x1;   // C4269
};
```

由于此类的实例在堆栈中的初始值，生成`m_data`可以是任何内容。 此外，由于它是**const**实例的值`m_data`永远不会更改。