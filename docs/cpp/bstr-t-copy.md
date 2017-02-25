---
title: "_bstr_t::copy | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_bstr_t::copy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BSTR 对象, copy"
  - "Copy 方法"
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# _bstr_t::copy
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 构造封装的 `BSTR` 的副本。  
  
## 语法  
  
```  
  
      BSTR copy(  
  bool fCopy = true  
) const;  
```  
  
#### 参数  
 `fCopy`  
 如果为 **true**，则 **copy** 将返回包含的 `BSTR` 的副本；否则，**copy** 将返回实际的 BSTR。  
  
## 备注  
 返回封装的 `BSTR` 对象的新分配的副本。  
  
## 示例  
  
```  
STDMETHODIMP CAlertMsg::get_ConnectionStr(BSTR *pVal){ //  m_bsConStr is _bstr_t  
   *pVal = m_bsConStr.copy();  
}  
```  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_bstr\_t 类](../cpp/bstr-t-class.md)