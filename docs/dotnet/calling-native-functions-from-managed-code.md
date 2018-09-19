---
title: 调用本机函数从托管代码 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- native functions called from managed code [C++]
- managed code [C++], interoperability
- platform invoke [C++], interoperability
- interoperabiliy [C++], calling native functions from managed code
- calling native functions from managed code
- interop [C++], calling native functions from managed code
ms.assetid: 982cef18-20d9-42b4-8242-a77fa65f2e36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 002093a6a9044c65e5780035ad6c19db35d6b648
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116738"
---
# <a name="calling-native-functions-from-managed-code"></a>从托管代码调用本机函数
公共语言运行时提供平台调用服务，简称 PInvoke，使托管代码能够调用本机动态链接库 (Dll) 中的 C 样式函数。 与 COM 互操作性与运行时和"It Just Works，"或 ijw 映像、 机制使用相同的数据封送处理。  
  
 有关详细信息，请参见:  
  
-   [在 C++ 中使用显式 PInvoke（DllImport 特性）](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)  
  
-   [使用 C++ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)  
  
 在本部分中的示例仅演示了如何`PInvoke`可用。 `PInvoke` 可以简化自定义的数据封送处理，这因为你提供属性而不是编写过程性的封送处理代码中声明的方式封送处理信息。  
  
> [!NOTE]
>  封送处理库提供了一种方法来以优化方式在本机和托管环境之间封送数据。 请参阅[Overview of Marshaling c + + 中](../dotnet/overview-of-marshaling-in-cpp.md)有关封送处理库的详细信息。 封送处理库是可用的数据，而不是针对函数。  
  
## <a name="pinvoke-and-the-dllimport-attribute"></a>PInvoke 和 DllImport 特性  
 下面的示例演示如何使用`PInvoke`Visual c + + 程序中。 本机函数的 puts 定义在 msvcrt.dll 中。 DllImport 特性用于 puts 的声明。  
  
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
  
-   无需编写`DLLImport`特性声明该程序使用的非托管 api。 只需包括标头文件和使用导入库链接。  
  
-   IJW 机制速度稍微快一些 （例如，IJW 存根 （stub） 不必检查是否需要 pin 或复制数据项，因为由开发人员显式完成的）。  
  
-   它清楚地说明了性能问题。 在这种情况下，这一事实从 Unicode 字符串转换为 ANSI 字符串，并且具有助理内存分配和解除分配。 在这种情况下，编写使用 IJW 的代码的开发人员将发现调用`_putws`并使用`PtrToStringChars`会更好的性能。  
  
-   如果调用许多非托管的 Api 使用相同的数据，封送处理它，一次并传递经过封送处理的复制速度比重新封送处理每次都有效得多。  
  
### <a name="disadvantages-of-ijw"></a>IJW 的缺点  
  
-   封送处理必须显式指定代码而不是由属性 （它们通常具有适当的默认值）。  
  
-   封送处理代码是内联，其中是应用程序逻辑的流中更具侵入性的。  
  
-   由于显式封送处理 Api 返回`IntPtr`32 位到 64 位可移植性类型，因此必须使用额外`ToPointer`调用。  
  
 公开 c + + 的特定方法是更为高效、 显式方法，但代价是附加的复杂性。  
  
 如果应用程序使用主要的非托管的数据类型，或如果它调用更多的非托管的 Api 比.NET Framework Api，我们建议你使用 IJW 功能。 若要在托管应用程序中调用偶尔的非托管的 API，是更细微而定。  
  
## <a name="pinvoke-with-windows-apis"></a>PInvoke 与 Windows Api  
 来说，PInvoke 很方便地在 Windows 中调用函数。  
  
 在此示例中，Visual c + + 程序进行互操作是 Win32 API 的一部分的 MessageBox 函数。  
  
