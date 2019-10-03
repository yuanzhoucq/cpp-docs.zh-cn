---
title: '#using 指令 (C++/cli)'
ms.date: 08/29/2019
f1_keywords:
- friend_as_cpp
- '#using'
- friend_as
- '#using_cpp'
helpviewer_keywords:
- using directive (#using)
- '#using directive'
- LIBPATH environment variable
- preprocessor, directives
ms.assetid: 870b15e5-f361-40a8-ba1c-c57d75c8809a
ms.openlocfilehash: 5dae5c277055157aef5451c19ee020fbbd2aaccb
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220196"
---
# <a name="using-directive-ccli"></a>#using 指令 (C++/cli)

将元数据导入使用[/clr](../build/reference/clr-common-language-runtime-compilation.md)编译的程序中。

## <a name="syntax"></a>语法

> **#using** *文件* [ **as_friend**]

### <a name="parameters"></a>参数

*文件*\
MSIL .dll、.exe、.netmodule 或 .obj。例如，应用于对象的

`#using <MyComponent.dll>`

**as_friend**\
指定*文件*中的所有类型都是可访问的。 有关详细信息, 请参阅[友元C++程序集 ()](../dotnet/friend-assemblies-cpp.md)。

## <a name="remarks"></a>备注

*文件*可以是为其托管数据和托管构造导入的 Microsoft 中间语言 (MSIL) 文件。 如果 .dll 文件包含程序集清单, 则将导入清单中引用的所有 .dll, 并将元数据中的*文件*作为程序集引用列出。

如果*文件*不包含程序集 (如果*文件*是模块), 并且不打算在当前 (程序集) 应用程序中使用模块中的类型信息, 则可以选择仅指示该模块是程序集的一部分;请使用[/ASSEMBLYMODULE](../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)。 然后，模块中的类型将可用于引用此程序集的任何应用程序。

使用 **#using**的替代方法是[/FU](../build/reference/fu-name-forced-hash-using-file.md)编译器选项。

传递给 **#using**的 .exe 程序集应使用某个 .Net Visual Studio 编译器 (例如 Visual Basic 或视觉对象C#) 进行编译。  尝试从使用 `/clr` 编译的 .exe 程序集导入元数据将导致文件加载异常。

> [!NOTE]
> 使用 **#using**引用的组件可在编译时导入的文件的不同版本中运行, 从而使客户端应用程序产生意外的结果。

为了使编译器能够识别程序集中的类型 (而不是模块), 需要强制解析该类型。 例如, 可以通过定义类型的实例来强制执行此方法。 还可以通过其他方式解析编译器程序集中的类型名称。 例如, 如果从程序集中的某个类型继承, 则该类型名称将成为编译器已知的名称。

导入从使用[__declspec (thread)](../cpp/thread.md)的源代码生成的元数据时, 线程语义不会保留在元数据中。 例如, 使用 **__declspec (thread)** 声明的变量, 在为 .NET Framework 公共语言运行时生成的程序中编译, 然后通过 **#using**导入, 对该变量不具有 **__declspec (thread)** 语义。

**#Using**引用的文件中的所有导入类型 (托管和本机) 都可用, 但编译器将本机类型视为声明, 而不是定义。

在使用 `/clr` 编译时，将自动引用 mscorlib.dll。

LIBPATH 环境变量指定当编译器解析传递给 **#using**的文件名时要搜索的目录。

编译器会搜索以下路径中的引用:

- 在 **#using**语句中指定的路径。

- 当前目录。

- .NET Framework 系统目录。

- 用[/AI](../build/reference/ai-specify-metadata-directories.md)编译器选项添加的目录。

- LIBPATH 环境变量上的目录。

## <a name="example"></a>示例

如果生成程序集 (C) 并引用本身引用另一个程序集 (A) 的程序集 (B), 则无需显式引用程序集 A, 除非显式使用 C 中的某个类型。

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

在下面的示例中, 没有引用*using_assembly_A*的编译器错误, 因为程序不使用*using_assembly_A*中定义的任何类型。

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
