---
title: 链接器工具错误 LNK2031
ms.date: 11/04/2016
f1_keywords:
- LNK2031
helpviewer_keywords:
- LNK2031
ms.assetid: 18ed4b6e-3e75-443c-bbd8-2f6030dc89ee
ms.openlocfilehash: 326886f8de8b59cce9df46eb7b0325b7cc9eb9f2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225197"
---
# <a name="linker-tools-error-lnk2031"></a>链接器工具错误 LNK2031

> 无法为 "*function_declaration*" *decorated_name*生成 p/invoke;元数据中缺少调用约定

## <a name="remarks"></a>备注

尝试将本机函数导入纯映像时，请记住，本机编译和纯编译之间的隐式调用约定有所不同。 有关纯映像的详细信息，请参阅[纯代码和可验证代码（c + +/cli）](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。

**/Clr： pure**编译器选项在 visual studio 2015 中已弃用，在 visual studio 2017 中不受支持。

## <a name="example"></a>示例

此代码示例使用导出的本机函数生成一个组件，该函数的调用约定隐式[__cdecl](../../cpp/cdecl.md)。

```cpp
// LNK2031.cpp
// compile with: /LD
extern "C" {
   __declspec(dllexport) int func() { return 3; }
};
```

## <a name="example"></a>示例

下面的示例创建一个使用本机函数的纯客户端。 但是，在 **/clr： pure**下调用约定[__clrcall](../../cpp/clrcall.md)。 下面的示例生成 LNK2031。

```cpp
// LNK2031_b.cpp
// compile with: /clr:pure LNK2031.lib
// LNK2031 expected
extern "C" int func();

int main() {
   return func();
}
```

## <a name="example"></a>示例

下面的示例演示如何从纯映像使用本机函数。 请注意显式 **`__cdecl`** 调用约定说明符。

```cpp
// LNK2031_c.cpp
// compile with: /clr:pure LNK2031.lib
extern "C" int __cdecl func();

int main() {
   return func();
}
```
