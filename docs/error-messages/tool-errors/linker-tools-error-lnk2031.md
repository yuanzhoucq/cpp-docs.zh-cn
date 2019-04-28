---
title: 链接器工具错误 LNK2031
ms.date: 11/04/2016
f1_keywords:
- LNK2031
helpviewer_keywords:
- LNK2031
ms.assetid: 18ed4b6e-3e75-443c-bbd8-2f6030dc89ee
ms.openlocfilehash: 003b9a58bfb08130f034530f59e2de27efa2ae8d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298914"
---
# <a name="linker-tools-error-lnk2031"></a>链接器工具错误 LNK2031

> 无法生成 p/invoke 为"*function_declaration*" *decorated_name*; 元数据中缺少调用约定

## <a name="remarks"></a>备注

在尝试导入纯映像的本机函数时，请记住，本机和纯各编译间不同的隐式调用约定。 有关纯映像的详细信息，请参阅[纯代码和可验证代码 (C++/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。

**/Clr: pure**编译器选项在 Visual Studio 2015 中弃用并在 Visual Studio 2017 中不受支持。

## <a name="example"></a>示例

此代码的示例生成具有其调用约定是隐式的导出的本机函数的组件[__cdecl](../../cpp/cdecl.md)。

```cpp
// LNK2031.cpp
// compile with: /LD
extern "C" {
   __declspec(dllexport) int func() { return 3; }
};
```

## <a name="example"></a>示例

下面的示例创建使用本机函数的纯客户端。 但是，在调用约定 **/clr: pure**是[__clrcall](../../cpp/clrcall.md)。 下面的示例生成 LNK2031。

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

下面的示例演示如何使用纯映像中的本机函数。 请注意的显式 **__cdecl**调用约定说明符。

```cpp
// LNK2031_c.cpp
// compile with: /clr:pure LNK2031.lib
extern "C" int __cdecl func();

int main() {
   return func();
}
```