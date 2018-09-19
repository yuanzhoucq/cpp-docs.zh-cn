---
title: 编译器警告 （等级 1） C4364 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4364
dev_langs:
- C++
helpviewer_keywords:
- C4364
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e37c7f37e1b51296bd5c3ae2cbdb85a93326f027
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087248"
---
# <a name="compiler-warning-level-1-c4364"></a>编译器警告（等级 1）C4364

\#使用适用于程序集 file 以前看到没有 as_friend 特性; location(line_number) 在未应用 as_friend

一个`#using`指令重复对于给定的元数据文件，但`as_friend`第一个匹配项中未使用过限定符; 编译器将忽略第二个`as_friend`。

有关详细信息，请参阅[友元程序集 （c + +）](../../dotnet/friend-assemblies-cpp.md)。

## <a name="example"></a>示例

下面的示例创建一个组件。

```
// C4364.cpp
// compile with: /clr /LD
ref class A {};
```

## <a name="example"></a>示例

下面的示例生成 C4364。

```
// C4364_b.cpp
// compile with: /clr /W1 /c
#using " C4364.dll"
#using " C4364.dll" as_friend   // C4364
```