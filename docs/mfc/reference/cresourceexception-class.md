---
title: "CResourceException 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CResourceException
- AFXWIN/CResourceException
- AFXWIN/CResourceException::CResourceException
dev_langs:
- C++
helpviewer_keywords:
- resource allocation exception
- resources [C++], allocating
- resource exceptions
- exceptions, resource
- CResourceException class
ms.assetid: af6ae043-d124-4bfd-b35e-7bb0db67d289
caps.latest.revision: 22
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 2013a73f91687277df9dd1e6747aba2dd02a4346
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cresourceexception-class"></a>CResourceException 类
当 Windows 无法找到或分配请求的资源时生成。  
  
## <a name="syntax"></a>语法  
  
```  
class CResourceException : public CSimpleException  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CResourceException::CResourceException](#cresourceexception)|构造 `CResourceException` 对象。|  
  
## <a name="remarks"></a>备注  
 没有进一步限定是有必要或不可能。  
  
 有关详细信息使用`CResourceException`，请参阅文章[异常处理 (MFC)](../../mfc/exception-handling-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CResourceException`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="cresourceexception"></a>CResourceException::CResourceException  
 构造 `CResourceException` 对象。  
  
```  
CResourceException();
```  
  
### <a name="remarks"></a>备注  
 不直接使用此构造函数，但而是调用全局函数[AfxThrowResourceException](exception-processing.md#afxthrowresourceexception)。 关于异常的详细信息，请参阅文章[Exception Handling in MFC](../exception-handling-in-mfc.md)。  
  
## <a name="see-also"></a>另请参阅  
 [CException 类](cexception-class.md)   
 [层次结构图](../hierarchy-chart.md)



