---
title: '#using 指令 (C++/CLI)'
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
ms.openlocfilehash: 0da255957e92a570750da2687bf1444df2e6ab13
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219425"
---
# <a name="using-directive-ccli"></a>#using 指令（c + +/CLI）

将元数据导入使用[/clr](../build/reference/clr-common-language-runtime-compilation.md)编译的程序中。

## <a name="syntax"></a>语法

> **`#using`***file* [ **`as_friend`** ]

### <a name="parameters"></a>参数

*文件*\
Microsoft 中间语言（MSIL） *`.dll`* 、 *`.exe`* 、 *`.netmodule`* 或 *`.obj`* 文件。 例如，

`#using <MyComponent.dll>`

**`as_friend`**\
指定*文件*中的所有类型都是可访问的。 有关详细信息，请参阅[友元程序集（c + +）](../dotnet/friend-assemblies-cpp.md)。

## <a name="remarks"></a>备注

*文件*可以是为其托管数据和托管构造导入的 Microsoft 中间语言（MSIL）文件。 如果 DLL 包含程序集清单，则将导入清单中引用的所有 Dll。 正在生成的程序集将在元数据中列出*文件*作为程序集引用。

*文件*中不包含程序集（*文件*是模块），并且不想使用当前（程序集）应用程序中的模块的类型信息。 您可以使用[/ASSEMBLYMODULE](../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)指示该模块是程序集的一部分。 然后，模块中的类型将可用于引用此程序集的任何应用程序。

使用的替代方法 **`#using`** 是[/FU](../build/reference/fu-name-forced-hash-using-file.md)编译器选项。

传递给的 .exe 程序集 **`#using`** 应使用一个 .Net Visual Studio 编译器（例如 Visual Basic 或 Visual c #）进行编译。  如果尝试从使用编译的 .exe 程序集导入元数据， **`/clr`** 将导致文件加载异常。

> [!NOTE]
> 用引用的组件 **`#using`** 可以使用编译时导入的文件的不同版本运行，从而导致客户端应用程序产生意外的结果。

为了使编译器能够识别程序集中的类型（而不是模块），需要强制解析该类型。 例如，可以通过定义类型的实例来强制执行此方法。 还可以通过其他方式解析编译器程序集中的类型名称。 例如，如果从程序集中的某个类型继承，则该类型名称将成为编译器已知的名称。

导入从使用的源代码生成的元数据时 [`__declspec(thread)`](../cpp/thread.md) ，线程语义不会保留在元数据中。 例如，使用在 **`__declspec(thread)`** 为 .NET Framework 公共语言运行时生成并随后通过导入的程序中编译的程序进行编译的变量 **`#using`** 不会 **`__declspec(thread)`** 对变量进行语义。

引用的文件中的所有导入类型（托管和本机） **`#using`** 都可用，但编译器将本机类型视为声明，而不是定义。

在编译时，将自动引用 mscorlib.dll **`/clr`** 。

LIBPATH 环境变量指定编译器解析传递到的文件名时要搜索的目录 **`#using`** 。

编译器会搜索以下路径中的引用：

- 语句中指定的路径 **`#using`** 。

- 当前目录。

- .NET Framework 系统目录。

- 随编译器选项一起添加的目录 [`/AI`](../build/reference/ai-specify-metadata-directories.md) 。

- LIBPATH 环境变量上的目录。

## <a name="example"></a>示例

可以生成引用第二个程序集的程序集，该程序集本身引用第三个程序集。 只需显式使用第三个程序集类型之一时，才必须从第一个程序集显式引用该程序集。

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

在下面的示例中，编译器不会报告有关引用*using_assembly_A.dll*的错误，因为程序不使用*using_assembly_A*中定义的任何类型。

```cpp
// using_assembly_C.cpp
// compile with: /clr
#using "using_assembly_B.dll"
int main() {
   B b;
   b.Test();
}
```

## <a name="see-also"></a>另请参阅

[预处理器指令](../preprocessor/preprocessor-directives.md)
