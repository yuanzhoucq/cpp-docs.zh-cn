---
title: CResourceException 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CResourceException
- AFXWIN/CResourceException
- AFXWIN/CResourceException::CResourceException
dev_langs:
- C++
helpviewer_keywords:
- CResourceException [MFC], CResourceException
ms.assetid: af6ae043-d124-4bfd-b35e-7bb0db67d289
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6fdbfb29b00eaac40b4da2b78753df6a0596764f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33371525"
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
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="cresourceexception"></a>  CResourceException::CResourceException  
 构造 `CResourceException` 对象。  
  
```  
CResourceException();
```  
  
### <a name="remarks"></a>备注  
 不直接，使用此构造函数，但而是调用全局函数[AfxThrowResourceException](exception-processing.md#afxthrowresourceexception)。 有关异常的详细信息，请参阅文章[MFC 中的异常处理](../exception-handling-in-mfc.md)。  
  
## <a name="see-also"></a>请参阅  
 [CException 类](cexception-class.md)   
 [层次结构图](../hierarchy-chart.md)


