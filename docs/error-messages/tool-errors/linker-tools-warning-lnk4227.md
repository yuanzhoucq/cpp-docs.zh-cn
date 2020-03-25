---
title: 链接器工具警告 LNK4227
ms.date: 11/04/2016
f1_keywords:
- LNK4227
helpviewer_keywords:
- LNK4227
ms.assetid: 941a0414-9964-4e02-8487-f9daa42ef7f9
ms.openlocfilehash: 7b75cff4f03370951245bde1b485d538ffdb4007
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182937"
---
# <a name="linker-tools-warning-lnk4227"></a>链接器工具警告 LNK4227

> 元数据操作警告（*HRESULT*）： *warning_message*

合并时，链接器检测到元数据差异：

- 具有当前正在生成的程序集的一个或多个引用的程序集。

- 编译中的一个或多个源代码文件。

例如，如果有两个名称相同但参数信息声明不同的全局函数（即，声明在所有 compiland 中都不一致），则可能导致 LNK4227。 在每个 .obj 文件上使用/TEXT/METADATA *object_file* ，以查看类型的不同之处。

LNK4227 还用于报告与其他工具有关的问题。 搜索警告消息以获取详细信息。

要解决此警告，必须修复元数据问题。

## <a name="example"></a>示例

当被引用的程序集的签名不同于引用它的程序集时，将生成 LNK4227。

下面的示例生成 LNK4227：

```cpp
// LNK4227.cpp
// compile with: /clr
using namespace System::Reflection;

[assembly:AssemblyDelaySignAttribute(false)];

int main() {}
```

然后

```cpp
// LNK4227b.cpp
// compile with: /clr LNK4227.cpp /FeLNK4227b.exe
using namespace System::Reflection;
using namespace System::Runtime::CompilerServices;

[assembly:AssemblyDelaySignAttribute(true)];
// Try the following line instead
// [assembly:AssemblyDelaySignAttribute(false)];

ref class MyClass
{
};
```

## <a name="example"></a>示例

如果将格式不正确的版本传递给程序集特性，也可以生成 LNK4227。  "*" 表示法特定于 `AssemblyVersionAttribute`。  若要解决此警告，请仅在 `AssemblyVersionAttribute`以外的版本属性中使用数字。

下面的示例生成 LNK4227：

```cpp
// LNK4227e.cpp
// compile with: /clr /LD /W1
using namespace System::Reflection;
[assembly:AssemblyVersionAttribute("2.3.*")];   // OK
[assembly:AssemblyFileVersionAttribute("2.3.*")];   // LNK4227
// try the following line instead
// [assembly:AssemblyFileVersionAttribute("2.3")];
```
