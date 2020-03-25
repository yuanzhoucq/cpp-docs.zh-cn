---
title: CDataSource 类
ms.date: 11/04/2016
f1_keywords:
- ATL.CDataSource
- ATL::CDataSource
- CDataSource
- ATL::CDataSource::Close
- ATL.CDataSource.Close
- CDataSource::Close
- CDataSource.Close
- ATL::CDataSource::GetInitializationString
- CDataSource.GetInitializationString
- GetInitializationString
- CDataSource::GetInitializationString
- ATL.CDataSource.GetInitializationString
- CDataSource::GetProperties
- ATL.CDataSource.GetProperties
- CDataSource.GetProperties
- ATL::CDataSource::GetProperties
- ATL::CDataSource::GetProperty
- ATL.CDataSource.GetProperty
- CDataSource.GetProperty
- CDataSource::GetProperty
- ATL::CDataSource::Open
- ATL.CDataSource.Open
- CDataSource::Open
- CDataSource.Open
- CDataSource::OpenFromFileName
- ATL::CDataSource::OpenFromFileName
- OpenFromFileName
- CDataSource.OpenFromFileName
- ATL.CDataSource.OpenFromFileName
- CDataSource.OpenFromInitializationString
- OpenFromInitializationString
- CDataSource::OpenFromInitializationString
- ATL::CDataSource::OpenFromInitializationString
- ATL.CDataSource.OpenFromInitializationString
- CDataSource.OpenWithPromptFileName
- OpenWithPromptFileName
- ATL::CDataSource::OpenWithPromptFileName
- ATL.CDataSource.OpenWithPromptFileName
- CDataSource::OpenWithPromptFileName
- CDataSource::OpenWithServiceComponents
- OpenWithServiceComponents
- CDataSource.OpenWithServiceComponents
helpviewer_keywords:
- CDataSource class
- Close method
- GetInitializationString method
- GetProperties method
- GetProperty method
- Open method
- OpenFromFileName method
- OpenFromInitializationString method
- OpenWithPromptFileName method
- OpenWithServiceComponents method
ms.assetid: 99bf862c-9d5c-4117-9501-aa0e2672085c
ms.openlocfilehash: 646d4b3548a1c5ee1bdfaf64f7823fa584abaac5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212002"
---
# <a name="cdatasource-class"></a>CDataSource 类

对应于一个 OLE DB 数据源对象，该对象表示通过提供程序建立的与数据源的连接。

## <a name="syntax"></a>语法

```cpp
class CDataSource
```

## <a name="requirements"></a>要求

