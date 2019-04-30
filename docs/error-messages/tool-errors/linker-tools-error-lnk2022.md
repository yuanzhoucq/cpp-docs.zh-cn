---
title: 链接器工具错误 LNK2022
ms.date: 11/04/2016
f1_keywords:
- LNK2022
helpviewer_keywords:
- LNK2022
ms.assetid: d2128c73-dde3-4b8e-a9b2-0a153acefb3b
ms.openlocfilehash: e55202274c5ec3982f784ad6cdf074a5a99e922f
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345339"
---
# <a name="linker-tools-error-lnk2022"></a>链接器工具错误 LNK2022

> 元数据操作失败 (*HRESULT*): *error_message*

正在合并元数据时，链接器检测到错误。 必须解析元数据错误链接才能成功。

若要诊断此问题的一种方法是运行**ildasm-令牌**中列出的令牌上要发现哪些类型的对象文件`error_message`，并查找不同之处。  元数据中具有相同名称的两种不同类型无效，即使只是 LayoutType 属性不同。

其中一个原因 LNK2022 就是当具有相同名称但具有冲突定义的多个编译单位中存在的类型 （如结构） 和使用进行编译时[/clr](../../build/reference/clr-common-language-runtime-compilation.md)。  在这种情况下，请确保该类型在所有编译单位中具有相同的定义。  中列出的类型名称`error_message`。

Lnk2022 另一个可能的原因是链接器在不是指定给编译器在不同的位置找到元数据文件时 (与[#using](../../preprocessor/hash-using-directive-cpp.md) )。 确保元数据文件（.dll 或 .netmodule）在传递给链接器时与传递给编译器时位于相同的位置。

生成 ATL 应用程序，使用宏时`_ATL_MIXED`如果中至少一个使用在所有编译单位，所需。

## <a name="example"></a>示例

下面的示例定义一个空的类型。

```cpp
// LNK2022_a.cpp
// compile with: /clr /c
public ref class Test {};
```

## <a name="example"></a>示例

此示例演示不能链接两个源代码文件包含类型的名称相同但不同的定义。

下面的示例生成 LNK2022。

```cpp
// LNK2022_b.cpp
// compile with: LNK2022_a.cpp /clr /LD
// LNK2022 expected
public ref class Test {
   void func() {}
   int var;
};
```