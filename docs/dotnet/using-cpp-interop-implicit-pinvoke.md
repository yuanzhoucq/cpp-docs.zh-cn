---
title: "使用 c + + 互操作 (隐式 PInvoke) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 78d104a41f052f994a19ebe359c8d3e557274783
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="using-c-interop-implicit-pinvoke"></a>使用 C++ 互操作（隐式 PInvoke）
Visual c + + 不同于其他.NET 语言，具有在同一应用程序和甚至同一文件中允许存在托管和非托管代码的互操作性支持 (与[managed、 unmanaged](../preprocessor/managed-unmanaged.md)杂注)。 这允许 Visual c + + 开发人员将.NET 功能集成到现有 Visual c + + 应用程序，而不影响应用程序的其余部分。  
  
 你还可以调用非托管的函数从托管编译单位使用[dllexport、 dllimport](../cpp/dllexport-dllimport.md)。  
  
 当您不需要指定如何将封送函数参数，或任何可在显式调用 DllImportAttribute 时指定的其他详细信息时，隐式 PInvoke 非常有用。  
  
 Visual c + + 提供托管和非托管函数进行互操作的两种的方法：  
  
-   [在 C++ 中使用显式 PInvoke（DllImport 特性）](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)  
  
 显式 PInvoke 支持由.NET Framework，以及在大多数.NET 语言中可用。 但正如其名，c + + 互操作是特定于 Visual c + +。  
  
## <a name="c-interop"></a>C++ 互操作  
 C + + 互操作是通过显式 PInvoke 建议，因为它提供更好地类型安全单调乏味通常较低，来实现，是多 forgiving 如果非托管的 API 将修改，并使性能增强功能可能不适用于显式PInvoke。 但是，c + + 互操作不可能如果非托管的源代码不可用。  
  
## <a name="c-com-interop"></a>C++ COM 互操作  
 当涉及到与 COM 组件进行互操作时，Visual c + + 支持的互操作性功能提供其他.NET 语言有特定的优势。 而不会限定的.NET framework 的限制[Tlbimp.exe （类型库导入程序）](/dotnet/framework/tools/tlbimp-exe-type-library-importer)，如对数据类型以及强制公开的每个 COM 接口的每个成员的有限支持，c + + 互操作允许 COM要访问在组件将和不需要单独的互操作程序集。 有关详细信息，请参阅[通过.NET 使用 COM](http://msdn.microsoft.com/en-us/03976661-6278-4227-a6c1-3b3315502c15)。  
  
## <a name="blittable-types"></a>通用类型  
 有关使用简单、 内部函数的类型的非托管 Api (请参阅[本机结构中和非 Blittable 类型](http://msdn.microsoft.com/Library/d03b050e-2916-49a0-99ba-f19316e5c1b3))，无需进行特殊编码是必需的因为这些数据类型具有相同的表示在内存中，但需要更复杂的数据类型显式数据封送处理。 有关示例，请参阅[如何： 从托管代码使用 PInvoke 调用本机 Dll](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md)。  
  
## <a name="example"></a>示例  
  
```  
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
  
-   [如何：使用 C++ 互操作封送 ANSI 字符串](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)  
  
-   [如何：使用 C++ 互操作封送 Unicode 字符串](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)  
  
-   [如何：使用 C++ 互操作封送 COM 字符串](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)  
  
-   [如何：使用 C++ 互操作封送结构](../dotnet/how-to-marshal-structures-using-cpp-interop.md)  
  
-   [如何：使用 C++ 互操作封送数组](../dotnet/how-to-marshal-arrays-using-cpp-interop.md)  
  
-   [如何：使用 C++ 互操作封送回调和委托](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)  
  
-   [如何：使用 C++ 互操作封送嵌入式指针](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)  
  
-   [如何：访问 System::String 中的字符](../dotnet/how-to-access-characters-in-a-system-string.md)  
  
-   [如何：将 char * 字符串转换为 System::Byte 数组](../dotnet/how-to-convert-char-star-string-to-system-byte-array.md)  
  
-   [如何： 将 system:: string 转换为 wchar_t * 或 char\*](../dotnet/how-to-convert-system-string-to-wchar-t-star-or-char-star.md)  
  
-   [如何：将 System::String 转换为标准字符串](../dotnet/how-to-convert-system-string-to-standard-string.md)  
  
-   [如何：将标准字符串转换为 System::String](../dotnet/how-to-convert-standard-string-to-system-string.md)  
  
-   [如何：获取字节数组的指针](../dotnet/how-to-obtain-a-pointer-to-byte-array.md)  
  
-   [如何：将非托管资源加载到一个字节数组](../dotnet/how-to-load-unmanaged-resources-into-a-byte-array.md)  
  
-   [如何：修改本机函数中的引用类](../dotnet/how-to-modify-reference-class-in-a-native-function.md)  
  
-   [如何：确定映像为本机映像还是 CLR 映像](../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)  
  
-   [如何：向全局程序集缓存添加本机 DLL](../dotnet/how-to-add-native-dll-to-global-assembly-cache.md)  
  
-   [如何：在本机类型中保存对值类型的引用](../dotnet/how-to-hold-reference-to-value-type-in-native-type.md)  
  
-   [如何：在非托管内存中保存对象引用](../dotnet/how-to-hold-object-reference-in-unmanaged-memory.md)  
  
-   [如何： 检测 /clr 编译](../dotnet/how-to-detect-clr-compilation.md)  
  
-   [如何：在 System::Guid 与 _GUID 之间进行转换](../dotnet/how-to-convert-between-system-guid-and-guid.md)  
  
-   [如何：指定 out 参数](../dotnet/how-to-specify-an-out-parameter.md)  
  
-   [如何： 在 /clr 编译中使用本机类型](../dotnet/how-to-use-a-native-type-in-a-clr-compilation.md)  
  
-   [如何：使用本机类型声明句柄](../dotnet/how-to-declare-handles-in-native-types.md)  
  
-   [如何：包装本机类以供 C# 使用](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)  
  
 有关在互操作方案中使用委托的信息，请参阅[委托 （c + + 组件扩展）](../windows/delegate-cpp-component-extensions.md)。  
  
## <a name="see-also"></a>请参阅  
 [从托管代码调用本机函数](../dotnet/calling-native-functions-from-managed-code.md)