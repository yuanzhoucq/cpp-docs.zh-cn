---
title: "CGopherConnection 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CGopherConnection
- AFXINET/CGopherConnection
- AFXINET/CGopherConnection::CGopherConnection
- AFXINET/CGopherConnection::CreateLocator
- AFXINET/CGopherConnection::GetAttribute
- AFXINET/CGopherConnection::OpenFile
dev_langs: C++
helpviewer_keywords:
- CGopherConnection [MFC], CGopherConnection
- CGopherConnection [MFC], CreateLocator
- CGopherConnection [MFC], GetAttribute
- CGopherConnection [MFC], OpenFile
ms.assetid: b5b96aea-ac99-430e-bd84-d1372b43f78f
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d669ebc954b73d848e22dc373704ab3434074274
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cgopherconnection-class"></a>CGopherConnection 类
管理与 Gopher Internet 服务器的连接。  
  
> [!NOTE]
>  类`CGopherConnection`， `CGopherFile`， `CGopherFileFind`，`CGopherLocator`和其成员具有已弃用，因为它们不能在 Windows XP 平台上，但它们将继续在早期版本的平台上正常工作。  
  
## <a name="syntax"></a>语法  
  
```  
class CGopherConnection : public CInternetConnection  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CGopherConnection::CGopherConnection](#cgopherconnection)|构造 `CGopherConnection` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CGopherConnection::CreateLocator](#createlocator)|创建[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)对象可以查找 gopher 服务器上的文件。|  
|[CGopherConnection::GetAttribute](#getattribute)|检索有关 gopher 对象的属性信息。|  
|[CGopherConnection::OpenFile](#openfile)|打开 gopher 文件。|  
  
## <a name="remarks"></a>备注  
 Gopher 服务是由 MFC WinInet 类识别的三个 Internet 服务之一。  
  
 类`CGopherConnection`包含一个构造函数和三个其他成员函数来管理 gopher 服务： [OpenFile](#openfile)， [CreateLocator](#createlocator)，和[GetAttribute](#getattribute).  
  
 若要与 gopher Internet 服务器通信，必须先创建的实例[CInternetSession](../../mfc/reference/cinternetsession-class.md)，然后调用[CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)，这将创建`CGopherConnection`对象，并将指针返回到它。 切勿创建`CGopherConnection`直接对象。  
  
 若要了解有关如何`CGopherConnection`工作与其他 MFC Internet 类，请参阅文章[使用 WinInet Internet 编程](../../mfc/win32-internet-extensions-wininet.md)。 有关详细信息使用与其他两个支持的 Internet 服务，FTP 和 HTTP 请参阅类[CHttpConnection](../../mfc/reference/chttpconnection-class.md)和[CFtpConnection](../../mfc/reference/cftpconnection-class.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)  
  
 `CGopherConnection`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxinet.h  
  
##  <a name="cgopherconnection"></a>CGopherConnection::CGopherConnection  
 此成员函数调用以构造`CGopherConnection`对象。  
  
```  
CGopherConnection(
    CInternetSession* pSession,  
    HINTERNET hConnected,  
    LPCTSTR pstrServer,  
    DWORD_PTR dwContext);

 