**标头:** atldbcli.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[关闭](#close)|关闭连接。|
|[GetInitializationString](#getinitializationstring)|检索当前打开的数据源的初始化字符串。|
|[GetProperties](#getproperties)|获取当前为连接的数据源设置的属性的值。|
|[GetProperty](#getproperty)|获取当前为连接的数据源设置的单个属性的值。|
|[打开](#open)|使用调用方提供的 `CLSID`、`ProgID`或 `CEnumerator` 名字对象创建与提供程序（数据源）的连接。|
|[OpenFromFileName](#openfromfilename)|从由用户提供的文件名指定的文件打开数据源。|
|[OpenFromInitializationString](#openfrominitializationstring)|打开由初始化字符串指定的数据源。|
|[OpenWithPromptFileName](#openwithpromptfilename)|允许用户选择之前创建的数据链接文件来打开对应的数据源。|
|[OpenWithServiceComponents](#openwithservicecomponents)|使用“数据链接”对话框打开数据源对象。|

## <a name="remarks"></a>备注

可以为单个连接创建一个或多个数据库会话。 这些会话由 `CSession` 表示。 在使用 `CSession::Open`创建会话之前，必须先调用[CDataSource：： open](../../data/oledb/cdatasource-open.md)以便打开连接。

有关如何使用 `CDataSource`的示例，请参阅[CatDB](../../overview/visual-cpp-samples.md)示例。

## <a name="cdatasourceclose"></a><a name="close"></a>CDataSource：： Close

通过释放 `m_spInit` 指针关闭连接。

### <a name="syntax"></a>语法

```cpp
void Close() throw();
```

## <a name="cdatasourcegetinitializationstring"></a><a name="getinitializationstring"></a>CDataSource：： GetInitializationString

检索当前打开的数据源的初始化字符串。

### <a name="syntax"></a>语法

```cpp
HRESULT GetInitializationString(BSTR* pInitializationString,
   bool bIncludePassword = false) throw();
```

#### <a name="parameters"></a>parameters

*pInitializationString*<br/>
弄指向初始化字符串的指针。

*bIncludePassword*<br/>
中如果字符串包含密码，则为**true** ;否则**为 false**。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

生成的初始化字符串可用于稍后重新打开此数据源连接。

## <a name="cdatasourcegetproperties"></a><a name="getproperties"></a>CDataSource：： GetProperties

返回为连接的数据源对象请求的属性信息。

### <a name="syntax"></a>语法

```cpp
HRESULT GetProperties(ULONG ulPropIDSets,
   constDBPROPIDSET* pPropIDSet,
   ULONG* pulPropertySets,
   DBPROPSET** ppPropsets) const throw();
```

#### <a name="parameters"></a>parameters

请参阅 Windows SDK 中*OLE DB 程序员参考*中的[IDBProperties：： GetProperties](/previous-versions/windows/desktop/ms714344(v=vs.85)) 。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

若要获取单个属性，请使用[GetProperty](../../data/oledb/cdatasource-getproperty.md)。

## <a name="cdatasourcegetproperty"></a><a name="getproperty"></a>CDataSource：： GetProperty

返回连接的数据源对象的指定属性的值。

### <a name="syntax"></a>语法

```cpp
HRESULT GetProperty(const GUID& guid,
   DBPROPID propid,
   VARIANT* pVariant) const throw();
```

#### <a name="parameters"></a>parameters

*guid*<br/>
中一个 GUID，用于标识要为其返回属性的属性集。

*propid*<br/>
中要返回的属性的属性 ID。

*pVariant*<br/>
弄指向变量的指针，其中 `GetProperty` 返回属性的值。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

若要获取多个属性，请使用[GetProperties](../../data/oledb/cdatasource-getproperties.md)。

## <a name="cdatasourceopen"></a><a name="open"></a>CDataSource：： Open

使用 `CLSID`、`ProgID`或 `CEnumerator` 名字对象打开与数据源的连接，或者使用定位符对话框提示用户。

### <a name="syntax"></a>语法

```cpp
HRESULT Open(const CLSID& clsid,
   DBPROPSET* pPropSet = NULL,
   ULONG nPropertySets = 1) throw();

HRESULT Open(const CLSID& clsid,
   LPCTSTR pName,
   LPCTSTR pUserName = NULL,
   LPCTSTR pPassword = NULL,
   long nInitMode = 0) throw();HRESULT Open(LPCTSTR szProgID,
   DBPROPSET* pPropSet = NULL,
   ULONG nPropertySets = 1) throw();HRESULT Open(LPCTSTR szProgID,
   LPCTSTR pName,  LPCTSTR pUserName = NULL,
   LPCTSTR pPassword = NULL,
   long nInitMode = 0) throw();

HRESULT Open(const CEnumerator& enumerator,
   DBPROPSET* pPropSet = NULL,
   ULONG nPropertySets = 1) throw();

HRESULT Open(const CEnumerator& enumerator,
   LPCTSTR pName,
   LPCTSTR pUserName = NULL,
   LPCTSTR pPassword = NULL,
   long nInitMode = 0) throw();

HRESULT Open(HWND hWnd = GetActiveWindow(),
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_WIZARDSHEET) throw();

HRESULT Open(LPCWSTR szProgID,
   DBPROPSET* pPropSet = NULL,
   ULONG nPropertySets = 1) throw();

HRESULT Open(LPCSTR szProgID,
   LPCTSTR pName,LPCTSTR pUserName = NULL,
   LPCTSTR pPassword = NULL,
   long nInitMode = 0) throw();
```

#### <a name="parameters"></a>parameters

*clsid*<br/>
中数据访问接口的 `CLSID`。

*传入 ppropset*<br/>
中指向包含要设置的属性和值的[DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))结构的数组的指针。 请参阅 Windows SDK 中*OLE DB 程序员参考*中的[属性集和属性组](/previous-versions/windows/desktop/ms713696(v=vs.85))。

*nPropertySets*<br/>
中在*传入 ppropset*参数中传递的[DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))结构的数目。

*pName*<br/>
[in] 要连接的数据库的名称。

*pUserName*<br/>
[in] 用户的名称。

*pPassword*<br/>
[in] 用户的密码。

*nInitMode*<br/>
[in] 数据库初始化模式。 有关有效初始化模式的列表，请参阅 Windows SDK 中*OLE DB 程序员参考*中的[初始化属性](/previous-versions/windows/desktop/ms723127(v=vs.85))。 如果*nInitMode*为零，则不会在用于打开连接的属性集中包含初始化模式。

*szProgID*<br/>
[in] 一个程序标识符。

*enumerator*<br/>
中一个[CEnumerator](../../data/oledb/cenumerator-class.md)对象，用于在调用方未指定 `CLSID`时获取用于打开连接的名字对象。

*hWnd*<br/>
[in] 将成为对话框父级的窗口的句柄。 使用使用*hWnd*参数的函数重载将自动调用服务组件;有关详细信息，请参阅备注。

*dwPromptOptions*<br/>
[in] 确定要显示的定位器对话框的样式。 请参阅 Msdasc.h 了解可能的值。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

使用*hWnd*参数的方法重载将使用 oledb32.dll 中的服务组件打开数据源对象;此 DLL 包含服务组件功能（如资源池、自动事务登记等）的实现。 有关详细信息，请参阅[OLE DB 程序员指南](/previous-versions/windows/desktop/ms713643(v=vs.85))中的 OLE DB 参考。

不使用*hWnd*参数的方法重载打开数据源对象，而不使用 oledb32.dll 中的服务组件。 使用这些函数重载打开的[CDataSource](../../data/oledb/cdatasource-class.md)对象将无法利用服务组件的任何功能。

### <a name="example"></a>示例

下面的代码演示如何使用 OLE DB 模板打开 Jet 4.0 数据源。 你将 Jet 数据源视为 OLE DB 数据源。 但是，对 `Open` 的调用需要两个属性集：一个用于 DBPROPSET_DBINIT，另一个用于 DBPROPSET_JETOLEDB_DBINIT，因此可以设置 DBPROP_JETOLEDB_DATABASEPASSWORD。

[!code-cpp[NVC_OLEDB_Consumer#7](../../data/oledb/codesnippet/cpp/cdatasource-open_1.cpp)]

## <a name="cdatasourceopenfromfilename"></a><a name="openfromfilename"></a>CDataSource：： OpenFromFileName

从由用户提供的文件名指定的文件打开数据源。

### <a name="syntax"></a>语法

```cpp
HRESULT OpenFromFileName(LPCOLESTR szFileName) throw();
```

#### <a name="parameters"></a>parameters

*szFileName*<br/>
[in] 文件的名称，通常是数据源连接 (.UDL) 文件。

有关数据链接文件（.udl 文件）的详细信息，请参阅 Windows SDK 中的[数据链接 API 概述](/previous-versions/windows/desktop/ms718102(v=vs.85))。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

此方法使用 oledb32.dll 中的服务组件打开数据源对象；此 DLL 包含资源池、自动事务登记等服务组件功能的实现。 有关详细信息，请参阅[OLE DB 程序员指南](/previous-versions/windows/desktop/ms713643(v=vs.85))中的 OLE DB 参考。

## <a name="cdatasourceopenfrominitializationstring"></a><a name="openfrominitializationstring"></a>CDataSource：： OpenFromInitializationString

打开由用户提供的初始化字符串指定的数据源。

### <a name="syntax"></a>语法

```cpp
HRESULT OpenFromInitializationString(LPCOLESTR szInitializationString,
   bool fPromptForInfo= false) throw();
```

#### <a name="parameters"></a>parameters

*szInitializationString*<br/>
中初始化字符串。

*fPromptForInfo*<br/>
中如果此参数设置为**true**，则 `OpenFromInitializationString` 会将 DBPROP_INIT_PROMPT 属性设置为 DBPROMPT_COMPLETEREQUIRED，这将指定仅当需要更多信息时才提示用户。 这对于以下情况非常有用：初始化字符串指定了需要密码的数据库，但该字符串不包含密码。 尝试连接到数据库时，系统将提示用户输入密码（或任何其他缺少的信息）。

默认值为**false**，指定不提示用户（将 DBPROP_INIT_PROMPT 设置为 DBPROMPT_NOPROMPT）。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

此方法使用 oledb32.dll 中的服务组件打开数据源对象；此 DLL 包含资源池、自动事务登记等服务组件功能的实现。

## <a name="cdatasourceopenwithpromptfilename"></a><a name="openwithpromptfilename"></a>CDataSource：： OpenWithPromptFileName

此方法通过对话框提示用户，然后使用由用户指定的文件打开数据源。

### <a name="syntax"></a>语法

```cpp
HRESULT OpenWithPromptFileName(HWND hWnd = GetActiveWindow(   ),
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_NONE,
   LPCOLESTR szInitialDirectory = NULL) throw();
```

#### <a name="parameters"></a>parameters

*hWnd*<br/>
[in] 将成为对话框父级的窗口的句柄。

*dwPromptOptions*<br/>
[in] 确定要显示的定位器对话框的样式。 请参阅 Msdasc.h 了解可能的值。

*szInitialDirectory*<br/>
[in] 要在定位器对话框中显示的初始目录。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

此方法使用 oledb32.dll 中的服务组件打开数据源对象；此 DLL 包含资源池、自动事务登记等服务组件功能的实现。 有关详细信息，请参阅[OLE DB 程序员指南](/previous-versions/windows/desktop/ms713643(v=vs.85))中的 OLE DB 参考。

## <a name="cdatasourceopenwithservicecomponents"></a><a name="openwithservicecomponents"></a>CDataSource：： OpenWithServiceComponents

使用 oledb32.dll 中的服务组件打开数据源对象。

### <a name="syntax"></a>语法

```cpp
HRESULT OpenWithServiceComponents (const CLSID clsid,
   DBPROPSET* pPropset = NULL,
   ULONG ulPropSets = 1);

HRESULT OpenWithServiceComponents (LPCSTR szProgID,
   DBPROPSET* pPropset = NULL,
   ULONG ulPropSets = 1);
```

#### <a name="parameters"></a>parameters

*clsid*<br/>
中数据访问接口的 `CLSID`。

*szProgID*<br/>
[in] 数据提供程序的程序 ID。

*传入 ppropset*<br/>
中指向包含要设置的属性和值的[DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))结构的数组的指针。 请参阅 Windows SDK 中*OLE DB 程序员参考*中的[属性集和属性组](/previous-versions/windows/desktop/ms713696(v=vs.85))。 如果数据源对象进行初始化，则属性必须属于数据源属性组。 如果在*传入 ppropset*中多次指定同一个属性，则使用哪个值是特定于提供程序的。 如果*ulPropSets*为零，则忽略此参数。

*ulPropSets*<br/>
中在*传入 ppropset*参数中传递的[DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))结构的数目。 如果此值为零，则提供程序将忽略*传入 ppropset*。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

此方法使用 oledb32.dll 中的服务组件打开数据源对象；此 DLL 包含资源池、自动事务登记等服务组件功能的实现。 有关详细信息，请参阅[OLE DB 程序员指南](/previous-versions/windows/desktop/ms713643(v=vs.85))中的 OLE DB 参考。

## <a name="see-also"></a>另请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)
