---
title: "C++ 中的封送处理概述 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "marshaling"
  - "marshalling"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++ 支持库, 封送处理"
  - "封送处理, 关于封送处理"
  - "Visual C++, 封送处理"
ms.assetid: 997dd4bc-5f98-408f-b890-f35de9ce3bb8
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++ 中的封送处理概述
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在混合模式中，您有时会需要封送在本机和托管类型之间的数据。  [!INCLUDE[vs_orcas_long](../atl/reference/includes/vs_orcas_long_md.md)] 引入一种简单的封送处理库方法来封送处理库，帮助您封送和转换数据。  
  
 可以使用封送处理库用或不用 [marshal\_context 类](../dotnet/marshal-context-class.md)。  这些转换需要上下文。  其他变换的实现，可以使用 函数[marshal\_as](../dotnet/marshal-as.md) 。  下表列出了支持的当前转换，它们是否需要上下文，以及送文件必须包括：  
  
|从类型|到\<目标类型\>|封送方法|包含文件\<include\>1|  
|---------|---------------|----------|----------------------|  
|System::String^|const char \*|marshal\_context|marshal.h|  
|const char \*|System::String^|marshal\_as|marshal.h|  
|char \*|System::String^|marshal\_as|marshal.h|  
|System::String^|const wchar\_t\*|marshal\_context|marshal.h|  
|const wchar\_t \*|System::String^|marshal\_as|marshal.h|  
|wchar\_t \*|System::String^|marshal\_as|marshal.h|  
|系统::IntPtr。|HANDLE|marshal\_as|marshal\_windows.h|  
|HANDLE|系统::IntPtr。|marshal\_as|marshal\_windows.h|  
|System::String^|BSTR|marshal\_context|marshal\_windows.h|  
|BSTR|System::String^|marshal\_as|marshal.h|  
|System::String^|bstr\_t|marshal\_as|marshal\_windows.h|  
|bstr\_t|System::String^|marshal\_as|marshal\_windows.h|  
|System::String^|std::string|marshal\_as|marshal\_cppstd.h|  
|std::string|System::String^|marshal\_as|marshal\_cppstd.h|  
|System::String^|std::wstring|marshal\_as|marshal\_cppstd.h|  
|std::wstring|System::String^|marshal\_as|marshal\_cppstd.h|  
|System::String^|CStringTchar\<\>|marshal\_as|marshal\_atl.h|  
|CStringTchar\<\>|System::String^|marshal\_as|marshal\_atl.h|  
|System::String^|CStringT\<wchar\_t\>|marshal\_as|marshal\_atl.h|  
|CStringT\<wchar\_t\>|System::String^|marshal\_as|marshal\_atl.h|  
|System::String^|CComBSTR|marshal\_as|marshal\_atl.h|  
|CComBSTR|System::String^|marshal\_as|marshal\_atl.h|  
  
 只有当您从托管代码封送到本机数据类型时和转换的本机类型没有自动的析构函数清理时才需要上下文。  封送处理上下文会销毁在析构函数中分配的本机数据类型。  因此，转换需要的上下文将是有效的，直至上下文被删除。  若要保存任何封送的值，必须将值复制到您的变量。  
  
> [!NOTE]
>  如果将 `NULL`s 封送到字符串中，则该字符串的结果得不到保证。  嵌入 `NULL`s 可能会导致该字符串被截断或保留。  
  
 封送处理库标头文件位于 msclr 子目录的 include 目录中。  此示例展示了如何引用在标头声明 msclr 内容：  
  
 `#include "msclr\marshal_cppstd.h"`  
  
 封送处理库是可扩展的，因此您可以自己添加封送的类型。  有关扩展封送库的详细信息，请参见 [如何：扩展封送处理库](../dotnet/how-to-extend-the-marshaling-library.md)。  
  
 在早期版本中，封送数据可以使用 [平台调用](../Topic/Consuming%20Unmanaged%20DLL%20Functions.md)。  有关 `PInvoke`的更多信息，请参见[从托管代码调用本机函数](../dotnet/calling-native-functions-from-managed-code.md)。  
  
## 请参阅  
 [C\+\+ 支持库](../dotnet/cpp-support-library.md)   
 [如何：扩展封送处理库](../dotnet/how-to-extend-the-marshaling-library.md)