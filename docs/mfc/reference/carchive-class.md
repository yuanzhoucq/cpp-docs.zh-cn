---
title: "CArchive Class | Microsoft Docs"
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
  - "CArchive"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CArchive class"
  - "data storage [C++], CArchive class"
  - "I/O [MFC], archiving objects"
  - "序列化 [C++], CArchive class"
  - "storage [C++], CArchive class"
ms.assetid: 9e950d23-b874-456e-ae4b-fe00781a7699
caps.latest.revision: 21
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CArchive Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

允许您保存对象的复杂的网络以持久一个永久二进制格式\(通常是磁盘存储\)，这些对象中后发生。  
  
## 语法  
  
```  
class CArchive  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CArchive::CArchive](../Topic/CArchive::CArchive.md)|创建一个 `CArchive` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CArchive::Abort](../Topic/CArchive::Abort.md)|关闭已存档，而不会引发异常。|  
|[CArchive::Close](../Topic/CArchive::Close.md)|对于未记录的数据以及与断开连接 `CFile`。|  
|[CArchive::Flush](../Topic/CArchive::Flush.md)|对于从存档缓冲区的未记录的数据。|  
|[CArchive::GetFile](../Topic/CArchive::GetFile.md)|获取此的 `CFile` 对象指针存档。|  
|[CArchive::GetObjectSchema](../Topic/CArchive::GetObjectSchema.md)|调用从 `Serialize` 函数确定反序列化对象的版本。|  
|[CArchive::IsBufferEmpty](../Topic/CArchive::IsBufferEmpty.md)|确定缓冲区是否为空了Windows套接字期间接收操作。|  
|[CArchive::IsLoading](../Topic/CArchive::IsLoading.md)|确定文件是否加载。|  
|[CArchive::IsStoring](../Topic/CArchive::IsStoring.md)|确定文件是否存储。|  
|[CArchive::MapObject](../Topic/CArchive::MapObject.md)|在映射将不会序列化为文件，但是，请供子对象可以引用的对象。|  
|[CArchive::Read](../Topic/CArchive::Read.md)|读取原始的字节。|  
|[CArchive::ReadClass](../Topic/CArchive::ReadClass.md)|读取选件类的引用以前存储在 `WriteClass`。|  
|[CArchive::ReadObject](../Topic/CArchive::ReadObject.md)|调用对象的加载的 `Serialize` 功能。|  
|[CArchive::ReadString](../Topic/CArchive::ReadString.md)|读取一行文本。|  
|[CArchive::SerializeClass](../Topic/CArchive::SerializeClass.md)|读取或写入选件类对 `CArchive` 对象基于 `CArchive`的方向。|  
|[CArchive::SetLoadParams](../Topic/CArchive::SetLoadParams.md)|设置负载增加到数组的大小。  必须调用，则所有对象加载之前，或者在 `MapObject` 或 `ReadObject` 调用之前。|  
|[CArchive::SetObjectSchema](../Topic/CArchive::SetObjectSchema.md)|将存档对象中存储的对象模式。|  
|[CArchive::SetStoreParams](../Topic/CArchive::SetStoreParams.md)|设置哈希表的大小，并用于映射的块大小在序列化时标识单个对象的过程。|  
|[CArchive::Write](../Topic/CArchive::Write.md)|编写原始的字节。|  
|[CArchive::WriteClass](../Topic/CArchive::WriteClass.md)|写入 `CRuntimeClass` 的对 `CArchive`。|  
|[CArchive::WriteObject](../Topic/CArchive::WriteObject.md)|调用对象的存储 `Serialize` 功能。|  
|[CArchive::WriteString](../Topic/CArchive::WriteString.md)|编写一行文本。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CArchive::operator \<\<](../Topic/CArchive::operator%20%3C%3C.md)|存储对象与原类型到存档。|  
|[CArchive::operator \>\>](../Topic/CArchive::operator%20%3E%3E.md)|加载对象与原类型从存档。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CArchive::m\_pDocument](../Topic/CArchive::m_pDocument.md)||  
  
## 备注  
 `CArchive` 没有基类。  
  
 可以从永久性存储加载后对象，重建它们在内存中。  此过程使数据持久称为“序列化”。  
  
 可以将存档对象作为二进制流。  与输入\/输出流，存档与文件以及向\/从存储允许缓冲区的文本和数据读取器。  输入\/输出流处理ASCII字符序列，但是，存档处理二进制对象数据以有效，非多余的格式。  
  
 然后才能创建 `CArchive` 对象之前，必须创建 [C文件](../../mfc/reference/cfile-class.md) 对象。  此外，您还必须确保存档的加载\/存储状态与文件的打开模式兼容。  您限于一激活每个文件存档。  
  
 当构造 `CArchive` 对象，则附加到表示打开文件选件类 `CFile` \(或派生类\)的对象。  您还可以指定存档是否为加载或存储是使用。  `CArchive` 对象可以处理不仅 [CObject](../../mfc/reference/cobject-class.md)基元类型，还对象\-\-用于序列化模型的派生类。  可序列化选件类通常具有一个 `Serialize` 成员函数，因此，它通常使用 [DECLARE\_SERIAL](../Topic/DECLARE_SERIAL.md) 和 [IMPLEMENT\_SERIAL](../Topic/IMPLEMENT_SERIAL.md) 宏，如中所述在选件类 `CObject`下。  
  
 重载提取 \(**\>\>**\) 和插入 \(**\<\<**\) 运算符非常方便的存档支持两种基元类型和 `CObject`派生类的编程接口。  
  
 `CArchive` 还支持编程时MFC Windows套接字选件类 [CSocket](../../mfc/reference/csocket-class.md) 和 [CSocketFile](../../mfc/reference/csocketfile-class.md)。  [IsBufferEmpty](../Topic/CArchive::IsBufferEmpty.md) 成员函数支持该用法。  
  
 有关 `CArchive`的更多信息，请参见位于 [序列化](../../mfc/serialization-in-mfc.md) 和 [Windows套接字:使用套接字与存档](../../mfc/windows-sockets-using-sockets-with-archives.md)。  
  
## 继承层次结构  
 `CArchive`  
  
## 要求  
 **Header:** afx.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CFile Class](../../mfc/reference/cfile-class.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [CSocket Class](../../mfc/reference/csocket-class.md)   
 [CSocketFile Class](../../mfc/reference/csocketfile-class.md)