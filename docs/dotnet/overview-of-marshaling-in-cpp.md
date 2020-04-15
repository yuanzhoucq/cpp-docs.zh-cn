---
title: C++ 中的封送处理概述
ms.date: 07/12/2019
ms.topic: reference
f1_keywords:
- marshaling
- marshalling
helpviewer_keywords:
- Visual C++, marshaling
- C++ Support Library, marshaling
- marshaling, about marshaling
ms.assetid: 997dd4bc-5f98-408f-b890-f35de9ce3bb8
ms.openlocfilehash: 0c7bf18fa823c6301a79c3f989efa73c9e8f628a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372001"
---
# <a name="overview-of-marshaling-in-ccli"></a>C++/CLI 中封送的概述

在混合模式下，有时必须在本机类型和托管类型之间封送数据。 *封送库*可帮助您以简单方式封送和转换数据。  封送库由一组函数和一个`marshal_context`类组成，这些函数和类执行公共类型的封送。 库在 Visual Studio 版的 **"包括/msclr"** 目录中的这些标头中定义：

|标头|说明|
|---------------|-----------------|
|元帅.h|`marshal_context`类和无上下文封送函数|
|marshal_atl.h| 用于封送 ATL 类型的函数|
|marshal_cppstd.h|用于封送标准C++类型的函数|
|marshal_windows.h|用于封送 Windows 类型的函数|

**msclr**文件夹的默认路径如下所示，具体取决于您拥有的版本和内部版本号：

```cmd
C:\\Program Files (x86)\\Microsoft Visual Studio\\Preview\\Enterprise\\VC\\Tools\\MSVC\\14.15.26528\\include\\msclr
```

您可以使用带或不带[marshal_context 类](../dotnet/marshal-context-class.md)的封送库。 某些转换需要上下文。 可以使用[marshal_as](../dotnet/marshal-as.md)函数实现其他转换。 下表列出了支持的当前转换、是否需要上下文以及必须包括哪些封送文件：

|从类型|键入|封送方法|包括文件|
|---------------|-------------|--------------------|------------------|
|系统：字符串*|const char \*|marshal_context|元帅.h|
|const char \*|系统：字符串*|marshal_as|元帅.h|
|字符\*|系统：字符串*|marshal_as|元帅.h|
|系统：字符串*|康斯特wchar_t\*|marshal_context|元帅.h|
|const wchar_t \*|系统：字符串*|marshal_as|元帅.h|
|wchar_t \*|系统：字符串*|marshal_as|元帅.h|
|系统：：IntPtr|句柄|marshal_as|marshal_windows.h|
|句柄|系统：：IntPtr|marshal_as|marshal_windows.h|
|系统：字符串*|BSTR|marshal_context|marshal_windows.h|
|BSTR|系统：字符串*|marshal_as|元帅.h|
|系统：字符串*|bstr_t|marshal_as|marshal_windows.h|
|bstr_t|系统：字符串*|marshal_as|marshal_windows.h|
|系统：字符串*|std：：字符串|marshal_as|marshal_cppstd.h|
|std：：字符串|系统：字符串*|marshal_as|marshal_cppstd.h|
|系统：字符串*|std::wstring|marshal_as|marshal_cppstd.h|
|std::wstring|系统：字符串*|marshal_as|marshal_cppstd.h|
|系统：字符串*|CStringT\<字符>|marshal_as|marshal_atl.h|
|CStringT\<字符>|系统：字符串*|marshal_as|marshal_atl.h|
|系统：字符串*|CStringt<wchar_t>|marshal_as|marshal_atl.h|
|CStringt<wchar_t>|系统：字符串*|marshal_as|marshal_atl.h|
|系统：字符串*|CComBSTR|marshal_as|marshal_atl.h|
|CComBSTR|系统：字符串*|marshal_as|marshal_atl.h|

封送仅在从托管数据类型封送到本机数据类型且要转换为的本机类型没有用于自动清理的析构函数时，才需要上下文。 封送上下文销毁其析构函数中分配的本机数据类型。 因此，需要上下文的转换仅在删除上下文之前才有效。 要保存任何封送值，必须将值复制到自己的变量。

> [!NOTE]
> 如果字符串中嵌入`NULL`了 s，则不能保证对字符串进行封送的结果。 嵌入`NULL`的 s 可能导致字符串被截断，或者可能保留它们。

此示例演示如何在包含标头声明中包括 msclr 目录：

`#include "msclr\marshal_cppstd.h"`

封送库是可扩展的，因此您可以添加自己的封送类型。 有关扩展封送库的详细信息，请参阅[如何：扩展封送库](../dotnet/how-to-extend-the-marshaling-library.md)。

## <a name="see-also"></a>另请参阅

[C++支持库](../dotnet/cpp-support-library.md)<br/>
[如何：扩展封送处理库](../dotnet/how-to-extend-the-marshaling-library.md)
