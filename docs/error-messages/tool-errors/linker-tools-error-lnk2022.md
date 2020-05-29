---
title: 链接器工具错误 LNK2022
ms.date: 11/04/2016
f1_keywords:
- LNK2022
helpviewer_keywords:
- LNK2022
ms.assetid: d2128c73-dde3-4b8e-a9b2-0a153acefb3b
ms.openlocfilehash: d30dad6f8ad146ff467eb4eaf32b21dd6950d25f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194637"
---
# <a name="linker-tools-error-lnk2022"></a>链接器工具错误 LNK2022

> 元数据操作失败（*HRESULT*）： *error_message*

链接器在合并元数据时检测到错误。 必须解析元数据错误才能成功链接。

诊断此问题的一种方法是对对象文件运行**ildasm 标记**，以查找在 `error_message`中列出了令牌的类型，并查找不同之处。  在元数据中，具有相同名称的两个不同类型是无效的，即使 LayoutType 属性不同也是如此。

LNK2022 的一个原因是，类型（如结构）存在于具有相同名称的多个 compiland 中，但存在有冲突的定义，并且使用[/clr](../../build/reference/clr-common-language-runtime-compilation.md)进行编译时。  在这种情况下，请确保在所有 compiland 中该类型具有相同的定义。  类型名称在 `error_message`中列出。

LNK2022 的另一个可能原因是链接器在与指定给编译器的位置不同的位置找到元数据文件（使用[#using](../../preprocessor/hash-using-directive-cpp.md) ）。 确保元数据文件（.dll 或 .netmodule）在传递给链接器时与传递给编译器时位于相同的位置。

生成 ATL 应用程序时，如果在至少一个 compiland 中使用宏 `_ATL_MIXED`，则必须在所有中使用。

## <a name="example"></a>示例

下面的示例定义了一个空类型。

```cpp
// LNK2022_a.cpp
// compile with: /clr /c
public ref class Test {};
```

## <a name="example"></a>示例

此示例显示不能链接两个包含同名但不同定义的类型的源代码文件。

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
