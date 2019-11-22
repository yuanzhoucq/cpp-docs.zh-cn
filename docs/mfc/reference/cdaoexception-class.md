---
title: CDaoException 类
ms.date: 09/17/2019
f1_keywords:
- CDaoException
- AFXDAO/CDaoException
- AFXDAO/CDaoException::CDaoException
- AFXDAO/CDaoException::GetErrorCount
- AFXDAO/CDaoException::GetErrorInfo
- AFXDAO/CDaoException::m_nAfxDaoError
- AFXDAO/CDaoException::m_pErrorInfo
- AFXDAO/CDaoException::m_scode
helpviewer_keywords:
- CDaoException [MFC], CDaoException
- CDaoException [MFC], GetErrorCount
- CDaoException [MFC], GetErrorInfo
- CDaoException [MFC], m_nAfxDaoError
- CDaoException [MFC], m_pErrorInfo
- CDaoException [MFC], m_scode
ms.assetid: b2b01fa9-7ce2-42a1-842e-40f13dc50da4
ms.openlocfilehash: 92105bfb094f50f3077fcf2c1fc221c43015c4d2
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303834"
---
# <a name="cdaoexception-class"></a>CDaoException 类

表示由基于数据访问对象 (DAO) 的 MFC 数据库类引起的异常条件。 DAO 3.6 是最终版本，被视为已过时。

## <a name="syntax"></a>语法

```
class CDaoException : public CException
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CDaoException::CDaoException](#cdaoexception)|构造 `CDaoException` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CDaoException::GetErrorCount](#geterrorcount)|返回数据库引擎的错误集合中的错误数。|
|[CDaoException::GetErrorInfo](#geterrorinfo)|返回有关错误集合中特定错误对象的错误信息。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CDaoException::m_nAfxDaoError](#m_nafxdaoerror)|包含 MFC DAO 类中的任何错误的扩展错误代码。|
|[CDaoException::m_pErrorInfo](#m_perrorinfo)|指向[CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md)对象的指针，该对象包含一个 DAO 错误对象的相关信息。|
|[CDaoException::m_scode](#m_scode)|与错误关联的[SCODE](#m_scode)值。|

## <a name="remarks"></a>备注

类包含可用于确定异常原因的公共数据成员。 `CDaoException` 对象由 DAO 数据库类的成员函数构造和引发。

> [!NOTE]
>  DAO 数据库类与基于开放式数据库连接（ODBC）的 MFC 数据库类不同。 所有 DAO 数据库类名称都具有 "CDao" 前缀。 你仍可以使用 DAO 类访问 ODBC 数据源。 通常，基于 DAO 的 MFC 类比基于 ODBC 的 MFC 类更强大;基于 DAO 的类可以通过其自己的数据库引擎来访问数据，包括通过 ODBC 驱动程序。 基于 DAO 的类还支持数据定义语言（DDL）操作，例如通过类添加表，而无需直接调用 DAO。 有关 ODBC 类引发的异常的信息，请参阅[CDBException](../../mfc/reference/cdbexception-class.md)。

可以访问[CATCH](../../mfc/reference/exception-processing.md#catch)表达式范围内的异常对象。 还可以从自己的代码中引发 `CDaoException` 对象以及[AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception) global 函数。

在 MFC 中，所有 DAO 错误都表示为异常，类型为 `CDaoException`。 捕获此类型的异常时，可以使用 `CDaoException` 成员函数从数据库引擎错误集合中存储的任何 DAO 错误对象中检索信息。 发生每个错误时，将一个或多个错误对象放置在错误集合中。 （通常，该集合仅包含一个错误对象; 如果使用的是 ODBC 数据源，则更有可能获得多个错误对象。）当另一个 DAO 操作生成错误时，将清除错误集合，并将新的错误对象放置在错误集合中。 不生成错误的 DAO 操作不会影响 "错误" 集合。

有关 DAO 错误代码，请参阅文件 DAOERR。高. 有关相关信息，请参阅 DAO 帮助中的 "可捕获的数据访问错误" 主题。

有关常规处理的详细信息，或有关 `CDaoException` 对象的详细信息，请参阅文章[异常处理（MFC）](../../mfc/exception-handling-in-mfc.md)和[异常：数据库异常](../../mfc/exceptions-database-exceptions.md)。 第二篇文章包含的示例代码演示了 DAO 中的异常处理。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CDaoException`

## <a name="requirements"></a>要求

**标头：** afxdao.h

##  <a name="cdaoexception"></a>CDaoException::CDaoException

构造 `CDaoException` 对象。

```
CDaoException();
```

### <a name="remarks"></a>备注

通常，当框架的代码引发异常时，框架会创建异常对象。 很少需要显式构造异常对象。 如果要从自己的代码中引发 `CDaoException`，请调用 global 函数[AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception)。

但是，如果您通过 MFC 类封装的 DAO 接口指针直接调用 DAO，则您可能希望显式创建异常对象。 在这种情况下，可能需要从 DAO 检索错误信息。 假设在通过 DAODatabases 接口通过工作区的数据库集合调用 DAO 方法时，DAO 中发生错误。

##### <a name="to-retrieve-the-dao-error-information"></a>检索 DAO 错误信息

1. 构造 `CDaoException` 对象。

