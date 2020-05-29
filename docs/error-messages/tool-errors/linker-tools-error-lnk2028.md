---
title: 链接器工具错误 LNK2028
ms.date: 11/04/2016
f1_keywords:
- LNK2028
helpviewer_keywords:
- LNK2028
ms.assetid: e2b03293-6066-464d-a050-ce747bcf7f0e
ms.openlocfilehash: ef9e3eae655a4fbee1c3da74f6036e5fb22434b1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194611"
---
# <a name="linker-tools-error-lnk2028"></a>链接器工具错误 LNK2028

函数 "*function_containing_function_call*" 中引用了 "*exported_function*" （*decorated_name*）（*decorated_name*）

## <a name="remarks"></a>备注

尝试将本机函数导入纯映像时，请记住，本机编译和纯编译之间的隐式调用约定有所不同。

**/Clr： pure**编译器选项在 visual studio 2015 中已弃用，在 visual studio 2017 中不受支持。

## <a name="example"></a>示例

此代码示例使用导出的本机函数生成一个组件，该函数的调用约定隐式[__cdecl](../../cpp/cdecl.md)。

```cpp
// LNK2028.cpp
// compile with: /LD
__declspec(dllexport) int func() {
   return 3;
}
```

## <a name="example"></a>示例

下面的示例创建一个使用本机函数的纯客户端。 但是，在 **/clr： pure**下调用约定[__clrcall](../../cpp/clrcall.md)。 下面的示例生成 LNK2028。

```cpp
// LNK2028_b.cpp
// compile with: /clr:pure lnk2028.lib
// LNK2028 expected
int func();

int main() {
   return func();
}
```
