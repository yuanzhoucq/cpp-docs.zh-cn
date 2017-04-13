---
title: "CInternetException 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CInternetException
- AFXINET/CInternetException
- AFXINET/CInternetException::CInternetException
- AFXINET/CInternetException::m_dwContext
- AFXINET/CInternetException::m_dwError
dev_langs:
- C++
helpviewer_keywords:
- exception handling, Internet operations
- exceptions, Internet
- CInternetException class
ms.assetid: 44fb3cbe-523e-4754-8843-a77909990b14
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
translationtype: Machine Translation
ms.sourcegitcommit: bb94e24657d16b2a3eda3a770c2b6ae734c6006f
ms.openlocfilehash: 1831f868b7388cbc6382e26fca92280c3b880276
ms.lasthandoff: 04/12/2017

---
# <a name="cinternetexception-class"></a>CInternetException 类
表示与 Internet 操作相关的异常条件。  
  
## <a name="syntax"></a>语法  
  
```  
class CInternetException : public CException  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CInternetException::CInternetException](#cinternetexception)|构造 `CInternetException` 对象。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CInternetException::m_dwContext](#m_dwcontext)|导致异常的操作与关联的上下文值。|  
|[CInternetException::m_dwError](#m_dwerror)|导致异常的错误。|  
  
## <a name="remarks"></a>备注  
 `CInternetException`类包括两个公共数据成员︰ 一个包含与此异常关联的错误代码和其他包含与错误关联 Internet 应用程序的上下文标识符。  
  
 有关 Internet 应用程序的上下文标识符的详细信息，请参阅文章[Internet 使用 WinInet 编程](../../mfc/win32-internet-extensions-wininet.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CInternetException`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxinet.h  
  
##  <a name="cinternetexception"></a>CInternetException::CInternetException  
 此成员函数调用时`CInternetException`创建对象。  
  
```  
CInternetException(DWORD dwError);
```  
  
### <a name="parameters"></a>参数  
 `dwError`  
 导致异常的错误。  
  
### <a name="remarks"></a>备注  
 若要引发 CInternetException，调用 MFC 全局函数[AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception)。  
  
##  <a name="m_dwcontext"></a>CInternetException::m_dwContext  
 上下文值和相关 Internet 操作相关联。  
  
```  
DWORD_PTR m_dwContext;  
```  
  
### <a name="remarks"></a>备注  
 中最初指定的上下文标识符[CInternetSession](../../mfc/reference/cinternetsession-class.md)和传递到 MFC 的[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)-和[CInternetFile](../../mfc/reference/cinternetfile-class.md)-派生类。 你可以重写此默认值并分配任何`dwContext`参数选择的值。 `dwContext`是与给定任何的操作相关联。 `dwContext`标识返回的操作的状态信息[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)。  
  
##  <a name="m_dwerror"></a>CInternetException::m_dwError  
 导致异常的错误。  
  
```  
DWORD m_dwError;  
```  
  
### <a name="remarks"></a>备注  
 此错误值可能是系统错误代码，在 WINERROR 中找到。H 或从 WININET 一个错误值。H。  
  
 有关 Win32 错误代码的列表，请参阅[错误代码](http://msdn.microsoft.com/library/windows/desktop/ms681381)。 有关特定于 Internet 的错误消息的列表，请参阅。 这两个主题位于[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [CException 类](../../mfc/reference/cexception-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CException 类](../../mfc/reference/cexception-class.md)

