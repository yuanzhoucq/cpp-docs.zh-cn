---
title: CDaoException 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoException
- AFXDAO/CDaoException
- AFXDAO/CDaoException::CDaoException
- AFXDAO/CDaoException::GetErrorCount
- AFXDAO/CDaoException::GetErrorInfo
- AFXDAO/CDaoException::m_nAfxDaoError
- AFXDAO/CDaoException::m_pErrorInfo
- AFXDAO/CDaoException::m_scode
dev_langs:
- C++
helpviewer_keywords:
- CDaoException [MFC], CDaoException
- CDaoException [MFC], GetErrorCount
- CDaoException [MFC], GetErrorInfo
- CDaoException [MFC], m_nAfxDaoError
- CDaoException [MFC], m_pErrorInfo
- CDaoException [MFC], m_scode
ms.assetid: b2b01fa9-7ce2-42a1-842e-40f13dc50da4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4531d63ff7047881f20368cbeaf8e5de4136bb9f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369211"
---
# <a name="cdaoexception-class"></a>CDaoException 类
表示由基于数据访问对象 (DAO) 的 MFC 数据库类引起的异常条件。  
  
## <a name="syntax"></a>语法  
  
```  
class CDaoException : public CException  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CDaoException::CDaoException](#cdaoexception)|构造 `CDaoException` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDaoException::GetErrorCount](#geterrorcount)|数据库引擎错误集合中返回错误的数。|  
|[CDaoException::GetErrorInfo](#geterrorinfo)|错误集合中返回有关特定错误对象的错误信息。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CDaoException::m_nAfxDaoError](#m_nafxdaoerror)|包含在 MFC DAO 类中的任何错误的扩展的错误代码。|  
|[CDaoException::m_pErrorInfo](#m_perrorinfo)|指向的指针[CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md)对象，其中包含有关一个 DAO 错误对象信息。|  
|[CDaoException::m_scode](#m_scode)|[SCODE](#m_scode)与错误关联的值。|  
  
## <a name="remarks"></a>备注  
 该类包括可用于确定异常的原因的公共数据成员。 `CDaoException` 对象为构造，并且由 DAO 数据库类的成员函数引发。  
  
> [!NOTE]
>  DAO 数据库类有别于基于开放式数据库连接 (ODBC) 的 MFC 数据库类。 DAO 数据库类的所有名称都具有"CDao"前缀。 你仍可以访问 ODBC 数据源对于 DAO 类。 通常情况下，基于 DAO 的 MFC 类是更强于基于 ODBC; 的 MFC 类基于 DAO 的类可以访问数据，包括通过 ODBC 驱动程序，通过其自己的数据库引擎。 基于 DAO 的类还支持数据定义语言 (DDL) 操作，如添加表通过类，而无需直接调用 DAO。 ODBC 类引发的异常的信息，请参阅[CDBException](../../mfc/reference/cdbexception-class.md)。  
  
 你可以访问的作用域内的异常对象[捕获](../../mfc/reference/exception-processing.md#catch)表达式。 你可以引发`CDaoException`对象从你自己的代码与[AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception)全局函数。  
  
 在 MFC 中，所有 DAO 错误都表示为类型的异常`CDaoException`。 当你捕获此类型的异常时，你可以使用`CDaoException`成员函数以从存储在数据库引擎错误集合中任何 DAO error 对象中检索信息。 每个错误发生时，一个或多个错误对象都将置于错误集合。 （通常集合只包含一个错误对象; 如果使用 ODBC 数据源，你很有可能，若要获取多个错误对象。）当另一个 DAO 操作生成错误时，错误集合处于未选中状态，并将新的错误对象置于错误集合。 不生成错误的 DAO 操作设置不会影响错误集合。  
  
 DAO 错误代码，请参阅 DAOERR 的文件。H。 有关相关信息，请参阅主题"可捕获中的数据访问错误"DAO 帮助。  
  
 有关常规，或有关中的异常处理的详细信息`CDaoException`对象，请参阅文章[异常处理 (MFC)](../../mfc/exception-handling-in-mfc.md)和[异常： 数据库异常](../../mfc/exceptions-database-exceptions.md)。 第二篇文章包含阐释了在 DAO 中的异常处理的代码示例。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CDaoException`  
  
## <a name="requirements"></a>要求  
 **标头：** afxdao.h  
  
##  <a name="cdaoexception"></a>  CDaoException::CDaoException  
 构造 `CDaoException` 对象。  
  
```  
CDaoException();
```  
  
### <a name="remarks"></a>备注  
 通常，框架创建异常对象，其代码引发异常时。 很少需要显式构造异常对象。 如果你想要引发`CDaoException`从你自己的代码，调用全局函数[AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception)。  
  
 但是，你可能想要显式创建异常对象，如果要进行直接调用 DAO MFC 类封装的 DAO 接口指针通过。 在这种情况下，你可能需要从 DAO 检索错误信息。 假设通过工作区中的数据库集合的 DAODatabases 接口调用 DAO 方法时，在 DAO 中发生错误。  
  
##### <a name="to-retrieve-the-dao-error-information"></a>若要检索的 DAO 错误信息  
  
1.  构造`CDaoException`对象。  
  
