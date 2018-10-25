---
title: CDataSource 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
- GetProperties
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f5f6224b86d7df7af223c441361832984ff6a85c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50058669"
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
|[打开](#open)|创建一个与提供程序 （数据源） 的连接，使用`CLSID`， `ProgID`，或`CEnumerator`调用方提供的名字对象。|
|[OpenFromFileName](#openfromfilename)|从由用户提供的文件名指定的文件打开数据源。|
|[OpenFromInitializationString](#openfrominitializationstring)|打开由初始化字符串指定的数据源。|
|[OpenWithPromptFileName](#openwithpromptfilename)|允许用户选择之前创建的数据链接文件来打开对应的数据源。|
|[OpenWithServiceComponents](#openwithservicecomponents)|使用“数据链接”对话框打开数据源对象。|

## <a name="remarks"></a>备注

可以为单个连接创建一个或多个数据库会话。 这些会话由 `CSession` 表示。 必须调用[cdatasource:: Open](../../data/oledb/cdatasource-open.md)以打开之前创建的会话连接`CSession::Open`。

有关如何使用的示例`CDataSource`，请参阅[CatDB](../../visual-cpp-samples.md)示例。

## <a name="close"></a> Cdatasource:: Close

通过释放关闭的连接`m_spInit`指针。

### <a name="syntax"></a>语法

```cpp
void Close() throw();
```

## <a name="getinitializationstring"></a> Cdatasource:: Getinitializationstring

检索当前处于打开状态的数据源初始化字符串。

### <a name="syntax"></a>语法

```cpp
HRESULT GetInitializationString(BSTR* pInitializationString, 
   bool bIncludePassword = false) throw();
```

#### <a name="parameters"></a>参数

*pInitializationString*<br/>
[out]指向在初始化字符串的指针。

*bIncludePassword*<br/>
[in]**，则返回 true**如果字符串包含密码; 否则为**false**。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

生成的初始化字符串可用于以后重新打开此数据源连接。

## <a name="getproperties"></a> Cdatasource:: Getproperties

返回所需的连接的数据源对象的属性信息。

### <a name="syntax"></a>语法

```cpp
HRESULT GetProperties(ULONG ulPropIDSets, 
   constDBPROPIDSET* pPropIDSet, 
   ULONG* pulPropertySets, 
   DBPROPSET** ppPropsets) const throw();
```

#### <a name="parameters"></a>参数

请参阅[idbproperties:: Getproperties](/previous-versions/windows/desktop/ms714344)中*OLE DB 程序员参考*Windows SDK 中。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

若要获取的单个属性，请使用[GetProperty](../../data/oledb/cdatasource-getproperty.md)。

## <a name="getproperty"></a> Cdatasource:: Getproperty

返回连接的数据源对象的指定属性的值。

### <a name="syntax"></a>语法

```cpp
HRESULT GetProperty(const GUID& guid, 
   DBPROPID propid, 
   VARIANT* pVariant) const throw();
```

#### <a name="parameters"></a>参数

*guid*<br/>
[in]标识属性设置为其返回属性的 GUID。

*propid*<br/>
[in]属性 ID 的属性返回。

*pVariant*<br/>
[out]指针的变体其中`GetProperty`返回属性的值。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

若要获取多个属性，请使用[GetProperties](../../data/oledb/cdatasource-getproperties.md)。

## <a name="open"></a> Cdatasource:: Open

打开与数据源使用的连接`CLSID`， `ProgID`，或`CEnumerator`名字对象或通过一个定位器对话框提示用户。

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

#### <a name="parameters"></a>参数

*clsid*<br/>
[in]`CLSID`的数据提供程序。

*pPropSet*<br/>
[in]指向数组的指针[DBPROPSET](/previous-versions/windows/desktop/ms714367)结构包含要设置属性和值。 请参阅[属性设置和属性组](/previous-versions/windows/desktop/ms713696)中*OLE DB 程序员参考*Windows SDK 中。

*nPropertySets*<br/>
[in]数[DBPROPSET](/previous-versions/windows/desktop/ms714367)结构传入*pPropSet*参数。

*pName*<br/>
[in] 要连接的数据库的名称。

*pUserName*<br/>
[in] 用户的名称。

*pPassword*<br/>
[in] 用户的密码。

*nInitMode*<br/>
[in] 数据库初始化模式。 请参阅[初始化属性](/previous-versions/windows/desktop/ms723127)中*OLE DB 程序员参考*Windows SDK for 有效初始化模式的列表中。 如果*nInitMode*是零个、 未初始化模式包含在用于打开连接的属性集。

*szProgID*<br/>
[in] 一个程序标识符。

*enumerator*<br/>
[in]一个[CEnumerator](../../data/oledb/cenumerator-class.md)对象，用于获取打开连接时未指定调用方的名字对象`CLSID`。

*hWnd*<br/>
[in] 将成为对话框父级的窗口的句柄。 使用使用的函数重载*hWnd*参数将自动调用服务组件; 有关详细信息，请参阅备注。

*dwPromptOptions*<br/>
[in] 确定要显示的定位器对话框的样式。 请参阅 Msdasc.h 了解可能的值。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

使用的方法重载*hWnd*参数使用 oledb32.dll 中的服务组件打开数据源对象; 此 DLL 包含服务组件功能，例如资源池、 自动的实现事务登记等。 有关详细信息，请参阅"OLE DB 服务"在 OLE DB 程序员参考中[ https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true)。

不使用的方法重载*hWnd*参数无需使用 oledb32.dll 中的服务组件打开数据源对象。 一个[CDataSource](../../data/oledb/cdatasource-class.md)使用这些函数重载打开的对象将不能使用任何服务组件的功能。

### <a name="example"></a>示例

下面的代码演示如何使用 OLE DB 模板打开 Jet 4.0 数据源。 你将 Jet 数据源视为 OLE DB 数据源。 但是，在调用`Open`需要两个属性集： 一个用于 DBPROPSET_DBINIT，另一个用于 DBPROPSET_JETOLEDB_DBINIT，以便您可以设置 DBPROP_JETOLEDB_DATABASEPASSWORD。

[!code-cpp[NVC_OLEDB_Consumer#7](../../data/oledb/codesnippet/cpp/cdatasource-open_1.cpp)]

## <a name="openfromfilename"></a> Cdatasource:: Openfromfilename

从由用户提供的文件名指定的文件打开数据源。

### <a name="syntax"></a>语法

```cpp
HRESULT OpenFromFileName(LPCOLESTR szFileName) throw();
```

#### <a name="parameters"></a>参数

*szFileName*<br/>
[in] 文件的名称，通常是数据源连接 (.UDL) 文件。

有关数据链接文件 （.udl 文件） 的详细信息，请参阅[数据链接 API 概述](/previous-versions/windows/desktop/ms718102)Windows SDK 中。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

此方法使用 oledb32.dll 中的服务组件打开数据源对象；此 DLL 包含资源池、自动事务登记等服务组件功能的实现。 有关详细信息，请参阅"OLE DB 服务"在 OLE DB 程序员参考中[ https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true)。

## <a name="openfrominitializationstring"></a> Cdatasource:: Openfrominitializationstring

打开由用户提供初始化字符串指定数据源。

### <a name="syntax"></a>语法

```cpp
HRESULT OpenFromInitializationString(LPCOLESTR szInitializationString, 
   bool fPromptForInfo= false) throw();
```

#### <a name="parameters"></a>参数

*szInitializationString*<br/>
[in]初始化字符串中。

*fPromptForInfo*<br/>
[in]如果此参数设置为 **，则返回 true**，然后`OpenFromInitializationString`将将 DBPROP_INIT_PROMPT 属性设置为 DBPROMPT_COMPLETEREQUIRED，指定仅在需要时的详细信息的情况下提示用户。 这对于在其中初始化字符串指定的数据库，要求使用密码的情况下很有用，但该字符串不包含密码。 将提示用户输入密码 （或其他任何缺少的信息） 时尝试连接到数据库。

默认值是**false**，其中指定用户不会提示 （将设置为 DBPROMPT_NOPROMPT DBPROP_INIT_PROMPT）。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

此方法使用 oledb32.dll 中的服务组件打开数据源对象；此 DLL 包含资源池、自动事务登记等服务组件功能的实现。

## <a name="openwithpromptfilename"></a> Cdatasource:: Openwithpromptfilename

此方法通过对话框提示用户，然后使用由用户指定的文件打开数据源。

### <a name="syntax"></a>语法

```cpp
HRESULT OpenWithPromptFileName(HWND hWnd = GetActiveWindow(   ), 
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_NONE, 
   LPCOLESTR szInitialDirectory = NULL) throw();
```

#### <a name="parameters"></a>参数

*hWnd*<br/>
[in] 将成为对话框父级的窗口的句柄。

*dwPromptOptions*<br/>
[in] 确定要显示的定位器对话框的样式。 请参阅 Msdasc.h 了解可能的值。

*szInitialDirectory*<br/>
[in] 要在定位器对话框中显示的初始目录。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

此方法使用 oledb32.dll 中的服务组件打开数据源对象；此 DLL 包含资源池、自动事务登记等服务组件功能的实现。 有关详细信息，请参阅"OLE DB 服务"在 OLE DB 程序员参考中[ https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true)。

## <a name="openwithservicecomponents"></a> Cdatasource:: Openwithservicecomponents

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

#### <a name="parameters"></a>参数

*clsid*<br/>
[in]`CLSID`数据提供程序。

*szProgID*<br/>
[in] 数据提供程序的程序 ID。

*pPropset*<br/>
[in]指向数组的指针[DBPROPSET](/previous-versions/windows/desktop/ms714367)结构包含要设置属性和值。 请参阅[属性设置和属性组](/previous-versions/windows/desktop/ms713696)中*OLE DB 程序员参考*Windows SDK 中。 如果数据源对象进行初始化，则属性必须属于数据源属性组。 如果相同的属性中指定了不止一次*pPropset*，则使用的值是特定于提供程序。 如果*ulPropSets*为零，则忽略此参数。

*ulPropSets*<br/>
[in]数[DBPROPSET](/previous-versions/windows/desktop/ms714367)结构传入*pPropSet*参数。 如果这是零，该提供程序将忽略*pPropset*。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

此方法使用 oledb32.dll 中的服务组件打开数据源对象；此 DLL 包含资源池、自动事务登记等服务组件功能的实现。 有关详细信息，请参阅"OLE DB 服务"在 OLE DB 程序员参考中[ https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true)。

## <a name="see-also"></a>请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)