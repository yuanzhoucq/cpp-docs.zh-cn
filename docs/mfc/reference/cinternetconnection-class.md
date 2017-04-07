---
title: "CInternetConnection 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- asynchronous connections
- CInternetConnection class
- Internet connections
ms.assetid: 62a5d1c3-8471-4e36-a064-48831829b2a7
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 7f99562e0c6103fc3f46a7fe28f9d2f2efff0a01
ms.lasthandoff: 02/24/2017

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
  
|名称|说明|  
|----------|-----------------|  
|[CInternetConnection::GetContext](#getcontext)|获取此连接对象的上下文 ID。|  
|[CInternetConnection::GetServerName](#getservername)|获取与连接相关联的服务器的名称。|  
|[CInternetConnection::GetSession](#getsession)|获取一个指针，到[CInternetSession](../../mfc/reference/cinternetsession-class.md)与连接关联的对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CInternetConnection::operator HINTERNET](#operator_hinternet)|一个 Internet 会话句柄。|  
  
## <a name="remarks"></a>备注  
 它是 MFC 类的基类[CFtpConnection](../../mfc/reference/cftpconnection-class.md)， [CHttpConnection](../../mfc/reference/chttpconnection-class.md)，和[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)。 其中每个类提供其他功能与各自的 FTP、 HTTP 或 gopher 服务器进行通信。  
  
 若要直接与 Internet 服务器进行通信，您必须[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象和一个`CInternetConnection`对象。  
  
 若要了解有关如何 WinInet 类工作的详细信息，请参阅文章[Internet 编程与 WinInet](../../mfc/win32-internet-extensions-wininet.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CInternetConnection`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxinet.h  
  
##  <a name="cinternetconnection"></a>CInternetConnection::CInternetConnection  
 当调用此成员函数`CInternetConnection`创建对象。  
  
```  
CInternetConnection(
    CInternetSession* pSession,  
    LPCTSTR pstrServer,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>参数  
 `pSession`  
 一个指向[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象。  
  
 `pstrServer`  
 指向一个包含服务器名称的字符串的指针。  
  
 `nPort`  
 标识此连接的互联网端口的编号。  
  
 `dwContext`  
 上下文标识符`CInternetConnection`对象。 请参阅**备注**有关详细信息`dwContext`。  
  
### <a name="remarks"></a>备注  
 永远不会调用`CInternetConnection`自己; 而应调用[CInternetSession](../../mfc/reference/cinternetsession-class.md)你想要建立的连接的类型的成员函数︰  
  
- [Cinternetsession:: Getftpconnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)  
  
- [Cinternetsession:: Gethttpconnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)  
  
- [Cinternetsession:: Getgopherconnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)  
  
 默认值为`dwContext`发送到 mfc `CInternetConnection`-派生对象从[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象创建**InternetConnection**-派生的对象。 默认值设置为 1;但是，可以显式指定一个特定的上下文标识符[CInternetSession](../../mfc/reference/cinternetsession-class.md#cinternetsession)连接的构造函数。 该对象，并且它执行任何工作将与该上下文 id。 上下文标识符返回到[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供对它标识的对象的状态。 请参阅文章[Internet 前几个步骤︰ WinInet](../../mfc/wininet-basics.md)有关的上下文标识符的详细信息。  
  
##  <a name="getcontext"></a>CInternetConnection::GetContext  
 调用该成员函数以获取此会话的上下文 ID。  
  
```  
DWORD_PTR GetContext() const;  
```  
  
### <a name="return-value"></a>返回值  
 应用程序分配的上下文 id。  
  
### <a name="remarks"></a>备注  
 中最初指定的上下文 ID [CInternetSession](../../mfc/reference/cinternetsession-class.md)并传播到`CInternetConnection`-和[CInternetFile](../../mfc/reference/cinternetfile-class.md)的派生类中，除非对打开的连接的函数调用中以不同的方式指定。 上下文 ID 与给定任何的对象操作相关联，并标识该操作返回的状态信息[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)。  
  
 有关如何**GetContext**适用于其他 WinInet 类，让用户状态信息，请参阅文章[Internet 前几个步骤︰ WinInet](../../mfc/wininet-basics.md)有关的上下文标识符的详细信息。  
  
##  <a name="getservername"></a>CInternetConnection::GetServerName  
 调用该成员函数以获取与此 Internet 连接关联的服务器的名称。  
  
```  
CString GetServerName() const;  
```  
  
### <a name="return-value"></a>返回值  
 使用此连接对象的服务器的名称。  
  
##  <a name="getsession"></a>CInternetConnection::GetSession  
 调用此成员函数以获取指向`CInternetSession`具有与此连接关联的对象。  
  
```  
CInternetSession* GetSession() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向[CInternetSession](../../mfc/reference/cinternetsession-class.md)与此 Internet 连接对象关联的对象。  
  
##  <a name="operator_hinternet"></a>CInternetConnection::operator HINTERNET  
 使用此运算符将为当前的 Internet 会话获取的 API 级别句柄。  
  
```  
operator HINTERNET() const;  
```  
  
## <a name="see-also"></a>另请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)