1. 调用 exception 对象的[GetErrorCount](#geterrorcount)成员函数，以确定数据库引擎的错误集合中有多少个错误对象。 （通常只有一个，除非使用 ODBC 数据源。）

1. 调用异常对象的[GetErrorInfo](#geterrorinfo)成员函数，以便一次检索一个特定错误对象，并通过异常对象在集合中索引。 将异常对象视为一个 DAO 错误对象的代理。

1. 检查[m_pErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md)数据成员中`GetErrorInfo`返回的当前 [CDaoErrorInfo](#m_perrorinfo) 结构。 其成员提供有关 DAO 错误的信息。

1. 对于 ODBC 数据源，请根据需要重复步骤3和4，以获取更多的错误对象。

1. 如果在堆上构造了异常对象，请在完成时将其与**delete**运算符一起删除。

有关处理 MFC DAO 类中的错误的详细信息，请参阅文章[异常：数据库异常](../../mfc/exceptions-database-exceptions.md)。

##  <a name="geterrorcount"></a>CDaoException::GetErrorCount

调用此成员函数以检索数据库引擎错误集合中 DAO 错误对象的数目。

```
short GetErrorCount();
```

### <a name="return-value"></a>返回值

数据库引擎的错误集合中的 DAO 错误对象数。

### <a name="remarks"></a>备注

此信息可用于循环遍历 Errors 集合以检索集合中的一个或多个 DAO 错误对象。 若要按索引或 DAO 错误号检索错误对象，请调用[GetErrorInfo](#geterrorinfo)成员函数。

> [!NOTE]
>  通常，错误集合中只有一个错误对象。 但是，如果您使用的是 ODBC 数据源，则可以有多个。

##  <a name="geterrorinfo"></a>CDaoException：： GetErrorInfo

返回有关错误集合中特定错误对象的错误信息。

```
void GetErrorInfo(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
数据库引擎的错误集合中的错误信息索引，用于按索引查找。

### <a name="remarks"></a>备注

调用此成员函数以获取有关异常的以下类型的信息：

- 错误代码

- 源

- 描述

- 帮助文件

- 帮助上下文

`GetErrorInfo` 将信息存储在异常对象的 `m_pErrorInfo` 数据成员中。 有关所返回信息的简要说明，请参阅[m_pErrorInfo](#m_perrorinfo)。 如果捕获 MFC 引发 `CDaoException` 类型的异常，`m_pErrorInfo` 成员将已填充。 如果选择直接调用 DAO，则必须自行调用 exception 对象的 `GetErrorInfo` 成员函数来填充 `m_pErrorInfo`。 有关更详细的说明，请参阅[CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md)结构。

有关 DAO 异常和示例代码的信息，请参阅文章[异常：数据库异常](../../mfc/exceptions-database-exceptions.md)。

##  <a name="m_nafxdaoerror"></a>  CDaoException::m_nAfxDaoError

包含 MFC 扩展错误代码。

### <a name="remarks"></a>备注

当 MFC DAO 类的特定组件具有观点时，将提供此代码。

可能的值包括：

- NO_AFX_DAO_ERROR 最近的操作未导致 MFC 扩展错误。 但是，此操作可能会产生 DAO 或 OLE 中的其他错误，因此应检查[m_pErrorInfo](#m_perrorinfo) ，并可能[m_scode](#m_scode)。

- AFX_DAO_ERROR_ENGINE_INITIALIZATION MFC 无法初始化 Microsoft Jet 数据库引擎。 OLE 可能无法初始化，或者可能无法创建 DAO 数据库引擎对象的实例。 这些问题通常建议不正确安装 DAO 或 OLE。

- AFX_DAO_ERROR_DFX_BIND DAO 记录字段交换（DFX）函数调用中使用的地址不存在或无效（该地址未用于绑定数据）。 你可能在 DFX 调用中传递了错误的地址，或者该地址可能在 DFX 操作之间变为无效。

- AFX_DAO_ERROR_OBJECT_NOT_OPEN 尝试打开基于 querydef 或未处于打开状态的 tabledef 对象的记录集。

##  <a name="m_perrorinfo"></a>CDaoException：： m_pErrorInfo

包含一个指向 `CDaoErrorInfo` 结构的指针，该结构提供有关通过调用[GetErrorInfo](#geterrorinfo)最后检索的 DAO 错误对象的信息。

### <a name="remarks"></a>备注

此对象包含以下信息：

|CDaoErrorInfo 成员|信息|含义|
|--------------------------|-----------------|-------------|
|`m_lErrorCode`|错误代码|DAO 错误代码|
|`m_strSource`|源|最初生成错误的对象或应用程序的名称|
|`m_strDescription`|描述|与错误关联的描述性字符串|
|`m_strHelpFile`|帮助文件|Windows 帮助文件的路径，用户可以在其中获取有关问题的信息|
|`m_lHelpContext`|帮助上下文|DAO 帮助文件中的主题的上下文 ID|

有关 `CDaoErrorInfo` 对象中包含的信息的完整详细信息，请参阅[CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md)结构。

##  <a name="m_scode"></a>CDaoException：： m_scode

包含描述错误的类型 `SCODE` 的值。

### <a name="remarks"></a>备注

这是一个 OLE 代码。 您很少需要使用此值，因为在几乎所有情况下，其他 `CDaoException` 数据成员中提供了更具体的 MFC 或 DAO 错误信息。

有关 SCODE 的信息，请参阅 Windows SDK 中的[OLE 错误代码](/windows/win32/com/structure-of-com-error-codes)的主题结构。 SCODE 数据类型映射到 HRESULT 数据类型。

## <a name="see-also"></a>另请参阅

[CException 类](../../mfc/reference/cexception-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CException 类](../../mfc/reference/cexception-class.md)
