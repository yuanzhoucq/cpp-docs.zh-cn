---
title: 使用 C++ 互操作（隐式 PInvoke）
ms.date: 11/04/2016
helpviewer_keywords:
- blittable types [C++]
- platform invoke [C++], implicit
- interop [C++], features
- data marshaling [C++], C++ Interop features
- porting [C++], C++ native to .NET
- COM interfaces [C++]
- implicit platform invoke
- examples [C++], interoperability
- types [C++], blittable
- marshaling [C++], C++ Interop features
- platform invoke [C++], examples
- interoperability [C++]
- C++ Interop
- interoperability [C++], Implicit PInvoke
- C++, interop
- C++ COM Interop
- .NET [C++], porting C++ native to
ms.assetid: 5f710bf1-88ae-4c4e-8326-b3f0b7c4c68a
ms.openlocfilehash: aaa07373b7dd22807290ceefa9197b4013c61fe5
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58778229"
---
# <a name="using-c-interop-implicit-pinvoke"></a>使用 C++ 互操作（隐式 PInvoke）

不同于其他.NET 语言，Visual c + + 具有在同一应用程序，即使在同一文件中允许存在的托管和非托管代码的互操作性支持 (与[managed、 unmanaged](../preprocessor/managed-unmanaged.md)杂注)。 这允许 Visual c + + 开发人员将.NET 功能集成到现有的 Visual c + + 应用程序，而不影响其他应用程序。

此外可以从托管的模块使用调用非托管的函数[dllexport、 dllimport](../cpp/dllexport-dllimport.md)。

不需要指定如何将封送函数参数，或任何显式调用 DllImportAttribute 时可以指定的其他详细信息时，隐式 PInvoke 很有用。

Visual c + + 提供托管和非托管函数进行互操作的两种的方法：

- [在 C++ 中使用显式 PInvoke（DllImport 特性）](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)

显式 PInvoke.NET Framework 中受支持，可在大多数与.NET 语言中。 但正如其名，c + + 互操作是特定于 Visual c + +。

## <a name="c-interop"></a>C++ 互操作

C + + 互操作是通过显式 PInvoke 建议，因为它更好地提供类型安全性，是通常变得更加轻松实现，如果非托管的 API 被修改，并使性能增强功能可能不可能实现的显式，则更严格PInvoke。 但是，c + + 互操作不能如果非托管的源代码不可用。

## <a name="c-com-interop"></a>C++ COM 互操作

与 COM 组件进行互操作时，支持 Visual c + + 的互操作性功能提供相比其他.NET 语言的特定优势。 而不是被限制为.NET Framework 的限制[Tlbimp.exe （类型库导入程序）](/dotnet/framework/tools/tlbimp-exe-type-library-importer)，c + + 互操作的数据类型和公开的每个 COM 接口的每个成员的行为必需的有限支持，如允许 COM要访问的组件将并不需要单独的互操作程序集。 与不同的是 Visual Basic 和C#，Visual c + + 可以使用 COM 对象直接使用常规的 COM 机制 (如**CoCreateInstance**并**QueryInterface**)。 这可能是由于会导致编译器自动插入转换代码来回移动从托管到非托管函数的 c + + 互操作功能。

使用 c + + 互操作，COM 组件可用作通常使用或它们可以在 c + + 类中使用换行。 这些包装器类调用自定义运行时可调用包装器，或 Crcw，并且它们具有通过直接在应用程序代码中使用 COM 的两个优势：

- 可以从 Visual c + + 之外的语言中使用生成的类。

- 可以从托管客户端代码隐藏的 COM 接口的详细信息。 .NET 数据类型来代替本机类型，并可以 CRCW 内部以透明方式执行数据封送处理的详细信息。

无论是否直接或通过 CRCW 使用 COM，必须封送不属于简单，可直接复制类型的参数类型。

## <a name="blittable-types"></a>可直接复制类型

