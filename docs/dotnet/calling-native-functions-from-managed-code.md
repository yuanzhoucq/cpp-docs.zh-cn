---
title: 从托管代码调用本机函数
ms.date: 11/04/2016
helpviewer_keywords:
- native functions called from managed code [C++]
- managed code [C++], interoperability
- platform invoke [C++], interoperability
- interoperabiliy [C++], calling native functions from managed code
- calling native functions from managed code
- interop [C++], calling native functions from managed code
ms.assetid: 982cef18-20d9-42b4-8242-a77fa65f2e36
ms.openlocfilehash: 0cdd5db4fae8d9167fa9ab1aeb6a4e8cbfe76ded
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372513"
---
# <a name="calling-native-functions-from-managed-code"></a>从托管代码调用本机函数

通用语言运行时提供平台调用服务（PInvoke），使托管代码能够在本机动态链接库 （DLL） 中调用 C 样式函数。 相同的数据封送与 COM 与运行时的互操作性以及"它只是工作"或 IJW 机制一样。

有关详细信息，请参阅：

- [在C++中使用显式 PInvoke（DllImport 属性）](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)

- [使用C++互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)

本节中的示例仅说明了如何使用`PInvoke`。 `PInvoke`可以简化自定义的数据封送，因为您在属性中以声明性方式提供封送信息，而不是编写过程封送代码。

> [!NOTE]
> 封送库提供了一种以优化方式在本机环境和托管环境之间封送数据的替代方法。 有关封送库的详细信息，请参阅[C++中的封送概述](../dotnet/overview-of-marshaling-in-cpp.md)。 封送库仅可用于数据，不适用于函数。

## <a name="pinvoke-and-the-dllimport-attribute"></a>PInvoke 和 Dll 导入属性

下面的示例显示了可视化C++程序中的使用`PInvoke`。 本机函数放置在 msvcrt.dll 中定义。 DllImport 属性用于报放。

```cpp
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

以下示例等效于前面的示例，但使用 IJW。

```cpp
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

### <a name="advantages-of-ijw"></a>IJW 的优势

- 无需为程序使用的非托管`DLLImport`API 编写属性声明。 只需包括标头文件和与导入库的链接。

- IJW 机制稍微快一些（例如，IJW 存根不需要检查是否需要固定或复制数据项，因为开发人员会显式执行）。

- 它清楚地说明了性能问题。 在这种情况下，您正在从 Unicode 字符串转换为 ANSI 字符串，并且具有相应的内存分配和处理。 在这种情况下，使用 IJW 编写代码的开发人员会意识到调用`_putws`和使用`PtrToStringChars`将更具有性能。

- 如果使用相同的数据调用许多非托管 API，则将其封送一次并传递封送副本比每次重新封送效率高得多。

### <a name="disadvantages-of-ijw"></a>IJW的缺点

- 封送必须在代码中显式指定，而不是按属性（通常具有适当的默认值）指定。

- 封送代码是内联的，在应用程序逻辑的流中它更具侵入性。

- 由于显式封送 API 返回`IntPtr`32 位到 64 位可移植性的类型，因此必须`ToPointer`使用额外的调用。

C++公开的特定方法是更高效、更明确的方法，但代价是一些额外的复杂性。

如果应用程序主要使用非托管数据类型，或者调用比 .NET 框架 API 更多的非托管 API，我们建议您使用 IJW 功能。 要在大多数托管应用程序中调用偶尔的非托管 API，选择更为微妙。

## <a name="pinvoke-with-windows-apis"></a>使用 Windows API 调用

PInvoke 便于在 Windows 中调用函数。

在此示例中，可视化C++程序与作为 Win32 API 一部分的 MessageBox 函数交互。

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

输出是一个消息框，标题为 PInvoke 测试，并包含文本 Hello World！

PInvoke 还使用封送信息来查找 DLL 中的函数。 在 user32.dll 中，实际上没有 MessageBox 函数，但 CharSet_CharSet：：Ansi 使 PInvoke 能够使用消息BoxA（ANSI 版本）而不是 MessageBoxW（即 Unicode 版本）。 通常，我们建议您使用非托管 API 的 Unicode 版本，因为这消除了从 .NET Framework 字符串对象的本机 Unicode 格式到 ANSI 的转换开销。

