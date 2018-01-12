---
title: "调用本机函数从托管代码 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- native functions called from managed code [C++]
- managed code [C++], interoperability
- platform invoke [C++], interoperability
- interoperabiliy [C++], calling native functions from managed code
- calling native functions from managed code
- interop [C++], calling native functions from managed code
ms.assetid: 982cef18-20d9-42b4-8242-a77fa65f2e36
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 159b80fcc015db2999309fe99e9617f7dcd409ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="calling-native-functions-from-managed-code"></a>从托管代码调用本机函数
公共语言运行时提供平台调用服务或 PInvoke，使托管代码能够调用本机动态链接库 (Dll) 中的 C 样式函数。 相同的数据封送处理既又用于与运行时和为"仅方式，"或 ijw 映像、 机制 COM 互操作性。  
  
 有关详细信息，请参见:  
  
-   [在 C++ 中使用显式 PInvoke（DllImport 特性）](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)  
  
-   [使用 C++ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)  
  
-   [详述平台调用](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)  
  
 此部分中的示例仅演示如何`PInvoke`可用。 `PInvoke`可以简化自定义的数据封送处理，这因为你提供以声明方式在属性而不是编写过程封送处理代码中的封送处理信息。  
  
> [!NOTE]
>  封送处理库提供了一种替代方式，以优化方式中的本机和托管环境之间封送数据。 请参阅[概述的封送处理在 c + +](../dotnet/overview-of-marshaling-in-cpp.md)有关封送处理库的详细信息。 封送处理库不仅数据，而不用于函数。  
  
## <a name="pinvoke-and-the-dllimport-attribute"></a>PInvoke 和 DllImport 特性  
 下面的示例演示如何使用`PInvoke`Visual c + + 程序中。 本机函数将在 msvcrt.dll 中定义。 DllImport 特性用于将的声明。  
  
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
  
 下面的示例等效于上面示例中，但使用了 IJW。  
  
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
  
### <a name="advantages-of-ijw"></a>IJW 的优点  
  
-   无需编写`DLLImport`特性声明该程序使用的非托管 Api。 只包括标头文件和使用导入库的链接。  
  
-   IJW 机制速度稍微快一些 （例如，IJW 存根 （stub） 不需要来检查是否需要 pin 或复制数据项，因为由开发人员显式完成）。  
  
-   它清楚地证明了性能问题。 在这种情况下，将从 Unicode 字符串转换为 ANSI 字符串，并你事实具有助理内存分配和释放。 在这种情况下，开发人员编写使用 IJW 的代码将发现调用`_putws`和使用`PtrToStringChars`会更好的性能。  
  
-   如果一次并传入调用许多非托管的 Api 使用的相同数据封送处理它的封送的副本是比每次都重新进行封送处理更高效。  
  
### <a name="disadvantages-of-ijw"></a>IJW 的缺点  
  
-   封送处理必须显式指定在代码中而不是通过属性 （属性通常具有适当的默认值）。  
  
-   封送处理代码是内联，其中很多侵入性的应用程序逻辑的流中。  
  
-   由于显式封送处理 Api 返回`IntPtr`32 位到 64 位可移植性的类型，你必须使用额外`ToPointer`调用。  
  
 特定方法公开由 c + + 是更为高效、 显式方法，但也会占用附加的复杂性。  
  
 如果应用程序使用主要非托管的数据类型，或如果它调用的非托管的 Api 更比.NET Framework Api，我们建议你使用 IJW 功能。 若要在主要托管的应用程序中调用偶尔的非托管的 API，选择是更难以捉摸的。  
  
## <a name="pinvoke-with-windows-apis"></a>与 Windows Api 的 PInvoke  
 PInvoke 适用于 Windows 中调用函数。  
  
 在此示例中，Visual c + + 程序与是 Win32 API 的一部分的 MessageBox 函数互操作。  
  
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
  
 输出是一个消息框，具有标题 PInvoke 测试，其文本 Hello World ！。  
  
 PInvoke 也使用的封送处理信息查找 DLL 中的函数。 User32.dll 中没有实际上没有 MessageBox 函数，但 CharSet = CharSet::Ansi 启用 PInvoke 用于 MessageBoxA，ANSI 版本中，而不是 MessageBoxW，这是 Unicode 版本。 通常情况下，我们建议你使用 Unicode 版本的非托管 Api，因为这样，便不.NET Framework 字符串对象的 ANSI 到开销从本机 Unicode 格式转换。  
  
