---
title: "Internet URL 分析全局变量 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.isapi
dev_langs:
- C++
helpviewer_keywords:
- parsing, URLs
- URLs, parsing
ms.assetid: 46c6384f-e4a6-4dbd-9196-219c19040ec5
caps.latest.revision: 14
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
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 3aec259acae2f5e9c9b65ac4e5c898ca57ff3d52
ms.lasthandoff: 02/24/2017

---
# <a name="internet-url-parsing-globals"></a>Internet URL 分析全局函数
当某个客户端发送查询到 Internet 服务器时，您可以使用 URL 分析全局变量之一提取有关此客户端的信息。  
  
### <a name="internet-url-parsing-globals"></a>Internet URL 分析全局函数  
  
|||  
|-|-|  
|[AfxParseURL](#afxparseurl)|分析 URL 字符串并返回服务类型及其组件。|  
|[AfxParseURLEx](#afxparseurlex)|分析 URL 字符串并返回服务类型及其组件，这与提供用户名和密码一样。|  
  
##  <a name="a-nameafxparseurla--afxparseurl"></a><a name="afxparseurl"></a>AfxParseURL  
 使用在此全局[cinternetsession:: Openurl](../../mfc/reference/cinternetsession-class.md#openurl)。  
  
```   
BOOL AFXAPI AfxParseURL(
    LPCTSTR pstrURL,  
    DWORD& dwServiceType,  
    CString& strServer,  
    CString& strObject,  
    INTERNET_PORT& nPort); 
```  
  
### <a name="parameters"></a>参数  
 *pstrURL*  
 指向包含要分析的 URL 的字符串的指针。  
  
 `dwServiceType`  
 指示 Internet 服务的类型。 可能的值如下：  
  
-   AFX_INET_SERVICE_FTP  
  
-   AFX_INET_SERVICE_HTTP  
  
-   AFX_INET_SERVICE_HTTPS  
  
-   AFX_INET_SERVICE_GOPHER  
  
-   AFX_INET_SERVICE_FILE  
  
-   AFX_INET_SERVICE_MAILTO  
  
-   AFX_INET_SERVICE_NEWS  
  
-   AFX_INET_SERVICE_NNTP  
  
-   AFX_INET_SERVICE_TELNET  
  
-   AFX_INET_SERVICE_WAIS  
  
-   AFX_INET_SERVICE_MID  
  
-   AFX_INET_SERVICE_CID  
  
-   AFX_INET_SERVICE_PROSPERO  
  
-   AFX_INET_SERVICE_AFS  
  
-   AFX_INET_SERVICE_UNK  
  
 `strServer`  
 以下服务类型的 URL 的第一个段。  
  
 `strObject`  
 URL 指代的对象 （可能为空）。  
  
 `nPort`  
 从服务器或对象部分 URL，确定是否存在。  
  
### <a name="return-value"></a>返回值  
 如果已成功分析该 URL; 则为非否则为 0，如果它为空或不包含已知的 Internet 服务类型。  
  
### <a name="remarks"></a>备注  
 它分析 URL 字符串并返回服务及其组件的类型。  
  
 例如，`AfxParseURL`分析窗体的 Url **service://server/dir/dir/object.ext:port** ，并返回其组件存储，如下所示︰  
  
 `strServer`= ="server"  
  
 `strObject`= ="/ dir/dir/object/object.ext"  
  
 `nPort`= = #port  
  
 `dwServiceType`= = #service  
  
> [!NOTE]
>  若要调用此函数，您的项目必须包括 AFXINET。H。  
  
### <a name="requirements"></a>要求  
  **标头**afxinet.h  
  
##  <a name="a-nameafxparseurlexa--afxparseurlex"></a><a name="afxparseurlex"></a>AfxParseURLEx  
 此全局函数是扩展的版本[AfxParseURL](#afxparseurl)并可用于[cinternetsession:: Openurl](../../mfc/reference/cinternetsession-class.md#openurl)。  
  
```   
BOOL AFXAPI AfxParseURLEx(
    LPCTSTR pstrURL,  
    DWORD& dwServiceType,  
    CString& strServer,  
    CString& strObject,  
    INTERNET_PORT& nPort,  
    CString& strUsername,  
    CString& strPassword,  
    DWORD dwFlags = 0); 
```  
  
### <a name="parameters"></a>参数  
 *pstrURL*  
 指向包含要分析的 URL 的字符串的指针。  
  
 `dwServiceType`  
 指示 Internet 服务的类型。 可能的值如下：  
  
-   AFX_INET_SERVICE_FTP  
  
-   AFX_INET_SERVICE_HTTP  
  
-   AFX_INET_SERVICE_HTTPS  
  
-   AFX_INET_SERVICE_GOPHER  
  
-   AFX_INET_SERVICE_FILE  
  
-   AFX_INET_SERVICE_MAILTO  
  
-   AFX_INET_SERVICE_NEWS  
  
-   AFX_INET_SERVICE_NNTP  
  
-   AFX_INET_SERVICE_TELNET  
  
-   AFX_INET_SERVICE_WAIS  
  
-   AFX_INET_SERVICE_MID  
  
-   AFX_INET_SERVICE_CID  
  
-   AFX_INET_SERVICE_PROSPERO  
  
-   AFX_INET_SERVICE_AFS  
  
-   AFX_INET_SERVICE_UNK  
  
 `strServer`  
 以下服务类型的 URL 的第一个段。  
  
 `strObject`  
 URL 指代的对象 （可能为空）。  
  
 `nPort`  
 从服务器或对象部分 URL，确定是否存在。  
  
 *strUsername*  
 对引用`CString`对象，其中包含用户的名称。  
  
 `strPassword`  
 对引用`CString`对象，其中包含用户的密码。  
  
 `dwFlags`  
 控制如何分析的 URL 的标志。 可以是以下值的组合︰  
  
|值|含义|  
|-----------|-------------|  
|**ICU_DECODE**|将 %xx 转义序列转换为字符。|  
|**ICU_NO_ENCODE**|不转换不安全的字符进行转义序列。|  
|**ICU_NO_META**|不要删除元序列 （如"\"。 和"\."）从该 URL。|  
|**ICU_ENCODE_SPACES_ONLY**|对空格进行编码。|  
|**ICU_BROWSER_MODE**|不进行编码或解码字符后 '#' 或 '，且不要删除尾随空格后。 如果未指定此值，整个 URL 编码，并且会删除尾随空格。|  
  
 如果您使用 MFC 默认情况下，这不是任何标志，该函数将所有不安全的字符和 meta 序列 (如\\。，\...，和\\...) 进行转义序列。  
  
### <a name="return-value"></a>返回值  
 如果已成功分析该 URL; 则为非否则为 0，如果它为空或不包含已知的 Internet 服务类型。  
  
### <a name="remarks"></a>备注  
 它分析 URL 字符串并返回的一种服务及其组件，以及提供用户的名称和密码。 这些标志指示如何不安全的字符进行处理。  
  
> [!NOTE]
>  若要调用此函数，您的项目必须包括 AFXINET。H。  

### <a name="requirements"></a>要求  
  **标头**afxinet.h  
    
## <a name="see-also"></a>另请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)

