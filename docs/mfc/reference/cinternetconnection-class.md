---
title: C 互联网连接类
ms.date: 11/04/2016
f1_keywords:
- CInternetConnection
- AFXINET/CInternetConnection
- AFXINET/CInternetConnection::CInternetConnection
- AFXINET/CInternetConnection::GetContext
- AFXINET/CInternetConnection::GetServerName
- AFXINET/CInternetConnection::GetSession
helpviewer_keywords:
- CInternetConnection [MFC], CInternetConnection
- CInternetConnection [MFC], GetContext
- CInternetConnection [MFC], GetServerName
- CInternetConnection [MFC], GetSession
ms.assetid: 62a5d1c3-8471-4e36-a064-48831829b2a7
ms.openlocfilehash: 6649986f279e010a833b31157922cb4fd1ea8613
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372426"
---
# <a name="cinternetconnection-class"></a>C 互联网连接类

管理与 Internet 服务器的连接。

## <a name="syntax"></a>语法

```
class CInternetConnection : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C 网连接：C 网连接](#cinternetconnection)|构造 `CInternetConnection` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[C 互联网连接：获取上下文](#getcontext)|获取此连接对象的上下文 ID。|
|[C 互联网连接：：获取服务器名称](#getservername)|获取与连接关联的服务器的名称。|
|[C 互联网连接：获取会话](#getsession)|获取指向与连接关联的[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象的指针。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[C网连接：：运营商HINTERNET](#operator_hinternet)|互联网会话的句柄。|

## <a name="remarks"></a>备注

它是 MFC 类[CFtpConnection、CHttpConnection](../../mfc/reference/cftpconnection-class.md)和[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)的基类。 [CHttpConnection](../../mfc/reference/chttpconnection-class.md) 每个类都提供了与相应的 FTP、HTTP 或 gopher 服务器通信的其他功能。

要直接与 Internet 服务器通信，您必须具有[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象和`CInternetConnection`对象。

要了解有关 WinInet 类如何工作的更多信息，请参阅[使用 WinInet 进行 Internet 编程的文章](../../mfc/win32-internet-extensions-wininet.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CInternetConnection`

## <a name="requirements"></a>要求

**标题：** afxinet.h

## <a name="cinternetconnectioncinternetconnection"></a><a name="cinternetconnection"></a>C 网连接：C 网连接

创建`CInternetConnection`对象时将调用此成员函数。

```
CInternetConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>参数

*p 会话*<br/>
指向[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象的指针。

*pstrServer*<br/>
指向包含服务器名称的字符串的指针。

*n波特*<br/>
标识此连接的 Internet 端口的数字。

*dwContext*<br/>
`CInternetConnection`对象的上下文标识符。 有关*dwContext*的详细信息，请参阅**备注**。

### <a name="remarks"></a>备注

你从来不叫`CInternetConnection`自己;相反，请调用[CInternetSession](../../mfc/reference/cinternetsession-class.md)成员函数，表示要建立的连接类型：

- [C 互联网会话：：获取Ftp连接](../../mfc/reference/cinternetsession-class.md#getftpconnection)

- [C 互联网会话：：获取Http连接](../../mfc/reference/cinternetsession-class.md#gethttpconnection)

- [C 互联网会话：：获取 Gopher 连接](../../mfc/reference/cinternetsession-class.md#getgopherconnection)

mFC 将*dwContext*的默认值发送到创建`CInternetConnection`**InternetConnection**派生对象的[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象的派生对象。 默认值设置为 1;将默认值设置为 1但是，您可以在连接的[CInternetSession](../../mfc/reference/cinternetsession-class.md#cinternetsession)构造函数中显式分配特定的上下文标识符。 对象及其执行的任何工作都将与该上下文 ID 相关联。 上下文标识符返回到[CInternetSession：：onStatusBackononononononback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)提供标识它的对象的状态。 有关上下文标识符的详细信息[，请参阅"Internet 第一步：WinInet"](../../mfc/wininet-basics.md)一文。

## <a name="cinternetconnectiongetcontext"></a><a name="getcontext"></a>C 互联网连接：获取上下文

调用此成员函数获取此会话的上下文 ID。

```
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>返回值

应用程序分配的上下文 ID。

### <a name="remarks"></a>备注

上下文 ID 最初在[CInternetSession](../../mfc/reference/cinternetsession-class.md)中指定，`CInternetConnection`并传播到 - 和[CInternetFile](../../mfc/reference/cinternetfile-class.md)派生类，除非在调用打开连接的函数时以不同方式指定。 上下文 ID 与给定对象的任何操作相关联，并标识 CInternetSession 返回的操作的状态信息[：：onStatusCallback。](../../mfc/reference/cinternetsession-class.md#onstatuscallback)

有关如何使用`GetContext`其他 WinInet 类提供用户状态信息的详细信息，请参阅文章["Internet 第一步：WinInet"](../../mfc/wininet-basics.md)了解有关上下文标识符的详细信息。

## <a name="cinternetconnectiongetservername"></a><a name="getservername"></a>C 互联网连接：：获取服务器名称

调用此成员函数获取与此 Internet 连接关联的服务器的名称。

```
CString GetServerName() const;
```

### <a name="return-value"></a>返回值

此连接对象正在使用的服务器的名称。

## <a name="cinternetconnectiongetsession"></a><a name="getsession"></a>C 互联网连接：获取会话

调用此成员函数以获取指向与此连接关联的`CInternetSession`对象的指针。

```
CInternetSession* GetSession() const;
```

### <a name="return-value"></a>返回值

指向与此 Internet 连接对象关联的[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象的指针。

## <a name="cinternetconnectionoperator-hinternet"></a><a name="operator_hinternet"></a>C网连接：：运营商HINTERNET

使用此运算符获取当前 Internet 会话的 API 级句柄。

```
operator HINTERNET() const;
```

## <a name="see-also"></a>另请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
