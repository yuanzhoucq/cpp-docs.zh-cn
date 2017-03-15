---
title: "从托管代码调用本机函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "从托管代码调用本机函数"
  - "互操作 [C++], 从托管代码调用本机函数"
  - "互操作性 [C++], 从托管代码调用本机函数"
  - "托管代码 [C++], 互操作性"
  - "从托管代码调用的本机函数 [C++]"
  - "平台调用 [C++], 互操作性"
ms.assetid: 982cef18-20d9-42b4-8242-a77fa65f2e36
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# 从托管代码调用本机函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

公共语言运行时提供平台调用服务（Platform Invocation Services，简称 PInvoke），使托管代码能够调用本机动态链接库 \(DLL\) 中的 C 样式函数。  相同的数据封送处理被用于 COM 与运行时的互操作，以及“它就是能工作”（It Just Works，简称 IJW）机制。  
  
 有关详细信息，请参阅：  
  
-   [在 C\+\+ 中使用显式 PInvoke（DllImport 特性）](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)  
  
-   [使用 C\+\+ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)  
  
-   [A Closer Look at Platform Invoke](http://msdn.microsoft.com/zh-cn/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)  
  
 本节中的示例仅演示了 `PInvoke` 的使用方法。  `PInvoke` 可以简化自定义数据封送处理，这是由于是在特性中以声明方式提供封送处理信息，而不是编写过程性的封送处理代码。  
  
> [!NOTE]
>  封送处理库以优化方式为在本机和托管环境之间封送数据提供了一个替代方法。  有关封送处理库的更多信息，请参见 [C\+\+ 中的封送处理概述](../dotnet/overview-of-marshaling-in-cpp.md)。  封送处理库仅适用于数据，不适用于函数。  
  
## PInvoke 和 DllImport 特性  
 下面的示例演示了 Visual C\+\+ 程序中 `PInvoke` 的用法。  本机函数的 puts 定义在 msvcrt.dll 中。  DllImport 特性用于 puts 的声明。  
  
```  
// platform_invocation_services.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
[DllImport("msvcrt", CharSet=CharSet::Ansi)]  
extern "C" int puts(String ^);  
  
int main() {  
   String ^ pStr = "Hello World!";  
   puts(pStr);  
}  
```  
  
 下面的示例等效于前一个示例，只是使用了 IJW。  
  
```  
// platform_invocation_services_2.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#include <stdio.h>  
  
int main() {  
   String ^ pStr = "Hello World!";  
   char* pChars = (char*)Marshal::StringToHGlobalAnsi(pStr).ToPointer();   
   puts(pChars);  
  
   Marshal::FreeHGlobal((IntPtr)pChars);  
}  
```  
  
### IJW 的优点  
  
-   无需编写程序使用的非托管 API 的 `DLLImport` 特性声明。  只需包含头文件并与导入库链接即可。  
  
-   IJW 机制稍快一些，例如，IJW 存根无需检查是否需要锁定或复制数据项，因为这项任务是由开发人员显式完成的。  
  
-   它清楚地说明了性能问题。  这种情况下，您事实上要将 Unicode 字符串转换为 ANSI 字符串，并且有伴随的内存分配和解除分配。  这种情况下，使用 IJW 编写代码的开发人员将发现调用 `_putws` 并使用 `PtrToStringChars` 可获得更佳的性能。  
  
-   如果调用使用相同数据的许多非托管 API，则对其进行一次封送处理并传递经过封送处理的副本，比每次都重新进行封送处理要高效得多。  
  
### IJW 的缺点  
  
-   封送处理必须在代码中显式指定，而不是通过特性指定（特性通常具有适当的默认值）。  
  
-   封送处理代码是内联的，因而在应用程序逻辑流中更具侵略性。  
  
-   由于显式封送处理 API 针对 32 位到 64 位可移植性返回 `IntPtr` 类型，因此必须使用额外的 `ToPointer` 调用。  
  
 由 C\+\+ 公开的特定方法更为高效、显式，其代价是具有附加的复杂性。  
  
 如果应用程序主要使用非托管数据类型，或者调用的非托管 API 比 .NET Framework API 多，则建议使用 IJW 功能。  若要在托管代码占主体的应用程序中偶尔调用非托管 API，在进行选择时需要更为慎重。  
  
## PInvoke 与 Windows API  
 对于调用 Windows 中的函数来说，PInvoke 很方便。  
  
 在本例中，Visual C\+\+ 程序与隶属 Win32 API 的 MessageBox 函数可互操作。  
  
```  
// platform_invocation_services_4.cpp  
// compile with: /clr /c  
using namespace System;  
using namespace System::Runtime::InteropServices;  
typedef void* HWND;  
[DllImport("user32", CharSet=CharSet::Ansi)]  
extern "C" int MessageBox(HWND hWnd, String ^ pText, String ^ pCaption, unsigned int uType);  
  
int main() {  
   String ^ pText = "Hello World! ";  
   String ^ pCaption = "PInvoke Test";  
   MessageBox(0, pText, pCaption, 0);  
}  
```  
  
 输出是标题为 PInvoke Test 的消息框，其中包含文本 Hello World\!。  
  
 PInvoke 还使用封送处理信息在 DLL 中查找函数。  在 user32.dll 中，实际上没有 MessageBox 函数，但 CharSet\=CharSet::Ansi 使 PInvoke 能够使用 MessageBoxA（ANSI 版本），而非 MessageBoxW（Unicode 版本）。  通常，我们建议使用非托管 API 的 Unicode 版本，因为它消除了从 .NET Framework 字符串对象的本机 Unicode 格式转换为 ANSI 格式的系统开销。  
  
## 何时不使用 PInvoke  
 并非 DLL 中的所有 C 样式函数都适合使用 PInvoke。  例如，假设 mylib.dll 中有一个函数 MakeSpecial，其函数声明如下：  
  
 `char * MakeSpecial(char * pszString);`  
  
 如果要在 Visual C\+\+ 应用程序中使用 PInvoke，则可能需要编写类似以下内容的代码：  
  
 `[DllImport("mylib")]`  
  
 `extern "C" String * MakeSpecial([MarshalAs(UnmanagedType::LPStr)] String ^);`  
  
 这里的难点是无法删除由 MakeSpecial 返回的非托管字符串的内存。  通过 PInvoke 调用的其他函数返回一个指向内部缓冲区的指针，该缓冲区无需由用户释放。  这种情况下，显然应使用 IJW 功能。  
  
## PInvoke 的局限性  
 无法从本机函数返回以前用作参数的完全相同的指针。  如果本机函数返回的指针已由 PInvoke 封送到该函数，可能紧跟着发生内存损坏和异常。  
  
```  
__declspec(dllexport)  
char* fstringA(char* param) {  
   return param;  
}  
```  
  
 下面的示例说明了此问题，即使程序看起来给出了正确的输出，输出也是来自已经释放的内存。  
  
```  
// platform_invocation_services_5.cpp  
// compile with: /clr /c  
using namespace System;  
using namespace System::Runtime::InteropServices;  
#include <limits.h>  
  
ref struct MyPInvokeWrap {  
public:  
   [ DllImport("user32.dll", EntryPoint = "CharLower", CharSet = CharSet::Ansi) ]  
   static String^ CharLower([In, Out] String ^);  
};  
  
int main() {  
   String ^ strout = "AabCc";  
   Console::WriteLine(strout);  
   strout = MyPInvokeWrap::CharLower(strout);  
   Console::WriteLine(strout);  
}  
```  
  
## 封送处理参数  
 使用 `PInvoke`，具有相同形式的托管类型和 C\+\+ 本机基元类型之间不需要封送处理。  例如，Int32 和 int 之间以及 Double 和 double 之间不需要封送处理。  
  
 不过，形式不同的类型之间必须进行封送处理。  这包括 char、string 和 struct 类型。  下表显示封送拆收器对各种类型使用的映射：  
  
|wtypes.h|Visual C\+\+|使用 \/clr 编译的 Visual C\+\+|公共语言运行时|  
|--------------|------------------|-------------------------------|-------------|  
|HANDLE|void \*|void \*|IntPtr、UIntPtr|  
|BYTE|unsigned char|unsigned char|Byte|  
|SHORT|short|short|Int16|  
|WORD|unsigned short|unsigned short|UInt16|  
|INT|int|int|Int32|  
|UINT|unsigned int|unsigned int|UInt32|  
|LONG|long|long|Int32|  
|BOOL|long|bool|Boolean|  
|DWORD|unsigned long|unsigned long|UInt32|  
|ULONG|unsigned long|unsigned long|UInt32|  
|CHAR|char|char|Char|  
|LPCSTR|char \*|String ^ \[in\]、StringBuilder ^ \[in, out\]|String ^ \[in\]、StringBuilder ^ \[in, out\]|  
|LPCSTR|const char \*|String ^|String|  
|LPWSTR|wchar\_t \*|String ^ \[in\]、StringBuilder ^ \[in, out\]|String ^ \[in\]、StringBuilder ^ \[in, out\]|  
|LPCWSTR|const wchar\_t \*|String ^|String|  
|FLOAT|float|float|Single|  
|DOUBLE|double|double|Double|  
  
 如果将在运行时堆上分配的内存的地址传递给了非托管函数，封送拆收器会自动锁定该内存。  锁定可防止垃圾回收器在压缩期间移动分配的内存块。  
  
 在本主题前面给出的示例中，DllImport 的 CharSet 参数指定应如何封送托管字符串；在这种情况下，对于本机方面，它们应封送为 ANSI 字符串。  
  
 使用 MarshalAs 特性可以指定本机函数的各个参数的封送处理信息。  对 String \* 参数进行封送处理有多种选项：BStr、ANSIBStr、TBStr、LPStr、LPWStr 和 LPTStr。  默认选项为 LPStr。  
  
 在本例中，字符串被封送为双字节 Unicode 字符字符串 LPWStr。  输出的是 Hello World\! 的第一个字母，原因是封送的字符串的第二个字节为 null，并将此解释为字符串尾标记。  
  
```  
// platform_invocation_services_3.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
[DllImport("msvcrt", EntryPoint="puts")]  
extern "C" int puts([MarshalAs(UnmanagedType::LPWStr)] String ^);  
  
int main() {  
   String ^ pStr = "Hello World!";  
   puts(pStr);  
}  
```  
  
 MarshalAs 特性位于 System::Runtime::InteropServices 命名空间中。  该特性可与其他数据类型（如数组）一起使用。  
  
 如本主题前面所述，封送处理库在本机和托管环境之间封送数据提供了一个新的优化方法。  有关详细信息，请参阅[C\+\+ 中的封送处理概述](../dotnet/overview-of-marshaling-in-cpp.md)。  
  
## 性能注意事项  
 对于每次调用，PInvoke 的系统开销在 10 到 30 条 x86 指令之间。  除这些固定开销外，封送处理也会导致额外的系统开销。  在托管和非托管代码中，具有相同表示形式的可直接复制到本机结构中的各种类型之间没有封送处理开销。  例如，int 和 Int32 之间的转换没有开销。  
  
 为了提高性能，应使尽可能少的 PInvoke 调用封送尽可能多的数据，而不是发出更多调用，但每个调用封送更少数据。  
  
## 请参阅  
 [本机和 .NET 的互操作性](../dotnet/native-and-dotnet-interoperability.md)