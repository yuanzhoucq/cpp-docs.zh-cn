---
title: "在 c + + 中的封送处理概述 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- marshaling
- marshalling
dev_langs: C++
helpviewer_keywords:
- Visual C++, marshaling
- C++ Support Library, marshaling
- marshaling, about marshaling
ms.assetid: 997dd4bc-5f98-408f-b890-f35de9ce3bb8
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 384c8bac652e16a4f66a82ee7e4dbb5cc92fd32b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="overview-of-marshaling-in-c"></a>C++ 中的封送处理概述
在混合模式下，你有时必须封你本机和托管类型之间的数据。 [!INCLUDE[vs_orcas_long](../atl/reference/includes/vs_orcas_long_md.md)]引入的封送处理库来帮助你封送，并将数据转换的简单方式。  
  
 你可以使用或不使用封送处理库[marshal_context 类](../dotnet/marshal-context-class.md)。 某些转换需要上下文。 可以使用实现其他转换[marshal_as](../dotnet/marshal-as.md)函数。 下表列出当前支持的转换、 是否需要非上下文，和封送文件必须包括：  
  
|从类型|为类型|封送方法|包含文件|  
|---------------|-------------|--------------------|------------------|  
|System:: string ^|const char *|marshal_context|marshal.h|  
|const char *|System:: string ^|marshal_as|marshal.h|  
|char *|System:: string ^|marshal_as|marshal.h|  
|System:: string ^|const wchar_t*|marshal_context|marshal.h|  
|const wchar_t *|System:: string ^|marshal_as|marshal.h|  
|wchar_t *|System:: string ^|marshal_as|marshal.h|  
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
  
 仅当你封送从托管到本机数据类型，并将转换为本机类型不具有的析构函数的自动清理时，封送处理需要上下文。 封送处理上下文销毁其析构函数中的已分配的本机数据类型。 因此，仅在删除上下文之前，需要上下文的转换将能有效。 若要保存任何封送的值，必须将值复制到你自己的变量中。  
  
> [!NOTE]
>  如果有嵌入`NULL`在字符串中的 s，但不保证的封送处理字符串结果。 嵌入`NULL`s 会导致字符串被截断，或者它们可能会保留。  
  
 封送处理库标头位于 msclr 子目录中的 include 目录中。 此示例演示如何在包含标头声明中包括 msclr 目录：  
  
 `#include "msclr\marshal_cppstd.h"`  
  
 封送处理库是可扩展的以便你可以添加你自己的封送处理类型。 有关扩展封送处理库的详细信息，请参阅[如何： 扩展封送处理库](../dotnet/how-to-extend-the-marshaling-library.md)。  
  
 在早期版本中，你无法封送数据使用[平台调用](/dotnet/framework/interop/consuming-unmanaged-dll-functions)。 有关详细信息`PInvoke`，请参阅[从托管代码调用本机函数](../dotnet/calling-native-functions-from-managed-code.md)。  
  
## <a name="see-also"></a>另请参阅  
 [C + + 支持库](../dotnet/cpp-support-library.md)   
 [如何：扩展封送处理库](../dotnet/how-to-extend-the-marshaling-library.md)