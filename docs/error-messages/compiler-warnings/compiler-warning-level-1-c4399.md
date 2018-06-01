---
title: 编译器警告 （等级 1） C4399 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4399
dev_langs:
- C++
helpviewer_keywords:
- C4399
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aedad6aed07a6056f74ad338037a7268c722627f
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2018
ms.locfileid: "34703715"
---
# <a name="compiler-warning-level-1-c4399"></a>编译器警告（等级 1）C4399

> *符号*： 不应与使用 /clr 进行编译时 __declspec （dllimport） 标记为每个进程的符号： 纯

## <a name="remarks"></a>备注

**/Clr: pure**编译器选项是在 Visual Studio 2015 中已过时，并在 Visual Studio 2017 中不支持。

本机映像或有本机和 CLR 构造的映像中的数据未导入到纯映像。 若要解决此警告，编译与 **/clr** (不 **/clr: pure**) 或删除`__declspec(dllimport)`。

## <a name="example"></a>示例

下面的示例生成 C4399。

```cpp
// C4399.cpp
// compile with: /clr:pure /doc /W1 /c
__declspec(dllimport) __declspec(process) extern const int i;   // C4399
```