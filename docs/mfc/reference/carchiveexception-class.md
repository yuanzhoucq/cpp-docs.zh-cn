---
title: "CArchiveException 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CArchiveException
dev_langs:
- C++
helpviewer_keywords:
- exceptions [C++], serialization
- serialization [C++], exceptions
- CArchiveException class
- exceptions [C++], archive
- archive exceptions [C++]
ms.assetid: da31a127-e86c-41d1-b0b6-bed0865b1b49
caps.latest.revision: 21
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
ms.openlocfilehash: e927bea5b8d9e6dbaafb191f6c3bdcf0f0d076cc
ms.lasthandoff: 02/24/2017

---
# <a name="carchiveexception-class"></a>CArchiveException 类
表示序列化异常条件  
  
## <a name="syntax"></a>语法  
  
```  
class CArchiveException : public CException  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CArchiveException::CArchiveException](#carchiveexception)|构造 `CArchiveException` 对象。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CArchiveException::m_cause](#m_cause)|指示异常原因。|  
|[CArchiveException::m_strFileName](#m_strfilename)|指定此异常条件的文件的名称。|  
  
## <a name="remarks"></a>备注  
 `CArchiveException`类包括指示该异常的原因的公共数据成员。  
  
 `CArchiveException`对象构造，并引发内部[CArchive](../../mfc/reference/carchive-class.md)成员函数。 您可以访问这些对象的作用域内**捕获**表达式。 原因代码是独立于操作系统。 有关异常处理的详细信息，请参阅[异常处理 (MFC)](../../mfc/exception-handling-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CArchiveException`  
  
## <a name="requirements"></a>要求  
 **标头：** afx.h  
  
##  <a name="a-namecarchiveexceptiona--carchiveexceptioncarchiveexception"></a><a name="carchiveexception"></a>CArchiveException::CArchiveException  
 构造`CArchiveException`对象，如果将值`cause`对象中。  
  
```  
CArchiveException(
    int cause = CArchiveException::none,  
    LPCTSTR lpszArchiveName = NULL);
```  
  
### <a name="parameters"></a>参数  
 `cause`  
 一个枚举的类型变量，指示该异常的原因。 枚举器的列表，请参阅[m_cause](#m_cause)数据成员。  
  
 `lpszArchiveName`  
 指向包含名称的字符串`CArchive`导致此异常的对象。  
  
### <a name="remarks"></a>备注  
 您可以创建`CArchiveException`在堆上对象而引发它自己或让全局函数[AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)为你处理它。  
  
 直接调用不使用此构造函数相反，调用全局函数`AfxThrowArchiveException`。  
  
##  <a name="a-namemcausea--carchiveexceptionmcause"></a><a name="m_cause"></a>CArchiveException::m_cause  
 指定异常的原因。  
  
```  
int m_cause;  
```  
  
### <a name="remarks"></a>备注  
 此数据成员是类型 `int` 的公共变量。 其值由`CArchiveException`枚举类型。 枚举器及其含义如下所示：  
  
- **CArchiveException::none**未发生错误。  
  
- **CArchiveException::genericException**未指定的错误。  
  
- **CArchiveException::readOnly**尝试写入打开以进行加载的存档。  
  
- **CArchiveException::endOfFile**读取某个对象时已达到最终的文件。  
  
- **CArchiveException::writeOnly**尝试从用于存储打开的存档中读取。  
  
- **CArchiveException::badIndex**文件格式无效。  
  
- **CArchiveException::badClass**尝试读取某个对象转换为对象类型不正确。  
  
- **CArchiveException::badSchema**尝试读取具有不同版本的类的对象。  
  
    > [!NOTE]
    >  引发这些 `CArchiveException` 的枚举器不同于引发 `CFileException` 的枚举器。  
  
    > [!NOTE]
    > **CArchiveException::generic**已弃用。 使用**genericException**相反。 如果**泛型**并使用应用程序中生成使用 /clr 时，将不容易解密的语法错误。  
  
##  <a name="a-namemstrfilenamea--carchiveexceptionmstrfilename"></a><a name="m_strfilename"></a>CArchiveException::m_strFileName  
 指定此异常条件的文件的名称。  
  
```  
CString m_strFileName;  
```  
  
## <a name="see-also"></a>另请参阅  
 [CException 类](../../mfc/reference/cexception-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CArchive 类](../../mfc/reference/carchive-class.md)   
 [AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)   
 [异常处理](../../mfc/reference/exception-processing.md)


