---
title: CArchiveException 类 |Microsoft Docs
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
ms.openlocfilehash: 53e82838ba952656d7067ce2294d9abdde11479c
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37335739"
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
|[CArchiveException::m_cause](#m_cause)|指示异常原因。|  
|[CArchiveException::m_strFileName](#m_strfilename)|指定此异常条件的文件的名称。|  
  
## <a name="remarks"></a>备注  
 `CArchiveException`类包括指示异常原因的公共数据成员。  
  
 `CArchiveException` 对象构造和内部发生[CArchive](../../mfc/reference/carchive-class.md)成员函数。 您可以访问这些对象的作用域内**捕获**表达式。 原因代码是独立于操作系统。 有关异常处理的详细信息，请参阅[异常处理 (MFC)](../../mfc/exception-handling-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CArchiveException`  
  
## <a name="requirements"></a>要求  
 **标头：** afx.h  
  
##  <a name="carchiveexception"></a>  CArchiveException::CArchiveException  
 构造`CArchiveException`对象，如果将值*导致*对象中。  
  
```  
CArchiveException(
    int cause = CArchiveException::none,  
    LPCTSTR lpszArchiveName = NULL);
```  
  
### <a name="parameters"></a>参数  
 *原因*  
 指示异常原因的枚举的类型变量。 枚举器的列表，请参阅[m_cause](#m_cause)数据成员。  
  
 *lpszArchiveName*  
 指向包含名称的字符串`CArchive`导致发生异常的对象。  
  
### <a name="remarks"></a>备注  
 您可以创建`CArchiveException`堆上对象和自行引发或让全局函数[AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)为你处理。  
  
 直接调用不使用此构造函数相反，调用全局函数`AfxThrowArchiveException`。  
  
##  <a name="m_cause"></a>  CArchiveException::m_cause  
 指定异常的原因。  
  
```  
int m_cause;  
```  
  
### <a name="remarks"></a>备注  
 此数据成员是类型的公共变量**int**。通过定义其值`CArchiveException`枚举类型。 枚举器及其含义如下所示：  
  
- `CArchiveException::none` 未发生错误。  
  
- `CArchiveException::genericException` 未指定的错误。  
  
- `CArchiveException::readOnly` 尝试写入到适用于加载的打开的存档。  
  
- `CArchiveException::endOfFile` 读取对象时达到的文件尾。  
  
- `CArchiveException::writeOnly` 尝试从存档存储可供读取。  
  
- `CArchiveException::badIndex` 无效的文件格式。  
  
- `CArchiveException::badClass` 尝试读取某个对象转换为对象类型不正确。  
  
- `CArchiveException::badSchema` 尝试读取具有不同版本的类的对象。  
  
    > [!NOTE]
    >  引发这些 `CArchiveException` 的枚举器不同于引发 `CFileException` 的枚举器。  
  
    > [!NOTE]
    > `CArchiveException::generic` 已弃用。 请改用 `genericException`。 如果**泛型**是应用程序中使用和构建使用 /clr，将不容易解密的语法错误。  
  
##  <a name="m_strfilename"></a>  CArchiveException::m_strFileName  
 指定此异常条件的文件的名称。  
  
```  
CString m_strFileName;  
```  
  
## <a name="see-also"></a>请参阅  
 [CException 类](../../mfc/reference/cexception-class.md)   
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [CArchive 类](../../mfc/reference/carchive-class.md)   
 [AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)   
 [异常处理](../../mfc/reference/exception-processing.md)

