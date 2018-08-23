---
title: 链接器工具错误 LNK1313 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1313
dev_langs:
- C++
helpviewer_keywords:
- LNK1313
ms.assetid: 5df0b72e-bb3f-428c-8d84-6084238f9827
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d6a896c8ba012c69755c5292475b2d155ad92066
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705083"
---
# <a name="linker-tools-error-lnk1313"></a>链接器工具错误 LNK1313

> 检测到 ijw/native 模块；不能与纯模块链接

## <a name="remarks"></a>备注

Visual c + + 的当前版本不支持将本机或混合托管/本机.obj 文件与编译的.obj 文件链接 **/clr: pure**。

**/Clr: pure**编译器选项是在 Visual Studio 2015 中已过时，并在 Visual Studio 2017 中不支持。

## <a name="example"></a>示例

```cpp
// LNK1313.cpp
// compile with: /c /clr:pure
// a pure module
int main() {}
```

## <a name="example"></a>示例

```cpp
// LNK1313_b.cpp
// compile with: /c /clr
// an IJW module
void test(){}
```

## <a name="example"></a>示例

下面的示例将生成 LNK1313。

```cpp
// LNK1313_c.cpp
// compile with: /link LNK1313.obj LNK1313_b.obj
// LNK1313 warning expected
```