## <a name="when-not-to-use-pinvoke"></a>何时不使用 PInvoke  
 使用 PInvoke 不适合于 Dll 中的所有 C 样式函数。 例如，假设那里 mylib.dll 中的函数 MakeSpecial 声明，如下所示：  
  
 `char * MakeSpecial(char * pszString);`  
  
 如果我们使用在 Visual c + + 应用程序中的 PInvoke，我们可以编写类似于以下内容：  
  
 `[DllImport("mylib")]`  
  
 `extern "C" String * MakeSpecial([MarshalAs(UnmanagedType::LPStr)] String ^);`  
  
 此处的难点是我们无法删除 MakeSpecial 返回的非托管字符串的内存。 通过 PInvoke 调用其他函数返回到不必释放由用户的内部缓冲区的指针。 在这种情况下，使用 IJW 功能是明智的选择。  
  
## <a name="limitations-of-pinvoke"></a>PInvoke 的限制  
 无法从以前用作参数的本机函数来返回完全相同的指针。 如果本机函数按 PInvoke 封送的指针返回到它，内存损坏和异常可能随之发生。  
  
```  
__declspec(dllexport)  
char* fstringA(char* param) {  
   return param;  
}  
```  
  
 下面的示例说明了此问题，并输出即使程序看起来给出正确的输出，来自已被释放的内存。  
  
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
  
## <a name="marshaling-arguments"></a>封送处理参数  
 与`PInvoke`，没有封送处理需要之间托管类型和 c + + 本机基元类型具有相同形式。 例如，没有封送处理是 Int32 和 int、 之间双和双精度型或之间必需的。  
  
 但是，你必须封送不具有相同的形式的类型。 这包括 char、 字符串和结构的类型。 下表显示由该封送处理用于各种类型的映射：  
  
|wtypes.h|Visual C++|/Clr 下的 visual c + +|公共语言运行时|  
|--------------|------------------|-----------------------------|-----------------------------|  
|句柄|void *|void *|IntPtr UIntPtr|  
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
|LPCSTR|char *|字符串 ^ [in]，StringBuilder ^ [中，out]|字符串 ^ [in]，StringBuilder ^ [中，out]|  
|LPCSTR|const char *|字符串 ^|String|  
|LPWSTR|wchar_t *|字符串 ^ [in]，StringBuilder ^ [中，out]|字符串 ^ [in]，StringBuilder ^ [中，out]|  
|LPCWSTR|const wchar_t *|字符串 ^|String|  
|FLOAT|float|float|Single|  
|DOUBLE|double|double|Double|  
  
 封送处理程序会自动锁定该如果其地址传递给非托管函数运行时堆上分配内存。 固定可防止垃圾回收器将分配的内存块移动压缩时。  
  
 在本主题前面所示示例中，DllImport 的 CharSet 参数指定如何将托管的字符串应封送;在这种情况下，它们应封送到本机方为 ANSI 字符串。  
  
 可以通过使用 MarshalAs 属性指定本机函数的各个自变量封送处理的信息。 封送处理字符串的几种选择 * 自变量： BStr、 ANSIBStr、 TBStr、 LPStr、 LPWStr，和 LPTStr。 默认值为 LPStr。  
  
 在此示例中，字符串的封送处理为双字节 Unicode 字符字符串，LPWStr。 输出为 Hello World 的第一个字母 ！ 因为第二个字节的封送的字符串为 null，并且将可以将此解释为字符串的结尾标记中。  
  
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
  
 该 MarshalAs 属性为 System::Runtime::InteropServices 命名空间中。 该属性可以用于其他数据类型，例如数组。  
  
 如本主题前面所述，封送处理库提供新的优化方法的本机和托管环境之间封送数据。 有关详细信息，请参阅[概述的封送处理在 c + +](../dotnet/overview-of-marshaling-in-cpp.md)。  
  
## <a name="performance-considerations"></a>性能注意事项  
 PInvoke 具有介于 10 和 30 之间的开销 x86 每次调用的说明。 除了此固定成本，封送处理创建其他系统开销。 在托管和非托管代码中有相同的表示形式的本机结构中类型之间没有任何封送处理开销。 例如，是免费 int 和 Int32 之间进行转换。  
  
 为了提高性能，具有 PInvoke 调用更少，以尽可能，而不是封送每次调用更少数据的更多调用封送尽可能多的数据。  
  
## <a name="see-also"></a>请参阅  
 [本机和 .NET 的互操作性](../dotnet/native-and-dotnet-interoperability.md)