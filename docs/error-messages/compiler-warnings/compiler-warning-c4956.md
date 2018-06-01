---
title: 编译器警告 C4956 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4956
dev_langs:
- C++
helpviewer_keywords:
- C4956
ms.assetid: 9154f2d1-d49f-4e07-90d2-0e9bc028011a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: be92eb948e31a0a5367f92f5c2ed59baac2bd39b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2018
ms.locfileid: "34703699"
---
# <a name="compiler-warning-c4956"></a>编译器警告 C4956

> *类型*： 此类型不是可验证

## <a name="remarks"></a>备注

当指定了 [/clr:safe](../../build/reference/clr-common-language-runtime-compilation.md) 而你的代码包含不可验证的类型时，将生成此警告。 **/Clr: safe**编译器选项是在 Visual Studio 2015 中已过时，并在 Visual Studio 2017 中不支持。

有关详细信息，请参阅[纯代码和可验证代码 (C + + /cli CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。

此警告作为错误发出，可通过 [warning](../../preprocessor/warning.md) 杂注或 [/wd](../../build/reference/compiler-option-warning-level.md) 编译器选项禁用该警告。

## <a name="example"></a>示例

下面的示例生成 C4956：

```cpp
// C4956.cpp
// compile with: /clr:safe
int* p;   // C4956
```