---
title: CArchiveException 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CArchiveException
- AFX/CArchiveException
- AFX/CArchiveException::CArchiveException
- AFX/CArchiveException::m_cause
- AFX/CArchiveException::m_strFileName
dev_langs:
- C++
helpviewer_keywords:
- CArchiveException [MFC], CArchiveException
- CArchiveException [MFC], m_cause
- CArchiveException [MFC], m_strFileName
ms.assetid: da31a127-e86c-41d1-b0b6-bed0865b1b49
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac864831e9d3a0cf0cd5e67501f1ac8396f99473
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="carchiveexception-class"></a>CArchiveException 类
表示序列化异常条件  
  
## <a name="syntax"></a>语法  
  
```  
class CArchiveException : public CException  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CArchiveException::CArchiveException](#carchiveexception)|构造 `CArchiveException` 对象。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CArchiveException::m_cause](#m_cause)|指示的异常原因。|  
|[CArchiveException::m_strFileName](#m_strfilename)|指定此异常条件的文件的名称。|  
  
## <a name="remarks"></a>备注  
 `CArchiveException`类包括一个公共数据成员，该值指示对导致异常。  
  
 `CArchiveException` 对象了构造和内引发[CArchive](../../mfc/reference/carchive-class.md)成员函数。 你可以访问这些对象的作用域内**捕获**表达式。 原因代码是独立于操作系统。 有关异常处理的详细信息，请参阅[异常处理 (MFC)](../../mfc/exception-handling-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CArchiveException`  
  
## <a name="requirements"></a>要求  
 **标头：** afx.h  
  
##  <a name="carchiveexception"></a>  CArchiveException::CArchiveException  
 构造`CArchiveException`对象，存储的值`cause`对象中。  
  
```  
CArchiveException(
    int cause = CArchiveException::none,  
    LPCTSTR lpszArchiveName = NULL);
```  
  
### <a name="parameters"></a>参数  
 `cause`  
 一个枚举的类型变量，指示该异常的原因。 枚举器的列表，请参阅[m_cause](#m_cause)数据成员。  
  
 `lpszArchiveName`  
 指向包含的名称的字符串`CArchive`引发异常的对象。  
  
### <a name="remarks"></a>备注  
 你可以创建`CArchiveException`堆上对象而引发它自己或让全局函数[AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)为你处理。  
  
 不要直接; 使用此构造函数相反，调用全局函数`AfxThrowArchiveException`。  
  
##  <a name="m_cause"></a>  CArchiveException::m_cause  
 指定的异常的原因。  
  
```  
int m_cause;  
```  
  
### <a name="remarks"></a>备注  
 此数据成员是类型 `int` 的公共变量。 由定义其值`CArchiveException`枚举类型。 枚举器及其含义如下所示：  
  
- **CArchiveException::none**未发生错误。  
  
- **CArchiveException::genericException**未指定的错误。  
  
- **CArchiveException::readOnly**尝试写入到适用于加载的打开的存档。  
  
- **CArchiveException::endOfFile**读取对象时已达到最终的文件。  
  
- **CArchiveException::writeOnly**尝试从用于存储打开的存档中读取。  
  
- **CArchiveException::badIndex**文件格式无效。  
  
- **CArchiveException::badClass**尝试读取某个对象为错误类型的对象。  
  
- **CArchiveException::badSchema**尝试读取具有不同版本的类的对象。  
  
    > [!NOTE]
    >  引发这些 `CArchiveException` 的枚举器不同于引发 `CFileException` 的枚举器。  
  
    > [!NOTE]
    > **CArchiveException::generic**已弃用。 使用**genericException**相反。 如果**泛型**是应用程序中使用和生成使用 /clr，将很难解密的语法错误。  
  
##  <a name="m_strfilename"></a>  CArchiveException::m_strFileName  
 指定此异常条件的文件的名称。  
  
```  
CString m_strFileName;  
```  
  
## <a name="see-also"></a>请参阅  
 [CException 类](../../mfc/reference/cexception-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CArchive 类](../../mfc/reference/carchive-class.md)   
 [AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)   
 [异常处理](../../mfc/reference/exception-processing.md)

