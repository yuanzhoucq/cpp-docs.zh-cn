---
title: "CNotSupportedException 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CNotSupportedException
- AFX/CNotSupportedException
- AFX/CNotSupportedException::CNotSupportedException
dev_langs:
- C++
helpviewer_keywords:
- CNotSupportedException class
- unsupported features
- exceptions, not supported
ms.assetid: e517391b-eb94-4c39-ae32-87b45bf7d624
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
ms.openlocfilehash: 6cb66448d0dadaf1f70c3606bc1b9027bd217a38
ms.lasthandoff: 02/24/2017

---
# <a name="cnotsupportedexception-class"></a>CNotSupportedException 类
表示因请求不支持的功能而引起的异常。  
  
## <a name="syntax"></a>语法  
  
```  
class CNotSupportedException : public CSimpleException  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CNotSupportedException::CNotSupportedException](#cnotsupportedexception)|构造 `CNotSupportedException` 对象。|  
  
## <a name="remarks"></a>备注  
 没有进一步限定是有必要或不可能。  
  
 有关详细信息使用`CNotSupportedException`，请参阅文章[异常处理 (MFC)](../../mfc/exception-handling-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CNotSupportedException`  
  
## <a name="requirements"></a>要求  
 **标头：** afx.h  
  
##  <a name="cnotsupportedexception"></a>CNotSupportedException::CNotSupportedException  
 构造 `CNotSupportedException` 对象。  
  
```  
CNotSupportedException();
```  
  
### <a name="remarks"></a>备注  
 不直接使用此构造函数，但而是调用全局函数[AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception)。 有关异常处理的详细信息，请参阅文章[Exception Handling in MFC](../exception-handling-in-mfc.md)。  
  
## <a name="see-also"></a>另请参阅  
 [CException 类](cexception-class.md)   
 [层次结构图](../hierarchy-chart.md)



