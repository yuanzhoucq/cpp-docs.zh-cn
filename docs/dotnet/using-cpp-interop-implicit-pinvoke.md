---
title: "使用 C++ 互操作（隐式 PInvoke） | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".NET [C++], 从 C++ 本机迁移"
  - "能直接复制到本机结构中的类型 [C++]"
  - "C++ COM 互操作"
  - "C++ 互操作"
  - "C++, 互操作"
  - "COM 接口 [C++]"
  - "数据封送处理 [C++], C++ 互操作功能"
  - "示例 [C++], 互操作性"
  - "隐式平台调用"
  - "互操作 [C++], 功能"
  - "互操作性 [C++]"
  - "互操作性 [C++], 隐式 PInvoke"
  - "封送处理 [C++], C++ 互操作功能"
  - "平台调用 [C++], 示例"
  - "平台调用 [C++], implicit"
  - "迁移 [C++], C++ 本机到 .NET"
  - "类型 [C++], 能直接复制到本机结构中"
ms.assetid: 5f710bf1-88ae-4c4e-8326-b3f0b7c4c68a
caps.latest.revision: 27
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 C++ 互操作（隐式 PInvoke）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

与其他 .NET 语言不同，Visual C\+\+ 支持互操作性，允许托管代码和非托管代码存在于同一个应用程序中，甚至存在于同一个文件中（使用 [managed、unmanaged](../preprocessor/managed-unmanaged.md) 杂注）。  Visual C\+\+ 开发人员可以通过此功能将 .NET 功能集成到现有 Visual C\+\+ 应用程序中，而不会干扰该应用程序的其余部分。  
  
 还可以使用 [dllexport、dllimport](../cpp/dllexport-dllimport.md) 从托管模块中调用非托管函数。  
  
 如果不需要指定封送函数参数的方式或显式调用 DllImportAttribute 时指定的任何其他详细信息，则隐式 PInvoke 非常有用。  
  
 Visual C\+\+ 为托管函数和非托管函数提供了两种交互操作方式：  
  
-   [在 C\+\+ 中使用显式 PInvoke（DllImport 特性）](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)  
  
 显式 PInvoke 受 .NET Framework 支持并且可用于大多数 .NET 语言。  但是顾名思义，C\+\+ Interop 特定于 Visual C\+\+。  
  
## C\+\+ Interop  
 推荐使用 C\+\+ Interop 而不是显式 PInvoke，因为 C\+\+ Interop 提供更好的类型安全性，通常实现起来比较有趣，更为常用（如果修改非托管 API），并且可能会实现显式 PInvoke 不可能实现的性能增强。  但是，如果非托管源代码不可用或使用 **\/clr:safe** 进行编译，则不可能使用 C\+\+ Interop（有关更多信息，请参见 [纯代码和可验证代码](../dotnet/pure-and-verifiable-code-cpp-cli.md)）。  
  
## C\+\+ COM 互操作  
 在与 COM 组件进行交互操作方面，Visual C\+\+ 支持的互操作性功能与其他 .NET 语言相比具有特别的优势。  C\+\+ Interop 不受限于 .NET Framework [Tlbimp.exe（类型库导入程序）](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md) 限制（如对数据类型的有限支持和强制公开每个 COM 接口的每个成员），而是允许随意访问 COM 组件，而且不需要单独的互操作程序集。  有关详细信息，请参阅[Using COM from .NET](http://msdn.microsoft.com/zh-cn/03976661-6278-4227-a6c1-3b3315502c15)。  
  
## 可直接复制到本机结构中的类型  
 对于使用简单内部类型（请参见 [可直接复制到本机结构中的类型和非直接复制到本机结构中的类型](../Topic/Blittable%20and%20Non-Blittable%20Types.md)）的非托管 API 而言，无需特殊编码，因为这些数据类型在内存中具有相同的表示形式，但是更复杂的数据类型需要显式数据封送处理。  有关示例，请参见[如何：使用 PInvoke 从托管代码调用本机 DLL](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md)。  
  
## 示例  
  
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
  
  **开始提示音**  
**已完成**   
## 本节内容  
  
-   [如何：使用 C\+\+ 互操作封送 ANSI 字符串](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)  
  
-   [如何：使用 C\+\+ 互操作封送 Unicode 字符串](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)  
  
-   [如何：使用 C\+\+ 互操作封送 COM 字符串](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)  
  
-   [如何：使用 C\+\+ 互操作封送结构](../dotnet/how-to-marshal-structures-using-cpp-interop.md)  
  
-   [如何：使用 C\+\+ 互操作封送数组](../dotnet/how-to-marshal-arrays-using-cpp-interop.md)  
  
-   [如何：使用 C\+\+ 互操作封送回调和委托](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)  
  
-   [如何：使用 C\+\+ 互操作封送嵌入式指针](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)  
  
-   [如何：访问 System::String 中的字符](../dotnet/how-to-access-characters-in-a-system-string.md)  
  
-   [如何：将 char \* 字符串转换为 System::Byte 数组](../dotnet/how-to-convert-char-star-string-to-system-byte-array.md)  
  
-   [如何：将 System::String 转换为 wchar\_t\* 或 char\*](../dotnet/how-to-convert-system-string-to-wchar-t-star-or-char-star.md)  
  
-   [如何：将 System::String 转换为标准字符串](../dotnet/how-to-convert-system-string-to-standard-string.md)  
  
-   [如何：将标准字符串转换为 System::String](../dotnet/how-to-convert-standard-string-to-system-string.md)  
  
-   [如何：获取字节数组的指针](../dotnet/how-to-obtain-a-pointer-to-byte-array.md)  
  
-   [如何：将非托管资源加载到一个字节数组](../dotnet/how-to-load-unmanaged-resources-into-a-byte-array.md)  
  
-   [如何：修改本机函数中的引用类](../dotnet/how-to-modify-reference-class-in-a-native-function.md)  
  
-   [如何：确定映像为本机映像还是 CLR 映像](../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)  
  
-   [如何：向全局程序集缓存添加本机 DLL](../dotnet/how-to-add-native-dll-to-global-assembly-cache.md)  
  
-   [如何：在本机类型中保存对值类型的引用](../dotnet/how-to-hold-reference-to-value-type-in-native-type.md)  
  
-   [如何：在非托管内存中保存对象引用](../dotnet/how-to-hold-object-reference-in-unmanaged-memory.md)  
  
-   [如何：检测 \/clr 编译](../dotnet/how-to-detect-clr-compilation.md)  
  
-   [如何：在 System::Guid 与 \_GUID 之间进行转换](../dotnet/how-to-convert-between-system-guid-and-guid.md)  
  
-   [如何：指定 out 参数](../dotnet/how-to-specify-an-out-parameter.md)  
  
-   [如何：在 \/clr 编译中使用本机类型](../dotnet/how-to-use-a-native-type-in-a-clr-compilation.md)  
  
-   [如何：使用本机类型声明句柄](../dotnet/how-to-declare-handles-in-native-types.md)  
  
-   [如何：包装本机类以供 C\# 使用](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)  
  
 有关在互操作方案中使用委托的信息，请参见 [委托](../windows/delegate-cpp-component-extensions.md)。  
  
## 请参阅  
 [从托管代码调用本机函数](../dotnet/calling-native-functions-from-managed-code.md)