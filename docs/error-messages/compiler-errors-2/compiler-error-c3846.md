---
title: 编译器错误 C3846 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3846
dev_langs:
- C++
helpviewer_keywords:
- C3846
ms.assetid: c470f8a5-106b-4efb-b8dc-e1319e04130f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f8b44661534dca1beb39c0407f882d41f1f503c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055125"
---
# <a name="compiler-error-c3846"></a>编译器错误 C3846

symbol： 无法导入 assembly2 中的符号： 因为 symbol 具有已导入从另一个程序集 assembly1

不是从引用的程序集导入一个符号，因为从引用的程序集以前导入。

## <a name="example"></a>示例

下面的示例生成 C3846:

```
// C3846a.cpp
// compile with: /LD /clr
public ref struct G
{
};
```

然后编译这段：

```
// C3846b.cpp
// compile with: /clr
#using "c3846a.dll"
#using "c3846a.obj"   // C3846

int main()
{
}
```
