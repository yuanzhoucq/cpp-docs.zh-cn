---
title: "CInvalidArgException 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CInvalidArgException
dev_langs:
- C++
helpviewer_keywords:
- CInvalidArgException class
ms.assetid: e43d7c67-1157-47f8-817a-804083e8186e
caps.latest.revision: 19
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
ms.openlocfilehash: 4091c0e8a35320482eba193c89c90982c7e4fca9
ms.lasthandoff: 02/24/2017

---
# <a name="cinvalidargexception-class"></a>CInvalidArgException 类
此类表示一个无效自变量异常条件。  
  
## <a name="syntax"></a>语法  
  
```  
class CInvalidArgException : public CSimpleException  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CInvalidArgException::CInvalidArgException](#cinvalidargexception)|构造函数。|  
  
## <a name="remarks"></a>备注  
 一个`CInvalidArgException`对象都表示一个无效参数异常条件。  
  
 异常处理的详细信息，请参阅[CException 类](../../mfc/reference/cexception-class.md)主题和[异常处理 (MFC)](../../mfc/exception-handling-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CInvalidArgException`  
  
## <a name="requirements"></a>要求  
 **标头：** afx.h  
  
##  <a name="a-namecinvalidargexceptiona--cinvalidargexceptioncinvalidargexception"></a><a name="cinvalidargexception"></a>CInvalidArgException::CInvalidArgException  
 构造函数。  
  
```  
CInvalidArgException();
```  
  
### <a name="remarks"></a>备注  
 直接调用不使用此构造函数调用全局函数**AfxThrowInvalidArgException**。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CSimpleException 类](../../mfc/reference/csimpleexception-class.md)

