---
title: 链接器工具错误 LNK2028 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2028
dev_langs:
- C++
helpviewer_keywords:
- LNK2028
ms.assetid: e2b03293-6066-464d-a050-ce747bcf7f0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9c8eaa03927f51acd3c3d84731e9ef2b282b7c6
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704149"
---
# <a name="linker-tools-error-lnk2028"></a>链接器工具错误 LNK2028

"*exported_function*"(*decorated_name*) 函数中引用"*function_containing_function_call*"(*decorated_name*)

## <a name="remarks"></a>备注

当尝试将本机函数导入纯映像，请记住，本机和纯各编译间不同隐式调用约定。

**/Clr: pure**编译器选项是在 Visual Studio 2015 中已过时，并在 Visual Studio 2017 中不支持。

## <a name="example"></a>示例

此代码示例生成具有其调用约定是隐式的导出的本机函数的组件[__cdecl](../../cpp/cdecl.md)。

```cpp
// LNK2028.cpp
// compile with: /LD
__declspec(dllexport) int func() {
   return 3;
}
```

## <a name="example"></a>示例

下面的示例创建一个使用本机函数的纯客户端。 但是，在下的调用约定 **/clr: pure**是[__clrcall](../../cpp/clrcall.md)。 下面的示例生成 LNK2028。

```cpp
// LNK2028_b.cpp
// compile with: /clr:pure lnk2028.lib
// LNK2028 expected
int func();

int main() {
   return func();
}
```