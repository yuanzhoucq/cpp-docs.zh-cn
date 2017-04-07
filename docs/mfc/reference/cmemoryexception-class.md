---
title: "CMemoryException 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMemoryException
- AFX/CMemoryException
- AFX/CMemoryException::CMemoryException
dev_langs:
- C++
helpviewer_keywords:
- CMemoryException class
- memory exceptions
- exceptions, memory type
- C++ exception handling, memory
- memory, exception handling
ms.assetid: 9af0ed57-d12a-45ca-82b5-c910a60f7edf
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 87be1b16d546791d24bbffa62207ec9ccb350139
ms.lasthandoff: 02/24/2017

---
# <a name="cmemoryexception-class"></a>CMemoryException 类
表示内存不足异常条件。  
  
## <a name="syntax"></a>语法  
  
```  
class CMemoryException : public CSimpleException  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CMemoryException::CMemoryException](#cmemoryexception)|构造 `CMemoryException` 对象。|  
  
## <a name="remarks"></a>备注  
 没有进一步限定是有必要或不可能。 自动引发内存异常**新**。 如果您编写您自己的内存的函数，使用`malloc`，请为示例中，则您负责引发内存异常。  
  
 有关详细信息`CMemoryException`，请参阅文章[异常处理 (MFC)](../../mfc/exception-handling-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CMemoryException`  
  
## <a name="requirements"></a>要求  
 **标头：** afx.h  
  
##  <a name="cmemoryexception"></a>CMemoryException::CMemoryException  
 构造 `CMemoryException` 对象。  
  
```  
CMemoryException();  
```  
  
### <a name="remarks"></a>备注  
 不直接使用此构造函数，但而是调用全局函数[AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception)。 此全局函数才能成功执行在内存不足的情况下，因为它构造以前分配的内存中的异常对象。 有关异常处理的详细信息，请参阅文章[异常](../exception-handling-in-mfc.md)。  
  
## <a name="see-also"></a>另请参阅  
 [CException 类](cexception-class.md)   
 [层次结构图](../hierarchy-chart.md)




