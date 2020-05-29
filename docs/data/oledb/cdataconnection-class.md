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
ms.openlocfilehash: fe954e218a099fa7956748904a4baa89f741c52f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368612"
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
|[CData连接](#cdataconnection)|构造函数。 实例化和初始化`CDataConnection`对象。|
|[复制](#copy)|创建现有数据连接的副本。|
|[打开](#open)|使用初始化字符串打开与数据源的连接。|
|[打开新会话](#opennewsession)|在当前连接上打开新会话。|

### <a name="operators"></a>运算符

|||
|-|-|
|[运营商 BOOL](#op_bool)|确定当前会话是否打开。|
|[operator bool](#op_bool_ole)|确定当前会话是否打开。|
|[运算符 CDataSource&](#op_cdata_amp)|返回对包含`CDataSource`对象的引用。|
|[运算符 CDataSource*](#op_cdata_star)|返回指向包含的 `CDataSource` 对象的指针。|
|[运算符 CSession&](#op_csession_amp)|返回对包含`CSession`对象的引用。|
|[运算符 CSession*](#op_csession_star)|返回指向包含的 `CSession` 对象的指针。|

## <a name="remarks"></a>备注

`CDataConnection`是创建客户端的有用类，因为它封装了必要的对象（数据源和会话）以及连接到数据源时需要执行的一些工作

如果没有`CDataConnection` `CDataSource` ，您必须创建对象，调用其[OpenFrom 初始化String](../../data/oledb/cdatasource-openfrominitializationstring.md)方法，然后创建[CSession](../../data/oledb/csession-class.md)对象的实例，调用其[Open](../../data/oledb/csession-open.md)方法，然后创建[CCommand](../../data/oledb/ccommand-class.md)对象`Open`并调用其 * 方法。

使用`CDataConnection`时，您只需创建连接对象，传递初始化字符串，然后使用该连接打开命令。 如果您计划重复使用与数据库的连接，最好保持连接打开状态，并提供`CDataConnection`一种方便的方法。

> [!NOTE]
> 如果要创建需要处理多个会话的数据库应用程序，则需要使用[OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md)。

## <a name="cdataconnectioncdataconnection"></a><a name="cdataconnection"></a>CData连接：：CData连接

实例化和初始化`CDataConnection`对象。

### <a name="syntax"></a>语法

```cpp
CDataConnection();
CDataConnection(const CDataConnection &ds);
```

#### <a name="parameters"></a>参数

*Ds*<br/>
[在]对现有数据连接的引用。

### <a name="remarks"></a>备注

第一个覆盖将创建`CDataConnection`具有默认设置的新对象。

第二个重写将创建`CDataConnection`一个新对象，其设置与指定的数据连接对象等效。

## <a name="cdataconnectioncopy"></a><a name="copy"></a>CData连接：：复制

创建现有数据连接的副本。

### <a name="syntax"></a>语法

```cpp
CDataConnection& Copy(const CDataConnection & ds) throw();
```

#### <a name="parameters"></a>参数

*Ds*<br/>
[在]对现有要复制的数据连接的引用。

## <a name="cdataconnectionopen"></a><a name="open"></a>CData连接：：打开

使用初始化字符串打开与数据源的连接。

### <a name="syntax"></a>语法

```cpp
HRESULT Open(LPCOLESTR szInitString) throw();
```

#### <a name="parameters"></a>参数

*什因特斯特林*<br/>
[在]数据源的初始化字符串。

### <a name="return-value"></a>返回值

标准 HRESULT。

## <a name="cdataconnectionopennewsession"></a><a name="opennewsession"></a>CData连接：：打开新会话

使用当前连接对象的数据源打开新会话。

### <a name="syntax"></a>语法

```cpp
HRESULT OpenNewSession(CSession & session) throw();
```

#### <a name="parameters"></a>参数

*会话*<br/>
[进出]对新会话对象的引用。

### <a name="remarks"></a>备注

新会话使用当前连接对象的包含数据源对象作为其父对象，并可以访问与数据源相同的所有信息。

### <a name="return-value"></a>返回值

标准 HRESULT。

## <a name="cdataconnectionoperator-bool"></a><a name="op_bool"></a>CData连接：：操作员BOOL

确定当前会话是否打开。

### <a name="syntax"></a>语法

```cpp
operator BOOL() throw();
```

### <a name="remarks"></a>备注

返回**BOOL** （MFC 类型def） 值。 **TRUE**表示当前会话处于打开状态;**FALSE**表示当前会话已关闭。

## <a name="cdataconnectionoperator-bool-ole-db"></a><a name="op_bool_ole"></a>CData连接：：操作员布尔（OLE DB）

确定当前会话是否打开。

### <a name="syntax"></a>语法

```cpp
operator bool() throw();
```

### <a name="remarks"></a>备注

返回**bool（C++** 数据类型）值。 **true**表示当前会话处于打开状态;**false**表示当前会话已关闭。

## <a name="cdataconnectionoperator-cdatasourceamp"></a><a name="op_cdata_amp"></a>CData连接：：运营商CDataSource&amp;

返回对包含`CDataSource`对象的引用。

### <a name="syntax"></a>语法

```cpp
operator const CDataSource&() throw();
```

### <a name="remarks"></a>备注

此运算符返回对包含`CDataSource`对象的引用，允许您传递预期`CDataConnection``CDataSource`引用的对象。

### <a name="example"></a>示例

如果您有一个`func`函数（如下所示），可以引用`CDataSource`引用，则可以使用`CDataSource&`传递`CDataConnection`对象。

[!code-cpp[NVC_OLEDB_Consumer#3](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#4](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_2.cpp)]

## <a name="cdataconnectionoperator-cdatasource"></a><a name="op_cdata_star"></a>CData连接：：操作员 CDataSource*

返回指向包含的 `CDataSource` 对象的指针。

### <a name="syntax"></a>语法

```cpp
operator const CDataSource*() throw();
```

### <a name="remarks"></a>备注

此运算符将返回指向包含的 `CDataSource` 对象的指针，允许您传递 `CDataConnection` 对象（其中需要 `CDataSource` 指针）。

有关使用示例，请参阅[运算符 CDataSource&。](../../data/oledb/cdataconnection-operator-cdatasource-amp.md)

## <a name="cdataconnectionoperator-csessionamp"></a><a name="op_csession_amp"></a>CData连接：：操作员会话&amp;

返回对包含`CSession`对象的引用。

### <a name="syntax"></a>语法

```cpp
operator const CSession&();
```

### <a name="remarks"></a>备注

此运算符返回对包含`CSession`对象的引用，允许您传递预期`CDataConnection``CSession`引用的对象。

### <a name="example"></a>示例

如果您有一个`func`函数（如下所示），可以引用`CSession`引用，则可以使用`CSession&`传递`CDataConnection`对象。

[!code-cpp[NVC_OLEDB_Consumer#5](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#6](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_2.cpp)]

## <a name="cdataconnectionoperator-csession"></a><a name="op_csession_star"></a>CData连接：：操作员会话*

返回指向包含的 `CSession` 对象的指针。

### <a name="syntax"></a>语法

```cpp
operator const CSession*() throw();
```

### <a name="remarks"></a>备注

此运算符将返回指向包含的 `CSession` 对象的指针，允许您传递 `CDataConnection` 对象（其中需要 `CSession` 指针）。

### <a name="example"></a>示例

有关使用示例，请参阅[运算符 CSession&。](../../data/oledb/cdataconnection-operator-csession-amp.md)

## <a name="see-also"></a>另请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)
