---
title: "引发软件异常 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "错误 [C++], 作为异常处理"
  - "异常处理, 检测错误"
  - "异常处理, 作为异常的错误"
  - "异常, 将错误标记为异常"
  - "异常, 软件"
  - "格式 [C++], 异常代码"
  - "RaiseException 函数"
  - "运行时错误, 作为异常处理"
  - "软件异常"
  - "结构化异常处理, 作为异常的错误"
ms.assetid: be1376c3-c46a-4f52-ad1d-c2362840746a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 引发软件异常
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

系统不会将某些最常见的程序错误源标记为异常。  例如，如果您尝试分配内存块，但没有足够的内存，则运行时或 API 函数不会引发异常，但会返回一个错误代码。  
  
 但可通过以下方式将任何条件视为异常：在代码中检测该条件，然后调用 [RaiseException](http://msdn.microsoft.com/library/windows/desktop/ms680552) 函数来报告它。  通过按此方式标记错误，您可以将结构化异常处理的优点引入任何类型的运行时错误中。  
  
 对错误使用结构化异常处理：  
  
-   为事件定义您自己的异常代码。  
  
-   检测问题时调用 **RaiseException**。  
  
-   使用异常处理筛选器来测试您定义的异常代码。  
  
 WINERROR.H 文件显示异常代码的格式。  若要确保不定义与现有异常代码发生冲突的代码，请将第三个最高有效位设置为 1。  应设置四个最高有效位，如下表所示。  
  
|位|建议的二进制设置|说明|  
|-------|--------------|--------|  
|31\-30|11|这两个位描述代码的基本状态：11 \= 错误，00 \= 成功，01 \= 信息性，10 \= 警告。|  
|29|1|客户端位。  为用户定义的代码将其设置为 1。|  
|28|0|保留位。（将其设置为 0。）|  
  
 虽然“错误”设置适用于大多数异常，但如果需要，您可将前两个位设置为 11 二进制之外的设置。  请务必记住设置 29 和 28 位，如上表所示。  
  
 因此，生成的错误代码应将最高四个位设置为十六进制 E。  例如，下面的定义将定义不与任何 Windows 异常代码发生冲突的异常代码。（但是，您可能需要检查第三方 DLL 使用了哪些代码。）  
  
```  
#define STATUS_INSUFFICIENT_MEM       0xE0000001  
#define STATUS_FILE_BAD_FORMAT        0xE0000002  
```  
  
 在定义异常代码后，可以使用它来引发异常。  例如，下面的代码引发 STATUS\_INSUFFICIENT\_MEM 异常以响应内存分配问题：  
  
```  
lpstr = _malloc( nBufferSize );  
if (lpstr == NULL)  
    RaiseException( STATUS_INSUFFICIENT_MEM, 0, 0, 0);  
```  
  
 如果只需引发异常，则可以将最后三个参数设置为 0。  最后三个参数对于传递附加信息和设置阻止处理程序继续执行的标记很有用。  有关详细信息，请参阅 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] 中的 [RaiseException](http://msdn.microsoft.com/library/windows/desktop/ms680552) 函数。  
  
 在异常处理筛选器中，您随后可以测试已定义的代码。  例如：  
  
```  
__try {  
    ...  
}  
__except (GetExceptionCode() == STATUS_INSUFFICIENT_MEM ||  
        GetExceptionCode() == STATUS_FILE_BAD_FORMAT )  
```  
  
## 请参阅  
 [编写异常处理程序](../cpp/writing-an-exception-handler.md)   
 [结构化异常处理](../cpp/structured-exception-handling-c-cpp.md)