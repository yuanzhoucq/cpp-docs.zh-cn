---
title: CInternetConnection 类
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
ms.openlocfilehash: 9f17c3ade53ec45ddde654e83c77fe1d817d8495
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62345690"
---
# <a name="cinternetconnection-class"></a>CInternetConnection 类

管理与 Internet 服务器的连接。

## <a name="syntax"></a>语法

```
class CInternetConnection : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CInternetConnection::CInternetConnection](#cinternetconnection)|构造 `CInternetConnection` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CInternetConnection::GetContext](#getcontext)|获取此连接对象的上下文 ID。|
|[CInternetConnection::GetServerName](#getservername)|获取与连接关联的服务器的名称。|
|[CInternetConnection::GetSession](#getsession)|获取一个指向[CInternetSession](../../mfc/reference/cinternetsession-class.md)与连接关联的对象。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CInternetConnection::operator HINTERNET](#operator_hinternet)|一个 Internet 会话句柄。|

## <a name="remarks"></a>备注

它是 MFC 类的基类[CFtpConnection](../../mfc/reference/cftpconnection-class.md)， [CHttpConnection](../../mfc/reference/chttpconnection-class.md)，并[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)。 每个类提供附加功能与相应的 FTP、 HTTP 或 gopher 服务器进行通信。

若要直接与 Internet 服务器进行通信，必须具有[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象和一个`CInternetConnection`对象。

若要了解有关如何 WinInet 类工作的详细信息，请参阅文章[Internet 编程与 WinInet](../../mfc/win32-internet-extensions-wininet.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CInternetConnection`

## <a name="requirements"></a>要求

**标头：** afxinet.h

##  <a name="cinternetconnection"></a>  CInternetConnection::CInternetConnection

此成员函数调用时`CInternetConnection`创建对象。

```
CInternetConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>参数

*pSession*<br/>
一个指向[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象。

*pstrServer*<br/>
指向包含服务器名称的字符串的指针。

*nPort*<br/>
标识此连接的 Internet 端口数。

*dwContext*<br/>
上下文标识符`CInternetConnection`对象。 请参阅**备注**有关详细信息*dwContext*。

### <a name="remarks"></a>备注

永远不会调用`CInternetConnection`自行; 而应调用[CInternetSession](../../mfc/reference/cinternetsession-class.md)您想要建立的连接的类型的成员函数：

- [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)

- [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)

- [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)

默认值为*dwContext*发送到 mfc `CInternetConnection`-派生的对象从[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象创建**InternetConnection**-派生的对象。 默认值设置为 1;但是，可以显式分配中的特定上下文标识符[CInternetSession](../../mfc/reference/cinternetsession-class.md#cinternetsession)连接的构造函数。 将与该上下文 id。 关联的对象以及它执行任何工作 上下文标识符就会归还[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供与该标识的对象上的状态。 请参阅文章[Internet 前几个步骤：WinInet](../../mfc/wininet-basics.md)有关的上下文标识符的详细信息。

##  <a name="getcontext"></a>  CInternetConnection::GetContext

调用此成员函数可获取为此会话的上下文 ID。

```
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>返回值

应用程序分配的上下文 id。

### <a name="remarks"></a>备注

中最初指定的上下文 ID [CInternetSession](../../mfc/reference/cinternetsession-class.md) ，并将传播到`CInternetConnection`-并[CInternetFile](../../mfc/reference/cinternetfile-class.md)的派生类中，除非另有指定以不同的方式对打开的函数的调用中连接。 上下文 ID 是与给定任何的对象操作相关联，并且标识返回的操作的状态信息[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)。

详细了解如何`GetContext`适用于其他 WinInet 类，让用户状态信息，请参阅文章[Internet 前几个步骤：WinInet](../../mfc/wininet-basics.md)有关的上下文标识符的详细信息。

##  <a name="getservername"></a>  CInternetConnection::GetServerName

调用此成员函数以获取与此 Internet 连接关联的服务器的名称。

```
CString GetServerName() const;
```

### <a name="return-value"></a>返回值

此连接对象正在与服务器的名称。

##  <a name="getsession"></a>  CInternetConnection::GetSession

调用此成员函数可获取一个指向`CInternetSession`与此连接关联的对象。

```
CInternetSession* GetSession() const;
```

### <a name="return-value"></a>返回值

一个指向[CInternetSession](../../mfc/reference/cinternetsession-class.md)与此 Internet 连接对象关联的对象。

##  <a name="operator_hinternet"></a>  CInternetConnection::operator HINTERNET

使用此运算符将当前的 Internet 会话获取的 API 级别句柄。

```
operator HINTERNET() const;
```

## <a name="see-also"></a>请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
