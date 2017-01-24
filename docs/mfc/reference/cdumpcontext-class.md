---
title: "CDumpContext Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDumpContext"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AfxDump object"
  - "CDumpContext class"
  - "诊断, diagnostic classes"
  - "diagnostic classes"
  - "诊断, diagnostic classes"
ms.assetid: 98c52b2d-14b5-48ed-b423-479a4d1c60fa
caps.latest.revision: 20
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDumpContext Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

以可读的文本形式，支持面向流的诊断输出。  
  
## 语法  
  
```  
class CDumpContext  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CDumpContext::CDumpContext](../Topic/CDumpContext::CDumpContext.md)|构造 `CDumpContext` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDumpContext::DumpAsHex](../Topic/CDumpContext::DumpAsHex.md)|在十六进制转储所指示的项目。|  
|[CDumpContext::Flush](../Topic/CDumpContext::Flush.md)|对于在转储上下文缓冲区的所有数据。|  
|[CDumpContext::GetDepth](../Topic/CDumpContext::GetDepth.md)|获取整数与转储对应的深度。|  
|[CDumpContext::HexDump](../Topic/CDumpContext::HexDump.md)|在十六进制转储数组中包含的字节。|  
|[CDumpContext::SetDepth](../Topic/CDumpContext::SetDepth.md)|设置转储的深度。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CDumpContext::operator \<\<](../Topic/CDumpContext::operator%20%3C%3C.md)|插入变量和对象到转储上下文中。|  
  
## 备注  
 `CDumpContext` 没有基类。  
  
 可以用于大多数您转储使用 [afxDump](../Topic/afxDump%20\(CDumpContext%20in%20MFC\).md)，一predeclared `CDumpContext` 对象。  `afxDump` 对象只在Microsoft基础选件类库的调试版本。  
  
 线程其输出内存 [诊断服务](../../mfc/reference/diagnostic-services.md) 使用 `afxDump`。  
  
 在Windows环境下，从预定义的 `afxDump` 对象的输出，概念上类似于 `cerr` 流，路由到调试器通过Windows功能 **OutputDebugString**。  
  
 `CDumpContext` 选件类具有转储对象的数据 `CObject` 指针的一个重载中插入 \(**\<\<**\) 运算符。  如果需要派生的对象的自定义转储格式，请重写 [CObject::Dump](../Topic/CObject::Dump.md)。  大多数Microsoft基础类实现一个被重写的 `Dump` 成员函数。  
  
 从 `CObject`未派生，例如 `CString`，`CTime`和 `CTimeSpan`的选件类，它们的重载 `CDumpContext` 插入运算符，如常用的结构\(例如 **CFileStatus**、 `CPoint`和 `CRect`。  
  
 如果您的选件类的实现使用 [IMPLEMENT\_DYNAMIC](../Topic/IMPLEMENT_DYNAMIC.md) 或 [IMPLEMENT\_SERIAL](../Topic/IMPLEMENT_SERIAL.md) 宏，则 `CObject::Dump` 将打印您的 `CObject`的名称派生类。  否则，它将打印 `CObject`。  
  
 `CDumpContext` 选件类对库的两个调试版本和发布版本可用，但是，`Dump` 成员函数在调试版本仅定义。  使用 **\#ifdef \_DEBUG** \/ `#endif` 语句括起来诊断代码，包括您的自定义 `Dump` 成员函数。  
  
 在创建您的 `CDumpContext` 对象之前，必须创建用作转储目标的 `CFile` 对象。  
  
 有关 `CDumpContext`的更多信息，请参见 [调试MFC应用程序](../Topic/MFC%20Debugging%20Techniques.md)。  
  
 **\#define \_DEBUG**  
  
## 继承层次结构  
 `CDumpContext`  
  
## 要求  
 **Header:** afx.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CFile Class](../../mfc/reference/cfile-class.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)