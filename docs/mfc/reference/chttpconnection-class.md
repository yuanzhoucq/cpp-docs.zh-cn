---
title: "CHttpConnection 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHttpConnection
dev_langs:
- C++
helpviewer_keywords:
- servers, connecting to
- protocols, HTTP
- connecting to servers, HTTP servers
- Internet protocols, HTTP
- HTTP connections
- Internet protocols
- CHttpConnection class
- HTTP servers, connecting to
- connecting to servers
- Internet connections, HTTP
- connections [C++], HTTP
- Internet server, HTTP
ms.assetid: a402b662-c445-4988-800d-c8278551babe
caps.latest.revision: 24
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 1b02a79cebbd73a05478887115646f0544f0a92d
ms.lasthandoff: 02/24/2017

---
# <a name="chttpconnection-class"></a>CHttpConnection 类
管理与 HTTP 服务器的连接。  
  
## <a name="syntax"></a>语法  
  
```  
class CHttpConnection : public CInternetConnection  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CHttpConnection::CHttpConnection](#chttpconnection)|创建一个 `CHttpConnection` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[Chttpconnection::](#openrequest)|打开 HTTP 请求。|  
  
## <a name="remarks"></a>备注  
 HTTP 是一个 MFC WinInet 类实现了三种 Internet 服务器协议。  
  
 此类`CHttpConnection`包含构造函数和一个成员函数， [OpenRequest](#openrequest)，管理与 HTTP 协议与服务器的连接。  
  
 要与 HTTP 服务器通信，必须首先创建的实例[CInternetSession](../../mfc/reference/cinternetsession-class.md)，然后创建[CHttpConnection](#_mfc_chttpconnection)对象。 切勿创建`CHttpConnection`直接对象; 而是调用[cinternetsession:: Gethttpconnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)，后者可创建`CHttpConnection`对象，并将指针返回到它。  
  
 若要了解有关如何`CHttpConnection`工作与其他 MFC Internet 类，请参阅文章[Internet 编程与 WinInet](../../mfc/win32-internet-extensions-wininet.md)。 有关连接到使用其他两个服务器的详细信息支持 Internet 协议、 gopher 和 FTP，请参阅类[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)和[CFtpConnection](../../mfc/reference/cftpconnection-class.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)  
  
 `CHttpConnection`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxinet.h  
  
##  <a name="a-namechttpconnectiona--chttpconnectionchttpconnection"></a><a name="chttpconnection"></a>CHttpConnection::CHttpConnection  
 调用此成员函数来构造`CHttpConnection`对象。  
  
```  
CHttpConnection(
    CInternetSession* pSession,  
    HINTERNET hConnected,  
    LPCTSTR pstrServer,  
    DWORD_PTR dwContext);

 
CHttpConnection(
    CInternetSession* pSession,  
    LPCTSTR pstrServer,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,  
    LPCTSTR pstrUserName = NULL,  
    LPCTSTR pstrPassword = NULL,  
    DWORD_PTR dwContext = 1);

 
