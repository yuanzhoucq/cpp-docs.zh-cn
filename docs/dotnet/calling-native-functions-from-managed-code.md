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
ms.openlocfilehash: 50f40cc147daaa26a7fa4e607f0d4dd42cf22d61
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545365"
---
# <a name="calling-native-functions-from-managed-code"></a>从托管代码调用本机函数

公共语言运行时提供平台调用服务（即 PInvoke），使托管代码能够调用本机动态链接库（Dll）中的 C 样式函数。 使用相同的数据封送处理与运行时的 COM 互操作性以及 "它的工作" 或 IJW 的机制相同。

有关详细信息，请参阅：

- [在 C++ 中使用显式 PInvoke（DllImport 特性）](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)

- [使用 C++ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)

本节中的示例演示如何使用 `PInvoke`。 `PInvoke` 可以简化自定义的数据封送处理，因为在属性中以声明方式提供封送处理信息，而不是编写过程封送

> [!NOTE]
>  封送处理库提供了一种方法，可通过优化的方式在本机和托管环境之间封送数据。 有关封送处理库的详细信息，请参阅[中C++的封送的概述](../dotnet/overview-of-marshaling-in-cpp.md)。 封送处理库仅适用于数据，不适用于函数。

## <a name="pinvoke-and-the-dllimport-attribute"></a>PInvoke 和 DllImport 特性

下面的示例演示如何在可视化C++程序中使用 `PInvoke`。 本机函数 put 是在 msvcrt.lib 中定义的。 DllImport 特性用于 put 的声明。

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

下面的示例与前面的示例等效，但使用 IJW。

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

### <a name="advantages-of-ijw"></a>IJW 的优点

- 不需要为程序使用的非托管 Api 写入 `DLLImport` 属性声明。 只需包含头文件并链接到导入库。

- IJW 机制稍微快一些（例如，IJW 存根无需检查是否需要固定或复制数据项，因为这是由开发人员显式完成的）。

- 它清楚地说明了性能问题。 在这种情况下，你要将 Unicode 字符串转换为 ANSI 字符串，并且具有助理内存分配和解除分配。 在这种情况下，使用 IJW 编写代码的开发人员将认识到调用 `_putws` 和使用 `PtrToStringChars` 对于性能更好。

- 如果使用相同的数据调用多个非托管 Api，则封送处理一次后，传递已封送的副本比每次重新封送处理要高效得多。

### <a name="disadvantages-of-ijw"></a>IJW 的缺点

- 必须在代码中（而不是按属性，通常具有适当的默认值）显式指定封送处理。

- 封送处理代码是内联的，在这种情况下，它会更容易受到应用程序逻辑的流动。

- 因为显式封送处理 Api 将32位的 `IntPtr` 类型返回到64位可移植性，所以必须使用额外 `ToPointer` 调用。

公开的特定方法C++是更有效的显式方法，但代价是增加一些额外的复杂性。

如果应用程序主要使用非托管数据类型，或者它调用的 Api 比 .NET Framework Api 多，则建议使用 IJW 功能。 若要在大多数托管的应用程序中调用偶尔非托管的 API，选择更为微妙。

## <a name="pinvoke-with-windows-apis"></a>带有 Windows Api 的 PInvoke

PInvoke 非常适合用于在 Windows 中调用函数。

在此示例中，可视化C++程序与 Win32 API 的一部分的 MessageBox 函数进行互操作。

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

输出是一个消息框，其标题为 PInvoke，并包含文本 Hello World！。

PInvoke 还使用封送处理信息在 DLL 中查找函数。 在 user32 中，事实上没有 MessageBox 函数，但字符集 = 字符集：： Ansi 允许 PInvoke 使用 MessageBoxA，而不是 MessageBoxW，这是 Unicode 版本。 通常，我们建议你使用非托管 Api 的 Unicode 版本，因为这样可以消除从 .NET Framework 字符串对象的本机 Unicode 格式到 ANSI 的转换开销。

## <a name="when-not-to-use-pinvoke"></a>何时不使用 PInvoke

