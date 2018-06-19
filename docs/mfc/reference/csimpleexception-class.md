---
title: CSimpleException 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSimpleException
- AFX/CSimpleException
- AFX/CSimpleException::CSimpleException
- AFX/CSimpleException::GetErrorMessage
dev_langs:
- C++
helpviewer_keywords:
- CSimpleException [MFC], CSimpleException
- CSimpleException [MFC], GetErrorMessage
ms.assetid: be0eb8ef-e5b9-47d6-b0fb-efaff2d1e666
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7d04a2f643add489d3302e58a9bde995303ecddd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369920"
---
# <a name="csimpleexception-class"></a>CSimpleException 类
此类是资源重要的 MFC 异常的基类。  
  
## <a name="syntax"></a>语法  
  
```  
class AFX_NOVTABLE CSimpleException : public CException  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CSimpleException::CSimpleException](#csimpleexception)|构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CSimpleException::GetErrorMessage](#geterrormessage)|提供有关已发生错误的文本。|  
  
## <a name="remarks"></a>备注  
 `CSimpleException` 是资源重要的 MFC 异常的基类和处理的所有权和初始化的一条错误消息。 下面的类使用`CSimpleException`作为其基类：  
  
|||  
|-|-|  
|[CMemoryException 类](../../mfc/reference/cmemoryexception-class.md)|内存不足异常|  
|[CNotSupportedException 类](../../mfc/reference/cnotsupportedexception-class.md)|不支持的操作的请求|  
|[CResourceException 类](../../mfc/reference/cresourceexception-class.md)|找不到或不能创建 Windows 资源|  
|[CUserException 类](../../mfc/reference/cuserexception-class.md)|找不到表示资源的异常|  
|[CInvalidArgException 类](../../mfc/reference/cinvalidargexception-class.md)|异常，该值指示参数无效|  
  
 因为`CSimpleException`是一个抽象基类，您無法宣告`CSimpleException`直接对象。 相反，您必须声明派生的对象，例如那些上表中。 如果你声明派生的类，作为一种模式中使用的以前的类。  
  
 有关详细信息，请参阅[CException 类](../../mfc/reference/cexception-class.md)主题和[异常处理 (MFC)](../../mfc/exception-handling-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CSimpleException`  
  
## <a name="requirements"></a>要求  
 **标头：** afx.h  
  
##  <a name="csimpleexception"></a>  CSimpleException::CSimpleException  
 构造函数。  
  
```  
CSimpleException();  
explicit CSimpleException(BOOL bAutoDelete);
```  
  
### <a name="parameters"></a>参数  
 `bAutoDelete`  
 指定**TRUE**如果的内存`CSimpleException`在堆中分配对象。 这将导致`CSimpleException`时删除的对象**删除**调用成员函数删除异常。 指定**FALSE**如果`CSimpleException`对象位于堆栈，或者是一个全局对象。 在这种情况下，`CSimpleException`对象不会删除时**删除**调用成员函数。  
  
### <a name="remarks"></a>备注  
 你将通常无需直接调用此构造函数。 引发异常的函数应创建的实例`CException`-派生类并调用其构造函数，或它应使用的 MFC 如引发函数， [AfxThrowFileException](exception-processing.md#afxthrowfileexception)、 引发的预定义的类型。  
  
##  <a name="geterrormessage"></a>  CSimpleException::GetErrorMessage  
 调用此成员函数以提供有关已发生错误的文本。  
  
```  
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT  nMaxError,
    PUNIT  pnHelpContext = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpszError`  
 指向将收到一条错误消息的缓冲区的指针。  
  
 `nMaxError`  
 最大缓冲区可以容纳，包括的字符数**NULL**终止符。  
  
 `pnHelpContext`  
 地址**UINT** ，将收到帮助上下文 id。 如果**NULL**，将返回没有 ID。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零否则，如果没有错误消息文本为 0 将用。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[CException::GetErrorMessage](../../mfc/reference/cfileexception-class.md#geterrormessage)。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CException 类](../../mfc/reference/cexception-class.md)   
 [异常处理](../../mfc/exception-handling-in-mfc.md)