CHttpConnection(
    CInternetSession* pSession,  
    LPCTSTR pstrServer,  
    DWORD dwFlags,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,  
    LPCTSTR pstrUserName = NULL,  
    LPCTSTR pstrPassword = NULL,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>参数  
 `pSession`  
 一个指向[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象。  
  
 `hConnected`  
 Internet 连接句柄。  
  
 `pstrServer`  
 指向一个包含服务器名称的字符串的指针。  
  
 `dwContext`  
 上下文标识符`CInternetConnection`对象。 请参阅**备注**有关详细信息`dwContext`。  
  
 `nPort`  
 标识此连接的互联网端口的编号。  
  
 `pstrUserName`  
 以 null 结尾的字符串，它指定要以用户身份登录的用户名称的指针。 如果**NULL**，默认值是匿名的。  
  
 `pstrPassword`  
 指向以 null 结尾的字符串，指定要用于登录的密码的指针。 如果两个`pstrPassword`和`pstrUserName`是**NULL**，默认匿名密码是用户的电子邮件名称。 如果`pstrPassword`是**NULL** （或空字符串），但`pstrUserName`不是**NULL**，使用空密码。 下表描述的四个可能的设置的行为`pstrUserName`和`pstrPassword`:  
  
|`pstrUserName`|`pstrPassword`|发送到 FTP 服务器的用户名|发送到 FTP 服务器的密码|  
|--------------------|--------------------|---------------------------------|---------------------------------|  
|**NULL**或""|**NULL**或""|"匿名"|用户的电子邮件名称|  
|非- **NULL**字符串|**NULL**或""|`pstrUserName`|" "|  
|**NULL**非**NULL**字符串|**错误**|**错误**||  
|非- **NULL**字符串|非- **NULL**字符串|`pstrUserName`|`pstrPassword`|  
  
 `dwFlags`  
 任意组合**INTERNET_ FLAG_\* **标志。 请参阅中的表**备注**部分[chttpconnection::](#openrequest)有关的说明`dwFlags`值。  
  
### <a name="remarks"></a>备注  
 切勿创建`CHttpConnection`直接。 相反，通过调用创建一个对象[cinternetsession:: Gethttpconnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)。  
  
##  <a name="a-nameopenrequesta--chttpconnectionopenrequest"></a><a name="openrequest"></a>Chttpconnection::  
 调用该成员函数以打开 HTTP 连接。  
  
```  
CHttpFile* OpenRequest(
    LPCTSTR pstrVerb,  
    LPCTSTR pstrObjectName,  
    LPCTSTR pstrReferer = NULL,  
    DWORD_PTR dwContext = 1,  
    LPCTSTR* ppstrAcceptTypes = NULL,  
    LPCTSTR pstrVersion = NULL,  
    DWORD dwFlags = INTERNET_FLAG_EXISTING_CONNECT);

 
CHttpFile* OpenRequest(
    int nVerb,  
    LPCTSTR pstrObjectName,  
    LPCTSTR pstrReferer = NULL,  
    DWORD_PTR dwContext = 1,  
    LPCTSTR* ppstrAcceptTypes = NULL,  
    LPCTSTR pstrVersion = NULL,  
    DWORD dwFlags = INTERNET_FLAG_EXISTING_CONNECT);
```  
  
### <a name="parameters"></a>参数  
 `pstrVerb`  
 指向一个包含要在请求中使用的谓词字符串的指针。 如果`NULL`，使用"GET"。  
  
 `pstrObjectName`  
 指向一个包含指定的谓词的目标对象的字符串的指针。 这通常是一个文件名、 可执行模块或搜索说明符。  
  
 `pstrReferer`  
 指向一个字符串，指定从其文档的地址 (URL) 中请求的 URL ( `pstrObjectName`) 获得。 如果`NULL`，指定的 HTTP 标头。  
  
 `dwContext`  
 上下文标识符`OpenRequest`操作。 请参阅备注部分以了解更多信息，关于`dwContext`。  
  
 `ppstrAcceptTypes`  
 以 null 结尾的数组的指针`LPCTSTR`客户端接受字符串来指示内容类型的指针。 如果`ppstrAcceptTypes`是`NULL`，服务器解释客户端仅接受类型的文档"文本 / *"（即，仅有的文本文档并不图片或其他二进制文件）。 内容类型等效于 CGI 变量 CONTENT_TYPE，用于标识用于已附加信息，如 HTTP POST 和 PUT 的查询的数据的类型。  
  
 `pstrVersion`  
 指向一个定义的 HTTP 版本字符串的指针。 如果`NULL`，使用"HTTP/1.0"。  
  
 `dwFlags`  
 INTERNET_ FLAG_ * 标志的任意组合。 请参阅备注部分中有关的可能说明`dwFlags`值。  
  
 `nVerb`  
 与 HTTP 请求类型的号码。 可以是以下各项之一：  
  
|HTTP 请求类型|`nVerb` 值|  
|-----------------------|-------------------|  
|`HTTP_VERB_POST`|0|  
|`HTTP_VERB_GET`|1|  
|`HTTP_VERB_HEAD`|2|  
|`HTTP_VERB_PUT`|3|  
|`HTTP_VERB_LINK`|4|  
|`HTTP_VERB_DELETE`|5|  
|`HTTP_VERB_UNLINK`|6|  
  
### <a name="return-value"></a>返回值  
 一个指向[CHttpFile](../../mfc/reference/chttpfile-class.md)请求对象。  
  
### <a name="remarks"></a>备注  
 `dwFlags`可以是以下项之一︰  
  
|Internet 标志|说明|  
|-------------------|-----------------|  
|`INTERNET_FLAG_RELOAD`|从原始服务器，而不是从缓存会强制下载请求的文件、 对象或在目录列表。|  
|`INTERNET_FLAG_DONT_CACHE`|不会向缓存添加返回的实体。|  
|`INTERNET_FLAG_MAKE_PERSISTENT`|将返回的实体为持久实体添加到缓存。 这意味着标准版缓存清理、 一致性检查，或垃圾回收无法从缓存删除该项目。|  
|`INTERNET_FLAG_SECURE`|使用安全的事务语义。 这将转换为使用 SSL/PCT，并且仅在 HTTP 请求中有意义|  
|`INTERNET_FLAG_NO_AUTO_REDIRECT`|仅用于 HTTP，则指定的重定向应该不会自动处理在[CHttpFile::SendRequest](../../mfc/reference/chttpfile-class.md#sendrequest)。|  
  
 重写`dwContext`默认上下文标识符设置为所选的值。 上下文标识符是否与此特定操作的关联`CHttpConnection`创建的对象及其[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象。 值返回到[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供有关它标识的操作的状态。 请参阅文章[Internet 前几个步骤︰ WinInet](../../mfc/wininet-basics.md)有关的上下文标识符的详细信息。  
  
 使用此函数可能会引发异常。  
  
## <a name="see-also"></a>另请参阅  
 [CInternetConnection 类](../../mfc/reference/cinternetconnection-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CInternetConnection 类](../../mfc/reference/cinternetconnection-class.md)   
 [CHttpFile 类](../../mfc/reference/chttpfile-class.md)