使用 PInvoke 并非适用于 Dll 中的所有 C 样式函数。 例如，假设 mylib.dll 中有一个函数 MakeSpecial，其声明如下：

`char * MakeSpecial(char * pszString);`

如果在可视化C++应用程序中使用 PInvoke，我们可能会编写类似于下面的内容：

```cpp
[DllImport("mylib")]
extern "C" String * MakeSpecial([MarshalAs(UnmanagedType::LPStr)] String ^);
```

此处的难点在于，我们无法删除 MakeSpecial 返回的非托管字符串的内存。 通过 PInvoke 调用的其他函数返回一个指针，该指针指向不需要由用户释放的内部缓冲区。 在这种情况下，使用 IJW 功能是显而易见的选择。

## <a name="limitations-of-pinvoke"></a>PInvoke 的限制

不能从用作为参数的本机函数返回相同的指针。 如果本机函数返回已通过 PInvoke 封送到它的指针，则内存损坏和异常可能会不幸。

```cpp
__declspec(dllexport)
char* fstringA(char* param) {
   return param;
}
```

下面的示例展示了此问题，即使该程序看起来好像提供了正确的输出，输出也来自已释放的内存。

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

## <a name="marshaling-arguments"></a>封送处理参数

在 `PInvoke`中，具有相同格式的托管和C++本机基元类型之间不需要封送处理。 例如，在 Int32 和 int 之间，或者在 Double 和 double 之间不需要封送处理。

但是，您必须对不具有相同形式的类型进行封送处理。 这包括 char、string 和 struct 类型。 下表显示了封送拆收器用于各种类型的映射：

|wtypes.h|Visual C++|Visual C++ with/clr|公共语言运行时|
|--------------|------------------|-----------------------------|-----------------------------|
|句柄|void \*|void \*|IntPtr、UIntPtr|
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
|LPCSTR|char \*|String ^ [in]，StringBuilder ^ [in，out]|String ^ [in]，StringBuilder ^ [in，out]|
|LPCSTR|const char \*|字符串 ^|String|
|LPWSTR|wchar_t \*|String ^ [in]，StringBuilder ^ [in，out]|String ^ [in]，StringBuilder ^ [in，out]|
|LPCWSTR|const wchar_t \*|字符串 ^|String|
|FLOAT|FLOAT|FLOAT|Single|
|DOUBLE|double|double|Double|

如果封送处理程序传递到非托管函数，则封送拆收器会自动固定在运行时堆上分配的内存。 固定可防止垃圾回收器在压缩期间移动分配的内存块。

在本主题前面所示的示例中，DllImport 的字符集参数指定应如何封送托管字符串;在这种情况下，应将它们封送到本机端的 ANSI 字符串。

您可以通过使用 MarshalAs 特性来指定本机函数的单个参数的封送处理信息。 有几种方式可用于封送字符串 \* 参数： BStr、ANSIBStr、TBStr、LPStr、LPWStr 和 LPTStr。 默认值为 LPStr。

在此示例中，将字符串作为双字节 Unicode 字符串 LPWStr 封送。 输出是 Hello World 的第一个字母！ 因为封送字符串的第二个字节为 null，并将其解释为字符串结尾标记。

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

MarshalAs 特性位于 System：： Runtime：： InteropServices 命名空间中。 属性可与其他数据类型（如数组）一起使用。

如本主题前面所述，封送处理库提供了一种新的优化方法，用于在本机和托管环境之间封送数据。 有关详细信息，请参阅[中C++的封送的概述](../dotnet/overview-of-marshaling-in-cpp.md)。

## <a name="performance-considerations"></a>性能注意事项

对于每个调用，PInvoke 的系统开销介于10到30个 x86 指令之间。 除这一固定开销外，封送还会产生额外的开销。 在托管代码和非托管代码中具有相同表示形式的可直接复制类型之间没有封送处理开销。 例如，int 和 Int32 之间不需要进行转换。

为了获得更好的性能，请使用更少的 PInvoke 调用来封送尽可能多的数据，而不是对每次调用封送更少数据的调用。

## <a name="see-also"></a>另请参阅

[本机和 .NET 的互操作性](../dotnet/native-and-dotnet-interoperability.md)
