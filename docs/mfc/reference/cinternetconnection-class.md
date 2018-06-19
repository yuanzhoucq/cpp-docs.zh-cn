---
title: CInternetConnection 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CInternetConnection
- AFXINET/CInternetConnection
- AFXINET/CInternetConnection::CInternetConnection
- AFXINET/CInternetConnection::GetContext
- AFXINET/CInternetConnection::GetServerName
- AFXINET/CInternetConnection::GetSession
dev_langs:
- C++
helpviewer_keywords:
- CInternetConnection [MFC], CInternetConnection
- CInternetConnection [MFC], GetContext
- CInternetConnection [MFC], GetServerName
- CInternetConnection [MFC], GetSession
ms.assetid: 62a5d1c3-8471-4e36-a064-48831829b2a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 07b269afce3ec0c3ef60e6cc37782fdea18260cf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33366673"
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
|[CInternetConnection::operator HINTERNET](#operator_hinternet)|Internet 会话句柄。|  
  
## <a name="remarks"></a>备注  
 它是 MFC 类的基类[CFtpConnection](../../mfc/reference/cftpconnection-class.md)， [CHttpConnection](../../mfc/reference/chttpconnection-class.md)，和[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)。 每个这些类提供附加功能与相应的 FTP、 HTTP 或 gopher 服务器进行通信。  
  
 若要直接与 Internet 服务器进行通信，你必须[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象和一个`CInternetConnection`对象。  
  
 若要了解有关如何 WinInet 类工作的详细信息，请参阅文章[使用 WinInet Internet 编程](../../mfc/win32-internet-extensions-wininet.md)。  
  
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
 `pSession`  
 指向的指针[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象。  
  
 `pstrServer`  
 指向包含服务器名称的字符串的指针。  
  
 `nPort`  
 标识此连接的 Internet 端口数。  
  
 `dwContext`  
 上下文标识符`CInternetConnection`对象。 请参阅**备注**有关详细信息`dwContext`。  
  
### <a name="remarks"></a>备注  
 永远不会调用`CInternetConnection`自己; 而应调用[CInternetSession](../../mfc/reference/cinternetsession-class.md)您想要建立的连接的类型的成员函数：  
  
- [Cinternetsession:: Getftpconnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)  
  
- [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)  
  
- [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)  
  
 默认值为`dwContext`发送到 mfc `CInternetConnection`-派生对象从[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象创建**InternetConnection**-派生对象。 默认值设置为 1;但是，你可以显式将分配中的特定的上下文标识符[CInternetSession](../../mfc/reference/cinternetsession-class.md#cinternetsession)连接的构造函数。 对象和做的任何工作将与该上下文 id。 上下文标识符返回到[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供用于标识对象上的状态。 请参阅文章[Internet 前几个步骤： WinInet](../../mfc/wininet-basics.md)有关的上下文标识符的详细信息。  
  
##  <a name="getcontext"></a>  CInternetConnection::GetContext  
 调用此成员函数可获取此会话的上下文 ID。  
  
```  
DWORD_PTR GetContext() const;  
```  
  
### <a name="return-value"></a>返回值  
 应用程序分配的上下文 id。  
  
### <a name="remarks"></a>备注  
 中最初指定的上下文 ID [CInternetSession](../../mfc/reference/cinternetsession-class.md)并传播到`CInternetConnection`-和[CInternetFile](../../mfc/reference/cinternetfile-class.md)-派生类中，除非对打开的函数调用中指定以不同方式连接。 上下文 ID 与给定的任何的对象操作相关联，并标识返回的操作的状态信息[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)。  
  
 详细了解如何**GetContext**适用于其他 WinInet 类，让用户状态信息，请参阅文章[Internet 前几个步骤： WinInet](../../mfc/wininet-basics.md)有关上下文的详细信息标识符。  
  
##  <a name="getservername"></a>  CInternetConnection::GetServerName  
 调用此成员函数可获取与此 Internet 连接关联的服务器的名称。  
  
```  
CString GetServerName() const;  
```  
  
### <a name="return-value"></a>返回值  
 此连接对象正在使用服务器的名称。  
  
##  <a name="getsession"></a>  CInternetConnection::GetSession  
 调用此成员函数以获取指向`CInternetSession`具有与此连接关联的对象。  
  
```  
CInternetSession* GetSession() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向的指针[CInternetSession](../../mfc/reference/cinternetsession-class.md)与此 Internet 连接对象关联的对象。  
  
##  <a name="operator_hinternet"></a>  CInternetConnection::operator HINTERNET  
 使用此运算符为当前的 Internet 会话获取的 API 级别句柄。  
  
```  
operator HINTERNET() const;  
```  
  
## <a name="see-also"></a>请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)