```cpp  
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
  
 输出是一个消息框标题为 PInvoke Test 并包含文本 Hello World ！。  
  
 PInvoke 还使用封送处理信息来查找 DLL 中的函数。 在 user32.dll 没有实际上没有 MessageBox 函数，但 CharSet = charset:: Ansi 使 PInvoke 能够使用 MessageBoxA，ANSI 版本，而非 MessageBoxW，它是 Unicode 版本。 一般情况下，我们建议你使用非托管 Api 的 Unicode 版本，因为它消除了开销从转换的本机 Unicode 格式的.NET Framework 字符串对象为 ANSI。  
  
## <a name="when-not-to-use-pinvoke"></a>何时不使用 PInvoke  
 使用 PInvoke 不适合于 Dll 中的所有 C 样式函数。 例如，假设 mylib.dll 中的一个函数 makespecial，其声明，如下所示：  
  
 `char * MakeSpecial(char * pszString);`  
  
 如果我们在 Visual c + + 应用程序中使用 PInvoke，我们可以编写类似于以下内容：  
  
```cpp
[DllImport("mylib")]
extern "C" String * MakeSpecial([MarshalAs(UnmanagedType::LPStr)] String ^);
```
  
 这里的难点是我们不能删除由 MakeSpecial 返回的非托管字符串的内存。 通过 PInvoke 调用的其他函数返回到没有用户已取消分配的内部缓冲区的指针。 在这种情况下，使用 IJW 功能是显而易见的选择。  
  
## <a name="limitations-of-pinvoke"></a>PInvoke 的局限性  
 无法从以前用作参数的本机函数来返回完全相同的指针。 如果本机函数由 PInvoke 封送的指针返回到它，可能会发生内存损坏和异常。  
  
```cpp  
__declspec(dllexport)  
char* fstringA(char* param) {  
   return param;  
}  
```  
  
 下面的示例说明了此问题，并且即使程序看起来给出了正确的输出，输出来自已经释放的内存。  
  
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
 使用`PInvoke`，没有封送处理需要之间管理和 c + + 本机基元类型具有相同形式。 例如，没有封送处理是 Int32 和 int、 Double 和 double 之间或之间必需的。  
  
 但是，您必须封送不具有相同的形式的类型。 这包括 char、 string 和 struct 类型。 下表显示封送处理程序使用的各种类型的映射：  
  
|wtypes.h|Visual C++|Visual c + + 和 /clr|公共语言运行时|  
|--------------|------------------|-----------------------------|-----------------------------|  
|句柄|Void \*|Void \*|IntPtr、 UIntPtr|  
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
|LPCSTR|Char \*|字符串 ^ [in]、 StringBuilder ^ [中，out]|字符串 ^ [in]、 StringBuilder ^ [中，out]|  
|LPCSTR|const char \*|字符串 ^|String|  
|LPWSTR|wchar_t \*|字符串 ^ [in]、 StringBuilder ^ [中，out]|字符串 ^ [in]、 StringBuilder ^ [中，out]|  
|LPCWSTR|const wchar_t \*|字符串 ^|String|  
|FLOAT|float|float|Single|  
|DOUBLE|double|double|Double|  
  
 封送处理程序会自动锁定其地址传递给非托管函数如果在运行时堆上分配内存。 固定可防止垃圾回收器在压缩期间移动分配的内存块。  
  
 在本主题中前面所示示例中，DllImport 的 CharSet 参数指定如何将托管的字符串封送处理;在这种情况下，它们应封送到本机端为 ANSI 字符串。  
  
 可以使用 MarshalAs 特性来指定各个自变量封送处理信息的本机函数。 有几个选项进行封送处理字符串\*参数： BStr、 ANSIBStr、 TBStr、 LPStr、 LPWStr 和 LPTStr。 默认选项为 LPStr。  
  
 在此示例中，该字符串被封送为双字节 Unicode 字符字符串 LPWStr。 输出是第一个字母的 Hello World ！ 因为封送的字符串的第二个字节为 null，并且将放则将此解释为字符串的结尾标记。  
  
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
  
 MarshalAs 特性位于 System::Runtime::InteropServices 命名空间中。 该属性可以用于其他数据类型，例如数组。  
  
 如本主题前面所述，封送处理库提供了一个新的本机和托管环境之间封送数据优化方法。 有关详细信息，请参阅[Overview of Marshaling c + + 中](../dotnet/overview-of-marshaling-in-cpp.md)。  
  
## <a name="performance-considerations"></a>性能注意事项  
 PInvoke 有 10 到 30 之间的开销为 x86 说明每个调用。 除了这些固定开销，封送处理造成额外的负担。 在托管和非托管代码中具有相同的表示形式的 blittable 类型之间没有封送处理成本。 例如，没有任何费用 int 和 Int32 之间进行转换。  
  
 为了提高性能，具有较少的 PInvoke 调用封送尽可能，而不是多个调用封送更少的数据每次调用的数量的数据。  
  
## <a name="see-also"></a>请参阅  
 [本机和 .NET 的互操作性](../dotnet/native-and-dotnet-interoperability.md)