有关使用简单、 内部类型的非托管 Api (请参阅[Blittable 和非 Blittable 类型](/dotnet/framework/interop/blittable-and-non-blittable-types))，无需特殊编码，因为这些数据类型在内存中，具有相同的表示形式，但需要更复杂的数据类型显式数据封送处理。 有关示例，请参见 [如何：使用 PInvoke 从托管代码调用本机 Dll](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md)。

## <a name="example"></a>示例

```cpp
// vcmcppv2_impl_dllimp.cpp
// compile with: /clr:pure user32.lib
using namespace System::Runtime::InteropServices;

// Implicit DLLImport specifying calling convention
extern "C" int __stdcall MessageBeep(int);

// explicit DLLImport needed here to use P/Invoke marshalling because
// System::String ^ is not the type of the first parameter to printf
[DllImport("msvcrt.dll", EntryPoint = "printf", CallingConvention = CallingConvention::Cdecl,  CharSet = CharSet::Ansi)]
// or just
// [DllImport("msvcrt.dll")]
int printf(System::String ^, ...);

int main() {
   // (string literals are System::String by default)
   printf("Begin beep\n");
   MessageBeep(100000);
   printf("Done\n");
}
```

```Output
Begin beep
Done
```

## <a name="in-this-section"></a>本节内容

- [如何：使用 C++ 互操作封送 ANSI 字符串](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

- [如何：使用 C++ 互操作封送 Unicode 字符串](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [如何：使用 C++ 互操作封送 COM 字符串](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

- [如何：使用 C++ 互操作封送结构](../dotnet/how-to-marshal-structures-using-cpp-interop.md)

- [如何：使用 C++ 互操作封送数组](../dotnet/how-to-marshal-arrays-using-cpp-interop.md)

- [如何：使用 C++ 互操作封送回调和委托](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)

- [如何：使用 C++ 互操作封送嵌入式指针](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)

- [如何：访问 System::String 中的字符](../dotnet/how-to-access-characters-in-a-system-string.md)

- [如何：将 char* 字符串转换为 System::Byte 数组](../dotnet/how-to-convert-char-star-string-to-system-byte-array.md)

- [如何：将 system:: string 转换为 wchar_t * 或 char\*](../dotnet/how-to-convert-system-string-to-wchar-t-star-or-char-star.md)

- [如何：将 System::String 转换为标准字符串](../dotnet/how-to-convert-system-string-to-standard-string.md)

- [如何：将标准字符串转换为 System::String](../dotnet/how-to-convert-standard-string-to-system-string.md)

- [如何：获取指向字节数组的指针](../dotnet/how-to-obtain-a-pointer-to-byte-array.md)

- [如何：将非托管资源加载到字节数组中](../dotnet/how-to-load-unmanaged-resources-into-a-byte-array.md)

- [如何：修改本机函数中的引用类](../dotnet/how-to-modify-reference-class-in-a-native-function.md)

- [如何：确定是本机映像还是 CLR 映像](../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)

- [如何：向全局程序集缓存添加本机 DLL](../dotnet/how-to-add-native-dll-to-global-assembly-cache.md)

- [如何：在本机类型中保留对值类型的引用](../dotnet/how-to-hold-reference-to-value-type-in-native-type.md)

- [如何：在非托管内存中保留对象引用](../dotnet/how-to-hold-object-reference-in-unmanaged-memory.md)

- [如何：检测 /clr 编译](../dotnet/how-to-detect-clr-compilation.md)

- [如何：在 System::Guid 与 _GUID 之间转换](../dotnet/how-to-convert-between-system-guid-and-guid.md)

- [如何：指定 out 参数](../dotnet/how-to-specify-an-out-parameter.md)

- [如何：在 /clr 编译中使用本机类型](../dotnet/how-to-use-a-native-type-in-a-clr-compilation.md)

- [如何：在本机类型中声明句柄](../dotnet/how-to-declare-handles-in-native-types.md)

- [如何：包装本机类以供 C# 使用](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)

在互操作方案中使用委托的信息，请参阅[委托 （c + + 组件扩展）](../extensions/delegate-cpp-component-extensions.md)。

## <a name="see-also"></a>请参阅

- [从托管代码调用本机函数](../dotnet/calling-native-functions-from-managed-code.md)
