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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: a128095cfc443f0ea8de4cb4028b903929a83f47
ms.lasthandoff: 02/24/2017

---
# <a name="cinternetexception-class"></a>CInternetException 类
表示与 Internet 操作相关的异常条件。  
  
## <a name="syntax"></a>语法  
  
```  
class CInternetException : public CException  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CInternetException::CInternetException](#cinternetexception)|构造 `CInternetException` 对象。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CInternetException::m_dwContext](#m_dwcontext)|与操作引发异常的异常关联的上下文值。|  
|[CInternetException::m_dwError](#m_dwerror)|导致该异常的错误。|  
  
## <a name="remarks"></a>备注  
 `CInternetException`类包括两个公共数据成员︰ 一个包含与该异常关联的错误代码和其他包含与错误关联的 Internet 应用程序的上下文标识符。  
  
 有关 Internet 应用程序的上下文标识符的详细信息，请参阅文章[Internet 编程与 WinInet](../../mfc/win32-internet-extensions-wininet.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CInternetException`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxinet.h  
  
##  <a name="a-namecinternetexceptiona--cinternetexceptioncinternetexception"></a><a name="cinternetexception"></a>CInternetException::CInternetException  
 当调用此成员函数`CInternetException`创建对象。  
  
```  
CInternetException(DWORD dwError);
```  
  
### <a name="parameters"></a>参数  
 `dwError`  
 导致该异常的错误。  
  
### <a name="remarks"></a>备注  
 若要引发 CInternetException，调用 MFC 全局函数[AfxThrowInternetException](http://msdn.microsoft.com/library/c9645b10-9541-48b2-8b0c-94ca33fed3cb)。  
  
##  <a name="a-namemdwcontexta--cinternetexceptionmdwcontext"></a><a name="m_dwcontext"></a>CInternetException::m_dwContext  
 上下文值和相关 Internet 操作相关联。  
  
```  
DWORD_PTR m_dwContext;  
```  
  
### <a name="remarks"></a>备注  
 在最初指定的上下文标识符[CInternetSession](../../mfc/reference/cinternetsession-class.md)并传递由 MFC 到[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)-和[CInternetFile](../../mfc/reference/cinternetfile-class.md)的派生类。 您可以覆盖此默认值并分配任何`dwContext`参数所选的值。 `dwContext`程序与给定任何的对象操作。 `dwContext`标识返回的操作的状态信息[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)。  
  
##  <a name="a-namemdwerrora--cinternetexceptionmdwerror"></a><a name="m_dwerror"></a>CInternetException::m_dwError  
 导致该异常的错误。  
  
```  
DWORD m_dwError;  
```  
  
### <a name="remarks"></a>备注  
 此错误值可能是系统在 WINERROR 中找到的错误代码。H 或从 WININET 错误值。H。  
  
 有关 Win32 错误代码的列表，请参阅[错误代码](http://msdn.microsoft.com/library/windows/desktop/ms681381)。 有关特定于 Internet 的错误消息的列表，请参阅。 这两个主题位于[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [CException 类](../../mfc/reference/cexception-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CException 类](../../mfc/reference/cexception-class.md)

