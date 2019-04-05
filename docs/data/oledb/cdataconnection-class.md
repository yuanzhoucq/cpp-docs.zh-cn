---
title: CDataConnection 类
ms.date: 03/27/2019
f1_keywords:
- ATL::CDataConnection
- ATL.CDataConnection
- CDataConnection
- CDataConnection.CDataConnection
- ATL.CDataConnection.CDataConnection
- CDataConnection::CDataConnection
- ATL::CDataConnection::CDataConnection
- CDataConnection.Copy
- ATL.CDataConnection.Copy
- ATL::CDataConnection::Copy
- CDataConnection::Copy
- CDataConnection.Open
- ATL.CDataConnection.Open
- CDataConnection::Open
- ATL::CDataConnection::Open
- CDataConnection.OpenNewSession
- ATL.CDataConnection.OpenNewSession
- ATL::CDataConnection::OpenNewSession
- OpenNewSession
- CDataConnection::OpenNewSession
- CDataConnection::operatorBOOL
- ATL::CDataConnection::operatorBOOL
- CDataConnection.operatorBOOL
- ATL.CDataConnection.operatorBOOL
- CDataConnection::operatorBOOL
- ATL::CDataConnection::operatorBOOL
- CDataConnection.operatorBOOL
- ATL.CDataConnection.operatorBOOL
- CDataSource&
- CDataConnection.operatorCDataSource&
- operatorCDataSource&
- CDataConnection::operatorCDataSource&
- CDataSource*
- CDataConnection::operatorCDataSource*
- CDataConnection.operatorCDataSource*
- operatorCDataSource*
- CSession&
- CDataConnection::operatorCSession&
- CDataConnection.operatorCSession&
- operatorCSession&
- CDataConnection.operatorCSession*
- CDataConnection::operatorCSession*
- operatorCSession*
- CSession*
helpviewer_keywords:
- CDataConnection class
- CDataConnection class, constructor
- Copy method
- Open method
- OpenNewSession method
- BOOL operator
- operator bool
- BOOL operator
- operator bool
- CDataSource& operator
- operator & (CDataSource)
- CDataSource* operator
- operator * (CDataSource)
- operator CSession&
- CSession& operator
- operator CSession*
- CSession* operator
ms.assetid: 77432d85-4e20-49ec-a0b0-142137828471
ms.openlocfilehash: 94c7025185a24b07d5968157d49c856d4359b33a
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59021626"
---
# <a name="cdataconnection-class"></a>CDataConnection 类

管理与数据源的连接。

## <a name="syntax"></a>语法

```cpp
class CDataConnection
```

## <a name="requirements"></a>要求

