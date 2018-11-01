---
title: 链接器工具错误 LNK2028
ms.date: 11/04/2016
f1_keywords:
- LNK2028
helpviewer_keywords:
- LNK2028
ms.assetid: e2b03293-6066-464d-a050-ce747bcf7f0e
ms.openlocfilehash: ed2dc1a95d4dd7c447b360da21b5046e20f79083
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643672"
---
# <a name="linker-tools-error-lnk2028"></a>链接器工具错误 LNK2028

"*exported_function*"(*decorated_name*) 函数中引用"*function_containing_function_call*"(*decorated_name*)

## <a name="remarks"></a>备注

在尝试导入纯映像的本机函数时，请记住，本机和纯各编译间不同的隐式调用约定。

**/Clr: pure**编译器选项在 Visual Studio 2015 中弃用并在 Visual Studio 2017 中不受支持。

## <a name="example"></a>示例

此代码的示例生成具有其调用约定是隐式的导出的本机函数的组件[__cdecl](../../cpp/cdecl.md)。

```cpp
// LNK2028.cpp
// compile with: /LD
__declspec(dllexport) int func() {
   return 3;
}
```

## <a name="example"></a>示例

下面的示例创建使用本机函数的纯客户端。 但是，在调用约定 **/clr: pure**是[__clrcall](../../cpp/clrcall.md)。 下面的示例生成 LNK2028。

```cpp
// LNK2028_b.cpp
// compile with: /clr:pure lnk2028.lib
// LNK2028 expected
int func();

int main() {
   return func();
}
```