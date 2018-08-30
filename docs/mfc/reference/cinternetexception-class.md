---
title: CInternetException 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CInternetException [MFC], CInternetException
- CInternetException [MFC], m_dwContext
- CInternetException [MFC], m_dwError
ms.assetid: 44fb3cbe-523e-4754-8843-a77909990b14
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f1439fc2a5d49a775f55c7c25e45f4faa9b9c99f
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211272"
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
|[CInternetException::m_dwContext](#m_dwcontext)|与导致异常的操作关联的上下文值。|  
|[CInternetException::m_dwError](#m_dwerror)|导致异常的错误。|  
  
## <a name="remarks"></a>备注  
 `CInternetException`类包括两个公共数据成员： 一个包含与异常关联的错误代码和其他包含与错误关联 Internet 应用程序的上下文标识符。  
  
 有关的 Internet 应用程序的上下文标识符的详细信息，请参阅文章[Internet 编程与 WinInet](../../mfc/win32-internet-extensions-wininet.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CInternetException`  
  
## <a name="requirements"></a>要求  
 **标头：** afxinet.h  
  
##  <a name="cinternetexception"></a>  CInternetException::CInternetException  
 此成员函数调用时`CInternetException`创建对象。  
  
```  
CInternetException(DWORD dwError);
```  
  
### <a name="parameters"></a>参数  
 *dwError*  
 导致异常的错误。  
  
### <a name="remarks"></a>备注  
 若要引发 CInternetException，调用 MFC 全局函数[AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception)。  
  
##  <a name="m_dwcontext"></a>  CInternetException::m_dwContext  
 上下文值和相关 Internet 操作相关联。  
  
```  
DWORD_PTR m_dwContext;  
```  
  
### <a name="remarks"></a>备注  
 中最初指定的上下文标识符[CInternetSession](../../mfc/reference/cinternetsession-class.md)并传递到 MFC [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)-并[CInternetFile](../../mfc/reference/cinternetfile-class.md)-派生的类。 您可以覆盖此默认值并分配任何*dwContext*参数所选的值。 *dwContext*与给定任何的对象操作相关联。 *dwContext*标识返回的操作的状态信息[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)。  
  
##  <a name="m_dwerror"></a>  CInternetException::m_dwError  
 导致异常的错误。  
  
```  
DWORD m_dwError;  
```  
  
### <a name="remarks"></a>备注  
 此错误值可能是一个系统错误代码，在 WINERROR 中找到。H 或从 WININET 错误值。H.  
  
 有关 Win32 错误代码的列表，请参阅[错误代码](/windows/desktop/Debug/system-error-codes)。 有关特定于 Internet 的错误消息的列表，请参阅。 这两个主题是 Windows SDK 中。  
  
## <a name="see-also"></a>请参阅  
 [CException 类](../../mfc/reference/cexception-class.md)   
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [CException 类](../../mfc/reference/cexception-class.md)
