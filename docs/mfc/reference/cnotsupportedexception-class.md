---
title: CNotSupportedException 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CNotSupportedException
- AFX/CNotSupportedException
- AFX/CNotSupportedException::CNotSupportedException
dev_langs:
- C++
helpviewer_keywords:
- CNotSupportedException [MFC], CNotSupportedException
ms.assetid: e517391b-eb94-4c39-ae32-87b45bf7d624
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 510f9db4a7e5688df76baafa868846fd1614f584
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33367485"
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
 没有进一步限定是必要或不可能。  
  
 有关详细信息使用`CNotSupportedException`，请参阅文章[异常处理 (MFC)](../../mfc/exception-handling-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CNotSupportedException`  
  
## <a name="requirements"></a>要求  
 **标头：** afx.h  
  
##  <a name="cnotsupportedexception"></a>  CNotSupportedException::CNotSupportedException  
 构造 `CNotSupportedException` 对象。  
  
```  
CNotSupportedException();
```  
  
### <a name="remarks"></a>备注  
 不直接，使用此构造函数，但而是调用全局函数[AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception)。 有关异常处理的详细信息，请参阅文章[MFC 中的异常处理](../exception-handling-in-mfc.md)。  
  
## <a name="see-also"></a>请参阅  
 [CException 类](cexception-class.md)   
 [层次结构图](../hierarchy-chart.md)


