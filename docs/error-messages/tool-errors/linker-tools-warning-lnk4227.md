---
title: 链接器工具警告 LNK4227 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4227
dev_langs:
- C++
helpviewer_keywords:
- LNK4227
ms.assetid: 941a0414-9964-4e02-8487-f9daa42ef7f9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 28bcf242e48046278030ec4259b7ae3edd1c4a61
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088860"
---
# <a name="linker-tools-warning-lnk4227"></a>链接器工具警告 LNK4227

> 元数据操作警告 (*HRESULT*): *warning_message*

合并时，链接器检测到元数据的差异：

- 一个或多个引用的程序集与当前正在生成的程序集。

- 一个或多个源代码文件编译中。

如果具有相同名称但以不同的方式声明的参数信息的两个全局函数例如，可能会导致 LNK4227 （即，声明不是所有编译单位中保持一致）。 使用 ildasm.exe /TEXT /METADATA *object_file*上每个.obj 文件中以查看类型有何不同。

LNK4227 还可由其他工具的报告问题。 搜索的详细信息的警告消息。

必须修复的元数据问题要解决此警告。

## <a name="example"></a>示例

引用的程序集进行签名以不同的方式与引用它的程序集时，将生成 LNK4227。

下面的示例生成 LNK4227:

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

格式不正确的版本号传递到程序集特性时，还可以生成 LNK4227。  * 表示法是特定于`AssemblyVersionAttribute`。  若要解决此警告，请使用仅统计中的行版本特性而不`AssemblyVersionAttribute`。

下面的示例生成 LNK4227:

```cpp
// LNK4227e.cpp
// compile with: /clr /LD /W1
using namespace System::Reflection;
[assembly:AssemblyVersionAttribute("2.3.*")];   // OK
[assembly:AssemblyFileVersionAttribute("2.3.*")];   // LNK4227
// try the following line instead
// [assembly:AssemblyFileVersionAttribute("2.3")];
```