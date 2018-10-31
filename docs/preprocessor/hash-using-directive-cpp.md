---
title: '#using 指令 (C + + CLI) |Microsoft Docs'
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- friend_as_cpp
- '#using'
- friend_as
- '#using_cpp'
dev_langs:
- C++
helpviewer_keywords:
- using directive (#using)
- '#using directive'
- LIBPATH environment variable
- preprocessor, directives
ms.assetid: 870b15e5-f361-40a8-ba1c-c57d75c8809a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 23e3447538590ec6a0e9392800bc6638900c6d6d
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808688"
---
# <a name="using-directive-ccli"></a>#using 指令 (C + + CLI)

将元数据导入编译的程序[/clr](../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="syntax"></a>语法

```
#using file [as_friend]
```

### <a name="parameters"></a>参数

文件<br/>
MSIL .dll、.exe、.netmodule 或 .obj。例如，应用于对象的

`#using <MyComponent.dll>`

*as_friend*<br/>
指定类型中所有*文件*可访问。 有关详细信息，请参阅[友元程序集 （c + +）](../dotnet/friend-assemblies-cpp.md)。

## <a name="remarks"></a>备注

*文件*可以是为其托管的数据和托管的结构导入的 Microsoft 中间语言 (MSIL) 文件。 如果.dll 文件包含程序集清单，然后导入此清单中引用的所有.dll，并且要生成的程序集将列出*文件*作为程序集引用的元数据中。

如果*文件*不包含程序集 (如果*文件*是一个模块) 如果不打算在当前 （程序集） 应用程序中使用的模块中的类型信息，我们可以选择指示，该模块是程序集; 的一部分使用[/ASSEMBLYMODULE](../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)。 然后，模块中的类型将可用于引用此程序集的任何应用程序。

若要使用的替代方法 **#using**是[/FU](../build/reference/fu-name-forced-hash-using-file.md)编译器选项。

.exe 程序集传递给 **#using**应编译使用.NET Visual Studio 编译器 （Visual Basic 或 Visual C# 中，例如） 之一。  尝试从使用 `/clr` 编译的 .exe 程序集导入元数据将导致文件加载异常。

> [!NOTE]
> 使用引用的组件 **#using**可以运行使用不同版本的导致产生意外的结果的客户端应用程序在编译时，导入的文件。

为了使编译器可以识别的程序集 （而不是模块） 中的类型，它需要强制解析类型，您可以执行此操作，例如，通过定义类型的实例。 如果从程序集中的类型继承有解析中的编译器，例如，程序集的类型名称的其他方法，类型名称就会知道到编译器。

导入从使用的源代码生成的元数据时[__declspec （thread)](../cpp/thread.md)，线程语义不会保留在元数据中。 例如，与声明的变量 **__declspec （thread)** 是.NET Framework 公共语言运行时，生成并通过导入的程序中编译 **#using**，将不再有 **__declspec （thread)** 对变量的语义。

导入所有引用的文件中的类型 （托管和本机） **#using**可用，但编译器则会将本机类型视为声明而非定义。

在使用 `/clr` 编译时，将自动引用 mscorlib.dll。

LIBPATH 环境变量指定该编译器尝试解析传递到文件的名称时，将搜索的目录 **#using**。

编译器将沿以下路径搜索引用：

- 中指定的路径 **#using**语句。

- 当前目录中。

- .NET Framework 系统目录。

- 与添加的目录[/AI](../build/reference/ai-specify-metadata-directories.md)编译器选项。

- LIBPATH 环境变量上的目录。

## <a name="example"></a>示例

如果您生成程序集 (C) 并引用自身引用其他程序集 (A) 的程序集 (B)，则不需要显式引用程序集 A，除非您在 C 中显式使用 A 的某个类型。

```cpp
// using_assembly_A.cpp
// compile with: /clr /LD
public ref class A {};
```

## <a name="example"></a>示例

```cpp
// using_assembly_B.cpp
// compile with: /clr /LD
#using "using_assembly_A.dll"
public ref class B {
public:
   void Test(A a) {}
   void Test() {}
};
```

## <a name="example"></a>示例

在下面的示例中，没有因不引用 using_assembly_A.dll 而导致的编译器错误，因为此程序不使用在 using_assembly_A.cpp 中定义的任一类型。

```cpp
// using_assembly_C.cpp
// compile with: /clr
#using "using_assembly_B.dll"
int main() {
   B b;
   b.Test();
}
```

## <a name="see-also"></a>请参阅

[预处理器指令](../preprocessor/preprocessor-directives.md)