2.  调用异常对象的[GetErrorCount](#geterrorcount)成员函数来确定数据库引擎错误集合中的错误对象数。 (通常只有一个，除非你使用 ODBC 数据源。)  
  
3.  调用异常对象的[GetErrorInfo](#geterrorinfo)成员函数来检索一次的一个特定的错误对象，通过在集合中，通过异常对象的索引。 将异常对象视为一个 DAO 错误对象的代理。  
  
4.  检查当前[CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md)结构的`GetErrorInfo`中返回[m_pErrorInfo](#m_perrorinfo)数据成员。 其成员提供有关 DAO 错误的信息。  
  
5.  对于 ODBC 数据源，请重复步骤 3 和 4 根据需要为多个错误对象。  
  
6.  如果你构造堆上的异常对象，将其与删除**删除**运算符时完成。  
  
 有关在 MFC DAO 类中处理错误的详细信息，请参阅文章[异常： 数据库异常](../../mfc/exceptions-database-exceptions.md)。  
  
##  <a name="geterrorcount"></a>  CDaoException::GetErrorCount  
 调用此成员函数可检索的 DAO 数据库引擎错误集合中的错误对象数。  
  
```  
short GetErrorCount();
```  
  
### <a name="return-value"></a>返回值  
 DAO 数据库引擎错误集合中的错误对象数。  
  
### <a name="remarks"></a>备注  
 此信息可用于循环访问要检索每个集合中的一个或多个的 DAO 错误对象的错误集合。 若要按索引或 DAO 错误号，请检索对象时出错，调用[GetErrorInfo](#geterrorinfo)成员函数。  
  
> [!NOTE]
>  通常错误集合中没有只有一个对象时出错。 如果你正在使用 ODBC 数据源，但是，可能有多个。  
  
##  <a name="geterrorinfo"></a>  CDaoException::GetErrorInfo  
 错误集合中返回有关特定错误对象的错误信息。  
  
```  
void GetErrorInfo(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 数据库引擎错误集合，按索引查找中的错误信息的索引。  
  
### <a name="remarks"></a>备注  
 调用此成员函数可获取以下类型的有关异常的信息：  
  
-   错误代码  
  
-   源  
  
-   描述  
  
-   帮助文件  
  
-   帮助上下文  
  
 `GetErrorInfo` 将信息存储在异常对象的`m_pErrorInfo`数据成员。 返回的信息的简要说明，请参阅[m_pErrorInfo](#m_perrorinfo)。 如果你捕获类型的异常`CDaoException`由 MFC，引发`m_pErrorInfo`成员，将已填写。 如果你选择直接调用 DAO，则必须调用异常对象的`GetErrorInfo`成员函数自己以填充`m_pErrorInfo`。 有关更多详细说明，请参阅[CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md)结构。  
  
 DAO 异常和示例代码有关的信息，请参阅文章[异常： 数据库异常](../../mfc/exceptions-database-exceptions.md)。  
  
##  <a name="m_nafxdaoerror"></a>  CDaoException::m_nAfxDaoError  
 包含 MFC 扩展错误代码。  
  
### <a name="remarks"></a>备注  
 此代码在其中会 MFC DAO 类的特定组件有误的情况下提供。  
  
 可能的值有：  
  
- **NO_AFX_DAO_ERROR**最新的操作未导致 MFC 扩展错误。 但是，该操作可能已产生其他错误从 DAO 或 OLE，因此你应该检查[m_pErrorInfo](#m_perrorinfo) ，还可能[m_scode](#m_scode)。  
  
- **AFX_DAO_ERROR_ENGINE_INITIALIZATION** MFC 无法初始化 Microsoft Jet 数据库引擎。 OLE 可能无法初始化，或者它可能无法创建 DAO 数据库引擎对象的实例。 这些问题通常建议 DAO 或 OLE 的错误安装。  
  
- **AFX_DAO_ERROR_DFX_BIND** DAO 记录字段交换 (DFX) 函数调用中使用的地址不存在或无效 （地址未用于将数据绑定）。 你可能在 DFX 调用传递错误地址或地址可能已变得无效 DFX 操作之间。  
  
- **AFX_DAO_ERROR_OBJECT_NOT_OPEN**尝试打开基于 querydef 或 tabledef 对象未处于打开状态的记录集。  
  
##  <a name="m_perrorinfo"></a>  CDaoException::m_pErrorInfo  
 包含指向的`CDaoErrorInfo`提供了有关上次检索通过调用 DAO 错误对象信息的结构[GetErrorInfo](#geterrorinfo)。  
  
### <a name="remarks"></a>备注  
 此对象包含以下信息：  
  
|CDaoErrorInfo 成员|信息|含义|  
|--------------------------|-----------------|-------------|  
|**m_lErrorCode**|错误代码|DAO 错误代码|  
|`m_strSource`|源|最初生成错误的应用程序的对象的名称|  
|`m_strDescription`|描述|与错误关联的描述性字符串|  
|`m_strHelpFile`|帮助文件|用户可以在其中获取有关问题的信息 Windows 帮助的文件的路径|  
|**m_lHelpContext**|帮助上下文|DAO 帮助文件中主题的上下文 ID|  
  
 有关完整详细信息中包含的信息`CDaoErrorInfo`对象，请参阅[CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md)结构。  
  
##  <a name="m_scode"></a>  CDaoException::m_scode  
 包含类型的值`SCODE`描述该错误。  
  
### <a name="remarks"></a>备注  
 这是 OLE 代码。 你将很少需要使用此值，因为在几乎所有情况下，更具体的 MFC 或 DAO 错误信息均以另`CDaoException`数据成员。  
  
 璝惠`SCODE`，请参阅主题[OLE 错误代码的结构](http://msdn.microsoft.com/library/windows/desktop/ms690088)Windows SDK 中。 `SCODE`数据类型映射到`HRESULT`数据类型。  
  
## <a name="see-also"></a>请参阅  
 [CException 类](../../mfc/reference/cexception-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CException 类](../../mfc/reference/cexception-class.md)