## <a name="when-not-to-use-pinvoke"></a>何时不使用 PInvoke

使用 PInvoke 不适用于 DLL 中的所有 C 样式函数。 例如，假设在 mylib.dll 中声明了一个函数"使特殊"，如下所示：

`char * MakeSpecial(char * pszString);`

如果我们在 Visual C++ 应用程序中使用 PInvoke，我们可能会编写类似于以下内容的内容：

```cpp
[DllImport("mylib")]
extern "C" String * MakeSpecial([MarshalAs(UnmanagedType::LPStr)] String ^);
```

这里的困难是，我们不能删除 MakeSpecial 返回的非托管字符串的内存。 通过 PInvoke 调用的其他函数返回指向内部缓冲区的指针，该指针不必由用户处理。 在这种情况下，使用 IJW 功能是明显的选择。

## <a name="limitations-of-pinvoke"></a>PInvoke 的限制

不能从作为参数的本机函数返回完全相同的指针。 如果本机函数返回已由 PInvoke 封送到它的指针，则内存损坏和异常可能会随之而来。

```cpp
__declspec(dllexport)
char* fstringA(char* param) {
   return param;
}
```

下面的示例显示了此问题，即使程序似乎给出了正确的输出，输出来自已释放的内存。

```cpp
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

## <a name="marshaling-arguments"></a>封送参数

使用`PInvoke`时，在托管和C++具有相同窗体的本机基元类型之间不需要封送。 例如，Int32 和 int 之间或 Double 和 Double 之间不需要封送。

但是，必须对具有相同窗体的类型进行封送。 这包括字符、字符串和结构类型。 下表显示了封送器用于各种类型的映射：

|wtypes.h|Visual C++|带 /clr 的视觉C++|公共语言运行时|
|--------------|------------------|-----------------------------|-----------------------------|
|句柄|无效\*|无效\*|IntPtr， UIntPtr|
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
|LPSTR|字符\*|字符串 = 输入，字符串生成器 = [输入、出]|字符串 = 输入，字符串生成器 = [输入、出]|
|LPCSTR|const char \*|字符串 ||字符串|
|LPWSTR|wchar_t \*|字符串 = 输入，字符串生成器 = [输入、出]|字符串 = 输入，字符串生成器 = [输入、出]|
|LPCWSTR|const wchar_t \*|字符串 ||字符串|
|FLOAT|FLOAT|FLOAT|Single|
|DOUBLE|double|double|Double|

如果服务器的地址传递给非托管函数，则封送器会自动将分配给运行时堆的内存固定。 固定可防止垃圾回收器在压缩过程中移动分配的内存块。

在本主题前面所示的示例中，DllImport 的 CharSet 参数指定如何封送托管字符串;否则，应如何对托管字符串进行封送处理。在这种情况下，它们应被封送到本机端的 ANSI 字符串。

可以使用 MarshalAs 属性为本机函数的各个参数指定封送信息。 对字符串\*参数进行封送有多种选择：BStr、ANSIBStr、TBStr、LPStr、LPWStr 和 LPTStr。 默认值为 LPStr。

在此示例中，字符串作为双字节 Unicode 字符串 LPWStr 进行封送。 输出是你好世界的第一个字母！ 因为封送字符串的第二个字节为空，并且将此解释为字符串结尾标记。

```cpp
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

MarshalAs 属性位于系统：运行时：：互通服务命名空间。 该属性可与其他数据类型（如数组）一起使用。

如本主题前面所述，封送库提供了一种新的优化数据在本机环境和托管环境之间封送的方法。 有关详细信息，请参阅[C++ 中的封送概述](../dotnet/overview-of-marshaling-in-cpp.md)。

## <a name="performance-considerations"></a>性能注意事项

PInvoke 的开销介于每个呼叫 10 到 30 x86 指令之间。 除了此固定成本外，封送还会产生额外的开销。 在托管代码和非托管代码中具有相同的表示形式的可声明类型之间没有封送成本。 例如，int 和 Int32 之间没有翻译费用。

为了更好的性能，减少 PInvoke 调用，以尽可能多地封送数据，而不是使用更多调用来为每个调用封送更少的数据。

## <a name="see-also"></a>另请参阅

[本机和 .NET 的互操作性](../dotnet/native-and-dotnet-interoperability.md)
