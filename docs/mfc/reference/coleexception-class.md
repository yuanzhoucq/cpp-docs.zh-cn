---
title: COleException 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleException
- AFXDISP/COleException
- AFXDISP/COleException::Process
- AFXDISP/COleException::m_sc
dev_langs:
- C++
helpviewer_keywords:
- COleException [MFC], Process
- COleException [MFC], m_sc
ms.assetid: 2571e9fe-26cc-42f0-9ad9-8ad5b4311ec1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 731ec7b359995fc8ecbfdeae89595442d8186eeb
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2018
ms.locfileid: "37851387"
---
# <a name="coleexception-class"></a>COleException 类
表示与 OLE 操作相关的异常条件。  
  
## <a name="syntax"></a>语法  
  
```  
class COleException : public CException  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[COleException::Process](#process)|将转换为 OLE 返回代码捕获的异常。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[COleException::m_sc](#m_sc)|包含指示异常原因的状态代码。|  
  
## <a name="remarks"></a>备注  
 `COleException`类包含保存的状态代码指示异常原因的公共数据成员。  
  
 一般情况下，不应创建`COleException`对象直接; 相反，应调用[AfxThrowOleException](exception-processing.md#afxthrowoleexception)。  
  
 有关异常的详细信息，请参阅文章[异常处理 (MFC)](../../mfc/exception-handling-in-mfc.md)并[异常： OLE 异常](../../mfc/exceptions-ole-exceptions.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `COleException`  
  
## <a name="requirements"></a>要求  
 **标头：** afxdisp.h  
  
##  <a name="m_sc"></a>  COleException::m_sc  
 此数据成员保留指示异常原因的 OLE 状态代码。  
  
```  
SCODE m_sc;  
```  
  
### <a name="remarks"></a>备注  
 设置此变量的值[AfxThrowOleException](exception-processing.md#afxthrowoleexception)。  
  
 SCODE 的详细信息，请参阅[COM 错误代码的结构](http://msdn.microsoft.com/library/windows/desktop/ms690088)Windows SDK 中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCOleContainer#22](../../mfc/codesnippet/cpp/coleexception-class_1.cpp)]  
  
##  <a name="process"></a>  COleException::Process  
 调用**进程**成员函数将转换为 OLE 状态代码捕获的异常。  
  
```  
static SCODE PASCAL Process(const CException* pAnyException);
```  
  
### <a name="parameters"></a>参数  
 *pAnyException*  
 为捕获的异常的指针。  
  
### <a name="return-value"></a>返回值  
 OLE 状态代码。  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  此函数是**静态**。  
  
 SCODE 的详细信息，请参阅[COM 错误代码的结构](http://msdn.microsoft.com/library/windows/desktop/ms690088)Windows SDK 中。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[coledispatchdriver:: Createdispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch)。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 CALCDRIV](../../visual-cpp-samples.md)   
 [CException 类](../../mfc/reference/cexception-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)



