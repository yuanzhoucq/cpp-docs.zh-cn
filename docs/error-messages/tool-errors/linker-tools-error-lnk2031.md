---
title: 链接器工具错误 LNK2031 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2031
dev_langs:
- C++
helpviewer_keywords:
- LNK2031
ms.assetid: 18ed4b6e-3e75-443c-bbd8-2f6030dc89ee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d86ea6da8a73d9ba2427e9455c4fca87cd32dd2b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34703660"
---
# <a name="linker-tools-error-lnk2031"></a>链接器工具错误 LNK2031

> 无法生成有关 p/invoke"*function_declaration*" *decorated_name*; 调用约定元数据中缺少

## <a name="remarks"></a>备注

当尝试将本机函数导入纯映像，请记住，本机和纯各编译间不同隐式调用约定。 有关纯映像的详细信息，请参阅[纯代码和可验证代码 (C + + /cli CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。

**/Clr: pure**编译器选项是在 Visual Studio 2015 中已过时，并在 Visual Studio 2017 中不支持。

## <a name="example"></a>示例

此代码示例生成具有其调用约定是隐式的导出的本机函数的组件[__cdecl](../../cpp/cdecl.md)。

```cpp
// LNK2031.cpp
// compile with: /LD
extern "C" {
   __declspec(dllexport) int func() { return 3; }
};
```

## <a name="example"></a>示例

下面的示例创建一个使用本机函数的纯客户端。 但是，在下的调用约定 **/clr: pure**是[__clrcall](../../cpp/clrcall.md)。 下面的示例生成 LNK2031。

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

下面的示例演示如何使用纯映像中的本机函数。 请注意显式 **__cdecl**调用约定说明符。

```cpp
// LNK2031_c.cpp
// compile with: /clr:pure LNK2031.lib
extern "C" int __cdecl func();

int main() {
   return func();
}
```