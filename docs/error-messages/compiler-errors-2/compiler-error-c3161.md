---
title: 编译器错误 C3161 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3161
dev_langs:
- C++
helpviewer_keywords:
- C3161
ms.assetid: 1fe2be85-a343-487b-8476-bf9e257eb29d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 11396ccad33489b41d18759ba4d2f00b445e94a3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46136070"
---
# <a name="compiler-error-c3161"></a>编译器错误 C3161

interface： 嵌套类、 结构、 联合或接口中的接口是非法的;类、 结构或联合中的嵌套接口是非法的

[__Interface](../../cpp/interface.md)只能出现在全局范围或命名空间内。 类、 结构或联合不能出现在接口中。

## <a name="example"></a>示例

下面的示例生成 C3161。

```
// C3161.cpp
// compile with: /c
__interface X {
   __interface Y {};   // C3161 A nested interface
};
```