---
title: C++ 中的封送处理概述
ms.date: 06/28/2018
ms.topic: reference
f1_keywords:
- marshaling
- marshalling
helpviewer_keywords:
- Visual C++, marshaling
- C++ Support Library, marshaling
- marshaling, about marshaling
ms.assetid: 997dd4bc-5f98-408f-b890-f35de9ce3bb8
ms.openlocfilehash: 9b4bdcb8a6e691d8f9f0f0f0c2e7d852b4885ea6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486276"
---
# <a name="overview-of-marshaling-in-c"></a>C++ 中的封送处理概述

在混合模式下，有时必须封送本机和托管类型之间的数据。 Visual Studio 2008 中引入*封送处理库*以帮助将封送，并将数据转换的简单方式。  封送处理库包含一组函数和一个`marshal_context`执行常见类型的封送处理的类。 在这些标头中定义库**包括 msclr**目录为您的 Visual Studio 版本：

|Header|描述|
|---------------|-----------------|
|marshal.h|`marshal_context` 类和无上下文的封送处理函数|
|marshal_atl.h| 用于封送处理 ATL 类型的函数|
|marshal_cppstd.h|用于封送处理标准 c + + 类型的函数|
|marshal_windows.h|用于封送处理 Windows 类型的函数|

默认路径**msclr**文件夹是类似下面有具体取决于哪个版本和内部版本号：

```cmd
C:\\Program Files (x86)\\Microsoft Visual Studio\\Preview\\Enterprise\\VC\\Tools\\MSVC\\14.15.26528\\include\\msclr
```

可以使用封送处理库，带或不带[marshal_context 类](../dotnet/marshal-context-class.md)。 某些转换需要上下文。 可以使用实现其他转换[marshal_as](../dotnet/marshal-as.md)函数。 下表列出了当前支持的转换、 是否需要上下文和封送文件必须包括：

|从类型|若要键入|封送方法|包含文件|
|---------------|-------------|--------------------|------------------|
|System:: string ^|const char \*|marshal_context|marshal.h|
|const char \*|System:: string ^|marshal_as|marshal.h|
|Char \*|System:: string ^|marshal_as|marshal.h|
|System:: string ^|const wchar_t\*|marshal_context|marshal.h|
|const wchar_t \*|System:: string ^|marshal_as|marshal.h|
|wchar_t \*|System:: string ^|marshal_as|marshal.h|
|System::IntPtr|句柄|marshal_as|marshal_windows.h|
|句柄|System::IntPtr|marshal_as|marshal_windows.h|
|System:: string ^|BSTR|marshal_context|marshal_windows.h|
|BSTR|System:: string ^|marshal_as|marshal.h|
|System:: string ^|bstr_t|marshal_as|marshal_windows.h|
|bstr_t|System:: string ^|marshal_as|marshal_windows.h|
|System:: string ^|std:: string|marshal_as|marshal_cppstd.h|
|std:: string|System:: string ^|marshal_as|marshal_cppstd.h|
|System:: string ^|std:: wstring|marshal_as|marshal_cppstd.h|
|std:: wstring|System:: string ^|marshal_as|marshal_cppstd.h|
|System:: string ^|CStringT\<char >|marshal_as|marshal_atl.h|
|CStringT\<char >|System:: string ^|marshal_as|marshal_atl.h|
|System:: string ^|CStringT < wchar_t >|marshal_as|marshal_atl.h|
|CStringT < wchar_t >|System:: string ^|marshal_as|marshal_atl.h|
|System:: string ^|CComBSTR|marshal_as|marshal_atl.h|
|CComBSTR|System:: string ^|marshal_as|marshal_atl.h|

仅当你将封送从托管到本机数据类型并将转换为本机类型不具有的析构函数的自动清理时，封送处理需要上下文。 封送处理上下文销毁其析构函数中的已分配的本机数据类型。 因此，仅删除上下文之前，需要上下文的转换将始终有效。 若要保存任何封送的值，必须将值复制到自己的变量中。

> [!NOTE]
>  如果您嵌入了`NULL`在字符串中的 s，不保证结果的封送处理字符串。 嵌入`NULL`s 会导致字符串被截断，或者它们可能会保留。

此示例演示如何在 include 标头声明中包含的 msclr 目录：

`#include "msclr\marshal_cppstd.h"`

封送处理库是可扩展的以便可以添加你自己的封送处理类型。 有关扩展封送处理库的详细信息，请参阅[如何： 扩展封送处理库](../dotnet/how-to-extend-the-marshaling-library.md)。

在早期版本中，您无法封送数据通过使用[平台调用](/dotnet/framework/interop/consuming-unmanaged-dll-functions)。 有关详细信息`PInvoke`，请参阅[从托管代码调用本机函数](../dotnet/calling-native-functions-from-managed-code.md)。

## <a name="see-also"></a>请参阅

[C++ 支持库](../dotnet/cpp-support-library.md)<br/>
[如何：扩展封送处理库](../dotnet/how-to-extend-the-marshaling-library.md)
