---
title: "CEnumerator::Open | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CEnumerator.Open"
  - "CEnumerator::Open"
  - "ATL::CEnumerator::Open"
  - "CEnumerator.Open"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Open 方法"
ms.assetid: b22821a0-257a-4543-ad0c-2649d4ac092e
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CEnumerator::Open
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

绑定该枚举器的名字对象，因此，如果指定一个回调方法\)，然后通过调用 [ISourcesRowset::GetSourcesRowset](https://msdn.microsoft.com/en-us/library/ms711200.aspx)枚举器检索的行集合。  
  
## 语法  
  
```  
  
      HRESULT Open(   
   LPMONIKER pMoniker    
) throw( );  
HRESULT Open(   
   const CLSID* pClsid = & CLSID_OLEDB_ENUMERATOR    
) throw( );  
HRESULT Open(   
   const CEnumerator& enumerator    
) throw( );  
```  
  
#### 参数  
 `pMoniker`  
 \[in\] 对命名对象的指针在枚举器的。  
  
 *pClsid*  
 \[in\] 对枚举器的 **CLSID** 的指针。  
  
 `enumerator`  
 \[in\] 对枚举器的引用。  
  
## 返回值  
 标准版`HRESULT`。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CEnumerator 类](../../data/oledb/cenumerator-class.md)