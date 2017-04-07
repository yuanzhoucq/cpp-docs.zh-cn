---
title: "COleDispatchException 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDispatchException
- AFXDISP/COleDispatchException
- AFXDISP/COleDispatchException::m_dwHelpContext
- AFXDISP/COleDispatchException::m_strDescription
- AFXDISP/COleDispatchException::m_strHelpFile
- AFXDISP/COleDispatchException::m_strSource
- AFXDISP/COleDispatchException::m_wCode
dev_langs:
- C++
helpviewer_keywords:
- COleDispatchException class
- Automation, exceptions
- exceptions, OLE
- OLE exceptions, to IDispatch interface
ms.assetid: 0e95c8be-e21a-490c-99ec-181c6a9a26d0
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
ms.openlocfilehash: 0071e57b6c8f6bec73712186e8ff8baa9bfcc165
ms.lasthandoff: 02/24/2017

---
# <a name="coledispatchexception-class"></a>COleDispatchException 类
处理特定于 OLE `IDispatch` 接口的异常，此接口是 OLE 自动化的重要组成部分。  
  
## <a name="syntax"></a>语法  
  
```  
class COleDispatchException : public CException  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[COleDispatchException::m_dwHelpContext](#m_dwhelpcontext)|错误的帮助上下文。|  
|[COleDispatchException::m_strDescription](#m_strdescription)|口头错误说明。|  
|[COleDispatchException::m_strHelpFile](#m_strhelpfile)|帮助文件中使用`m_dwHelpContext`。|  
|[COleDispatchException::m_strSource](#m_strsource)|生成异常的应用程序。|  
|[COleDispatchException::m_wCode](#m_wcode)|`IDispatch`-特定错误代码。|  
  
## <a name="remarks"></a>备注  
 像其他异常类派生自`CException`基类，`COleDispatchException`可以与使用**引发**， `THROW_LAST`，**尝试**，**捕获**， `AND_CATCH`，和`END_CATCH`宏。  
  
 一般情况下，应调用[AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception)创建并引发`COleDispatchException`对象。  
  
 有关异常的详细信息，请参阅文章[异常处理 (MFC)](../../mfc/exception-handling-in-mfc.md)和[异常︰ OLE 异常](../../mfc/exceptions-ole-exceptions.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `COleDispatchException`  
  
## <a name="requirements"></a>要求  
 **标头：** afxdisp.h  
  
##  <a name="m_dwhelpcontext"></a>COleDispatchException::m_dwHelpContext  
 标识应用程序的帮助中的帮助上下文 (。HLP) 文件。  
  
```  
DWORD m_dwHelpContext;  
```  
  
### <a name="remarks"></a>备注  
 此成员将由该函数[AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception)时将引发异常。  
  
### <a name="example"></a>示例  
  请参阅示例[COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch)。  
  
##  <a name="m_strdescription"></a>COleDispatchException::m_strDescription  
 包含一个口头错误说明，如"磁盘已满。"  
  
```  
CString m_strDescription;  
```  
  
### <a name="remarks"></a>备注  
 此成员将由该函数[AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception)时将引发异常。  
  
### <a name="example"></a>示例  
  请参阅示例[COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch)。  
  
##  <a name="m_strhelpfile"></a>COleDispatchException::m_strHelpFile  
 框架填充应用程序的帮助文件的名称与此字符串中。  
  
```  
CString m_strHelpFile;  
```  
  
##  <a name="m_strsource"></a>COleDispatchException::m_strSource  
 框架填充的应用程序生成了异常的名称与此字符串中。  
  
```  
CString m_strSource;  
```  
  
### <a name="example"></a>示例  
  请参阅示例[COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch)。  
  
##  <a name="m_wcode"></a>COleDispatchException::m_wCode  
 包含特定于您的应用程序的错误代码。  
  
```  
WORD m_wCode;  
```  
  
### <a name="remarks"></a>备注  
 此成员将由该函数[AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception)时将引发异常。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 CALCDRIV](../../visual-cpp-samples.md)   
 [CException 类](../../mfc/reference/cexception-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDispatchDriver 类](../../mfc/reference/coledispatchdriver-class.md)   
 [COleException 类](../../mfc/reference/coleexception-class.md)