**标头:** atldbcli.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[CDataConnection](#cdataconnection)|构造函数。 实例化并初始化`CDataConnection`对象。|
|[复制](#copy)|创建现有数据连接的副本。|
|[打开](#open)|打开到将初始化字符串的数据源的连接。|
|[OpenNewSession](#opennewsession)|打开当前连接上的新会话。|

### <a name="operators"></a>运算符

|||
|-|-|
|[BOOL 运算符](#op_bool)|确定当前会话是否为打开。|
|[operator bool](#op_bool_ole)|确定当前会话是否为打开。|
|[CDataSource 运算符 （& a)](#op_cdata_amp)|返回对所包含的引用`CDataSource`对象。|
|[运算符 CDataSource *](#op_cdata_star)|返回指向包含的 `CDataSource` 对象的指针。|
|[运算符 CSession&](#op_csession_amp)|返回对所包含的引用`CSession`对象。|
|[运算符 CSession*](#op_csession_star)|返回指向包含的 `CSession` 对象的指针。|

## <a name="remarks"></a>备注

`CDataConnection` 是用于创建客户端，因为它封装必要的对象 （数据源和会话） 和一些操作，您需要连接到数据源时执行的操作的有用类

无需`CDataConnection`，则必须创建`CDataSource`对象，请调用其[OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md)方法，然后创建的实例[CSession](../../data/oledb/csession-class.md)对象，请调用其[打开](../../data/oledb/csession-open.md)方法，然后创建[CCommand](../../data/oledb/ccommand-class.md)对象，并调用其`Open`* 方法。

使用`CDataConnection`，只需创建连接对象，将其传递初始化字符串，然后使用该连接打开的命令。 如果打算反复使用与数据库的连接，则使连接保持打开状态，一个好办法和`CDataConnection`提供了方便地执行该操作。

> [!NOTE]
>  如果要创建需要处理多个会话的数据库应用程序，您需要使用[OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md)。

## <a name="cdataconnection"></a> Cdataconnection:: Cdataconnection

实例化并初始化`CDataConnection`对象。

### <a name="syntax"></a>语法

```cpp
CDataConnection();
CDataConnection(const CDataConnection &ds);
```

#### <a name="parameters"></a>参数

*ds*<br/>
[in]对现有数据连接的引用。

### <a name="remarks"></a>备注

第一个重写创建一个新`CDataConnection`对象使用默认设置。

第二个重写创建一个新`CDataConnection`设置等效于指定类型的数据连接对象的对象。

## <a name="copy"></a> CDataConnection::Copy

创建现有数据连接的副本。

### <a name="syntax"></a>语法

```cpp
CDataConnection& Copy(const CDataConnection & ds) throw();
```

#### <a name="parameters"></a>参数

*ds*<br/>
[in]对要复制的现有数据连接的引用。

## <a name="open"></a> Cdataconnection:: Open

打开到将初始化字符串的数据源的连接。

### <a name="syntax"></a>语法

```cpp
HRESULT Open(LPCOLESTR szInitString) throw();
```

#### <a name="parameters"></a>参数

*szInitString*<br/>
[in]数据源初始化字符串。

### <a name="return-value"></a>返回值

标准的 HRESULT。

## <a name="opennewsession"></a> CDataConnection::OpenNewSession

将打开一个新的会话使用当前连接对象的数据源。

### <a name="syntax"></a>语法

```cpp
HRESULT OpenNewSession(CSession & session) throw();
```

#### <a name="parameters"></a>参数

*会话*<br/>
[输入/输出]对新的会话对象的引用。

### <a name="remarks"></a>备注

在新的会话使用当前连接对象的包含的数据源对象作为其父级，并且可以访问所有与数据源相同的信息。

### <a name="return-value"></a>返回值

标准的 HRESULT。

## <a name="op_bool"></a> Cdataconnection:: Operator BOOL

确定当前会话是否为打开。

### <a name="syntax"></a>语法

```cpp
operator BOOL() throw();
```

### <a name="remarks"></a>备注

返回**BOOL** (MFC typedef) 值。 **TRUE**意味着当前会话处于打开状态;**FALSE**表示关闭当前会话。

## <a name="op_bool_ole"></a> Cdataconnection:: Operator bool (OLE DB)

确定当前会话是否为打开。

### <a name="syntax"></a>语法

```cpp
operator bool() throw();
```

### <a name="remarks"></a>备注

返回**bool** （c + + 数据类型） 值。 **true**意味着当前会话处于打开状态;**false**表示关闭当前会话。

## <a name="op_cdata_amp"></a> Cdataconnection:: Operator CDataSource&amp;

返回对所包含的引用`CDataSource`对象。

### <a name="syntax"></a>语法

```cpp
operator const CDataSource&() throw();
```

### <a name="remarks"></a>备注

此运算符返回对所包含的引用`CDataSource`对象，允许将传入`CDataConnection`对象其中`CDataSource`应引用。

### <a name="example"></a>示例

如果您有一个函数 (如`func`下面) 采用`CDataSource`引用，可以使用`CDataSource&`传递`CDataConnection`对象。

[!code-cpp[NVC_OLEDB_Consumer#3](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#4](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_2.cpp)]

## <a name="op_cdata_star"></a> Cdataconnection:: Operator CDataSource *

返回指向包含的 `CDataSource` 对象的指针。

### <a name="syntax"></a>语法

```cpp
operator const CDataSource*() throw();
```

### <a name="remarks"></a>备注

此运算符将返回指向包含的 `CDataSource` 对象的指针，允许您传递 `CDataConnection` 对象（其中需要 `CDataSource` 指针）。

请参阅[运算符 CDataSource &](../../data/oledb/cdataconnection-operator-cdatasource-amp.md)有关用法示例。

## <a name="op_csession_amp"></a> Cdataconnection:: Operator CSession&amp;

返回对所包含的引用`CSession`对象。

### <a name="syntax"></a>语法

```cpp
operator const CSession&();
```

### <a name="remarks"></a>备注

此运算符返回对所包含的引用`CSession`对象，允许将传入`CDataConnection`对象其中`CSession`应引用。

### <a name="example"></a>示例

如果您有一个函数 (如`func`下面) 采用`CSession`引用，可以使用`CSession&`传递`CDataConnection`对象。

[!code-cpp[NVC_OLEDB_Consumer#5](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#6](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_2.cpp)]

## <a name="op_csession_star"></a> CDataConnection::operator CSession*

返回指向包含的 `CSession` 对象的指针。

### <a name="syntax"></a>语法

```cpp
operator const CSession*() throw();
```

### <a name="remarks"></a>备注

此运算符将返回指向包含的 `CSession` 对象的指针，允许您传递 `CDataConnection` 对象（其中需要 `CSession` 指针）。

### <a name="example"></a>示例

请参阅[运算符 CSession &](../../data/oledb/cdataconnection-operator-csession-amp.md)有关用法示例。

## <a name="see-also"></a>请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)