CGopherConnection(
    CInternetSession* pSession,  
    LPCTSTR pstrServer,  
    LPCTSTR pstrUserName = NULL,  
    LPCTSTR pstrPassword = NULL,  
    DWORD_PTR dwContext = 0,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```  
  
### <a name="parameters"></a>参数  
 `pSession`  
 指向相关[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象。  
  
 `hConnected`  
 当前的 Internet 会话的 Windows 句柄。  
  
 `pstrServer`  
 指向包含 FTP 服务器名称的字符串的指针。  
  
 `dwContext`  
 操作上下文标识符。 `dwContext`标识返回的操作的状态信息[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)。 默认值设置为 1;但是，你可以显式分配操作的特定的上下文 ID。 对象和做的任何工作将与该上下文 id。  
  
 `pstrUserName`  
 指向以 null 结尾的字符串，指定要登录的用户的名称。 如果**NULL**，默认值是匿名的。  
  
 `pstrPassword`  
 指向一个以 null 结尾的字符串，指定要用于登录的密码的指针。 如果这两个`pstrPassword`和`pstrUserName`是**NULL**，默认匿名密码是用户的电子邮件名称。 如果`pstrPassword`是**NULL** （或空字符串），但`pstrUserName`不**NULL**，使用空白密码。 下表描述的四个可能的设置的行为`pstrUserName`和`pstrPassword`:  
  
|`pstrUserName`|`pstrPassword`|发送到 FTP 服务器的用户名|发送到 FTP 服务器的密码|  
|--------------------|--------------------|---------------------------------|---------------------------------|  
|**NULL**或""|**NULL**或""|"匿名"|用户的电子邮件名称|  
|非- **NULL**字符串|**NULL**或""|`pstrUserName`|" "|  
|**NULL**非**NULL**字符串|**错误**|**错误**||  
|非- **NULL**字符串|非- **NULL**字符串|`pstrUserName`|`pstrPassword`|  
  
 `nPort`  
 一个数字，标识要使用服务器上的 TCP/IP 端口。  
  
### <a name="remarks"></a>备注  
 切勿创建`CGopherConnection`直接。 相反，调用[CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)，这将创建`CGopherConnection`对象，并将指针返回到它。  
  
##  <a name="createlocator"></a>CGopherConnection::CreateLocator  
 调用此成员函数可创建 gopher 定位符以查找或识别 gopher 服务器上的文件。  
  
```  
CGopherLocator CreateLocator(
    LPCTSTR pstrDisplayString,  
    LPCTSTR pstrSelectorString,  
    DWORD dwGopherType);  
  
static CGopherLocator CreateLocator(LPCTSTR pstrLocator);

 
static CGopherLocator CreateLocator(
    LPCTSTR pstrServerName,  
    LPCTSTR pstrDisplayString,  
    LPCTSTR pstrSelectorString,  
    DWORD dwGopherType,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```  
  
### <a name="parameters"></a>参数  
 `pstrDisplayString`  
 指向包含 gopher 文档或要检索的目录名称的字符串的指针。 如果`pstrDisplayString`参数是**NULL**，返回 gopher 服务器的默认目录。  
  
 `pstrSelectorString`  
 指向要发送到 gopher 服务器以检索项的选择器字符串的指针。 `pstrSelectorString`可以是**NULL**。  
  
 *dwGopherType*  
 此设置指定是否`pstrSelectorString`指一个目录或文档，以及请求是 gopher +。 请参阅结构属性[GOPHER_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa384215) Windows SDK 中。  
  
 `pstrLocator`  
 指向用于标识要打开的文件的字符串的指针。 通常情况下，此字符串返回到调用[CGopherFileFind::GetLocator](../../mfc/reference/cgopherfilefind-class.md#getlocator)。  
  
 *pstrServerName*  
 指向包含 gopher 服务器名称的字符串的指针。  
  
 `nPort`  
 标识此连接的 Internet 端口的编号。  
  
### <a name="return-value"></a>返回值  
 A [CGopherLocator](../../mfc/reference/cgopherlocator-class.md)对象。  
  
### <a name="remarks"></a>备注  
 成员函数的静态版本要求你指定服务器，而非静态版本使用的连接对象的服务器名称。  
  
 从 gopher 服务器检索信息，以便应用程序必须先获取 gopher 定位符。 应用程序然后必须将定位符视为不透明的令牌 （即，应用程序可以使用该定位符但不是直接操作或将其进行比较）。 通常情况下，应用程序使用该定位符以便调用[CGopherFileFind::FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile)成员函数以检索特定的信息。  
  
##  <a name="getattribute"></a>CGopherConnection::GetAttribute  
 调用此成员函数以从 gopher 服务器检索有关某个项的特定属性信息。  
  
```  
BOOL GetAttribute(
    CGopherLocator& refLocator    CString strRequestedAttributes,  
    CString& strResult,);
```  
  
### <a name="parameters"></a>参数  
 `refLocator`  
 对引用[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)对象。  
  
 *strRequestedAttributes*  
 指定请求的属性的名称以空格分隔的字符串。  
  
 `strResult`  
 对引用[CString](../../atl-mfc-shared/reference/cstringt-class.md)接收定位符类型。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 如果调用失败，Win32 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可调用以确定错误的原因。  
  
##  <a name="openfile"></a>CGopherConnection::OpenFile  
 调用此成员函数以打开 gopher 服务器上的文件。  
  
```  
CGopherFile* OpenFile(
    CGopherLocator& refLocator,  
    DWORD dwFlags = 0,  
    LPCTSTR pstrView = NULL,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>参数  
 `refLocator`  
 对引用[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)对象。  
  
 `dwFlags`  
 INTERNET_FLAG_ * 标志的任意组合。 请参阅[cinternetsession:: Openurl](../../mfc/reference/cinternetsession-class.md#openurl)有关进一步信息 INTERNET_FLAG_\*标志。  
  
 `pstrView`  
 指向文件视图字符串的指针。 如果在服务器上存在的文件的多个视图，此参数指定要打开的文件视图。 如果`pstrView`是**NULL**，使用默认文件视图。  
  
 `dwContext`  
 所打开的文件上下文 ID。 请参阅**备注**有关详细信息`dwContext`。  
  
### <a name="return-value"></a>返回值  
 指向的指针[CGopherFile](../../mfc/reference/cgopherfile-class.md)要打开的对象。  
  
### <a name="remarks"></a>备注  
 重写`dwContext`默认可为你选择的值设置的上下文标识符。 上下文标识符是与此特定操作的关联`CGopherConnection`对象由其[CInternetSession](../../mfc/reference/cinternetsession-class.md)对象。 值返回到[CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)以提供有关用于标识的操作的状态。 请参阅文章[Internet 前几个步骤： WinInet](../../mfc/wininet-basics.md)有关的上下文标识符的详细信息。  
  
## <a name="see-also"></a>请参阅  
 [CInternetConnection 类](../../mfc/reference/cinternetconnection-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CFtpConnection 类](../../mfc/reference/cftpconnection-class.md)   
 [CHttpConnection 类](../../mfc/reference/chttpconnection-class.md)   
 [CInternetConnection 类](../../mfc/reference/cinternetconnection-class.md)   
 [CGopherLocator 类](../../mfc/reference/cgopherlocator-class.md)   
 [CGopherFile 类](../../mfc/reference/cgopherfile-class.md)   
 [CInternetSession 类](../../mfc/reference/cinternetsession-class.md)
