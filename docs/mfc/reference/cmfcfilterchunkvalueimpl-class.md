---
title: "CMFCFilterChunkValueImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCFilterChunkValueImpl"
  - "afxwin/CMFCFilterChunkValueImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCFilterChunkValueImpl class"
ms.assetid: 3c833f23-5b88-4d08-9e09-ca6a8aec88bf
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CMFCFilterChunkValueImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

这是简化块，而且属性值匹配逻辑的选件类。  
  
## 语法  
  
```  
class CMFCFilterChunkValueImpl : public ATL::IFilterChunkValue;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCFilterChunkValueImpl::~CMFCFilterChunkValueImpl](../Topic/CMFCFilterChunkValueImpl::~CMFCFilterChunkValueImpl.md)|析构对象。|  
|[CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl](../Topic/CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl.md)|构造对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCFilterChunkValueImpl::Clear](../Topic/CMFCFilterChunkValueImpl::Clear.md)|清除ChunkValue。|  
|[CMFCFilterChunkValueImpl::CopyChunk](../Topic/CMFCFilterChunkValueImpl::CopyChunk.md)|复制此区块指向描述块的属性结构。|  
|[CMFCFilterChunkValueImpl::CopyFrom](../Topic/CMFCFilterChunkValueImpl::CopyFrom.md)|初始化从其他值的按区块此值。|  
|[CMFCFilterChunkValueImpl::GetChunkGUID](../Topic/CMFCFilterChunkValueImpl::GetChunkGUID.md)|检索区块GUID。|  
|[CMFCFilterChunkValueImpl::GetChunkPID](../Topic/CMFCFilterChunkValueImpl::GetChunkPID.md)|检索区块PID \(属性ID）。|  
|[CMFCFilterChunkValueImpl::GetChunkType](../Topic/CMFCFilterChunkValueImpl::GetChunkType.md)|获取块类型。|  
|[CMFCFilterChunkValueImpl::GetString](../Topic/CMFCFilterChunkValueImpl::GetString.md)|检索字符串值。|  
|[CMFCFilterChunkValueImpl::GetValue](../Topic/CMFCFilterChunkValueImpl::GetValue.md)|检索值作为已分配的propvariant。|  
|[CMFCFilterChunkValueImpl::GetValueNoAlloc](../Topic/CMFCFilterChunkValueImpl::GetValueNoAlloc.md)|returns非分配了\(内部值\)值。|  
|[CMFCFilterChunkValueImpl::IsValid](../Topic/CMFCFilterChunkValueImpl::IsValid.md)|检查是否该属性值是否有效。|  
|[CMFCFilterChunkValueImpl::SetBoolValue](../Topic/CMFCFilterChunkValueImpl::SetBoolValue.md)|已重载。  由键属性设置为布尔值。|  
|[CMFCFilterChunkValueImpl::SetDwordValue](../Topic/CMFCFilterChunkValueImpl::SetDwordValue.md)|由键属性设置为一个。|  
|[CMFCFilterChunkValueImpl::SetFileTimeValue](../Topic/CMFCFilterChunkValueImpl::SetFileTimeValue.md)|由键属性设置为filetime。|  
|[CMFCFilterChunkValueImpl::SetInt64Value](../Topic/CMFCFilterChunkValueImpl::SetInt64Value.md)|由键属性设置为int64。|  
|[CMFCFilterChunkValueImpl::SetIntValue](../Topic/CMFCFilterChunkValueImpl::SetIntValue.md)|由键属性设置为int。|  
|[CMFCFilterChunkValueImpl::SetLongValue](../Topic/CMFCFilterChunkValueImpl::SetLongValue.md)|由键属性设置为长。|  
|[CMFCFilterChunkValueImpl::SetSystemTimeValue](../Topic/CMFCFilterChunkValueImpl::SetSystemTimeValue.md)|由键属性设置为SystemTime。|  
|[CMFCFilterChunkValueImpl::SetTextValue](../Topic/CMFCFilterChunkValueImpl::SetTextValue.md)|由键属性设置为Unicode字符串。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCFilterChunkValueImpl::SetChunk](../Topic/CMFCFilterChunkValueImpl::SetChunk.md)|设置区块的通用属性的helper函数。|  
  
## 备注  
 若要使用，您创建正确的类型的CMFCFilterChunkValueImpl选件类  
  
 示例：  
  
 CMFCFilterChunkValueImpl区块;  
  
 hr \= chunk.SetBoolValue \(PKEY\_IsAttachment，为true\);  
  
 或  
  
 hr \= chunk.SetFileTimeValue \(PKEY\_ItemDate，ftLastModified\);  
  
## 继承层次结构  
 `ATL::IFilterChunkValue`  
  
 [CMFCFilterChunkValueImpl](../../mfc/reference/cmfcfilterchunkvalueimpl-class.md)  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)