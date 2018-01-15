---
title: "CResourceException 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CResourceException
- AFXWIN/CResourceException
- AFXWIN/CResourceException::CResourceException
dev_langs: C++
helpviewer_keywords: CResourceException [MFC], CResourceException
ms.assetid: af6ae043-d124-4bfd-b35e-7bb0db67d289
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e2e17b859042a5712a998eaeebe9f16f81c91200
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cresourceexception-class"></a>CResourceException 类
当 Windows 无法找到或分配请求的资源时生成。  
  
## <a name="syntax"></a>语法  
  
```  
class CResourceException : public CSimpleException  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CResourceException::CResourceException](#cresourceexception)|构造 `CResourceException` 对象。|  
  
## <a name="remarks"></a>备注  
 没有进一步限定是必要或不可能。  
  
 有关详细信息使用`CResourceException`，请参阅文章[异常处理 (MFC)](../../mfc/exception-handling-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CResourceException`  
  
## <a name="requirements"></a>惠?  
 **标头:** afxwin.h  
  
##  <a name="cresourceexception"></a>CResourceException::CResourceException  
 构造 `CResourceException` 对象。  
  
```  
CResourceException();
```  
  
### <a name="remarks"></a>备注  
 不直接，使用此构造函数，但而是调用全局函数[AfxThrowResourceException](exception-processing.md#afxthrowresourceexception)。 有关异常的详细信息，请参阅文章[MFC 中的异常处理](../exception-handling-in-mfc.md)。  
  
## <a name="see-also"></a>请参阅  
 [CException 类](cexception-class.md)   
 [层次结构图](../hierarchy-chart.md)


