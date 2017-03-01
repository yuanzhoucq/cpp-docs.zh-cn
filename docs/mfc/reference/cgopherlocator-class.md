---
title: "CGopherLocator 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CGopherLocator
dev_langs:
- C++
helpviewer_keywords:
- gopher locator
- CGopherLocator class
- Internet, gopher searches
ms.assetid: 6fcc015f-5ae6-4959-b936-858634c71019
caps.latest.revision: 22
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
ms.openlocfilehash: c5c9b862714d046bc81a49dda27fd5fc062b9ba8
ms.lasthandoff: 02/24/2017

---
# <a name="cgopherlocator-class"></a>CGopherLocator 类
从 gopher 服务器获取 gopher"定位器"，确定定位器的类型，并使定位器可用于[CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)。  
  
> [!NOTE]
>  这些类`CGopherConnection`， `CGopherFile`， `CGopherFileFind`，`CGopherLocator`和其成员已被否决，因为它们不能在 Windows XP 平台上，但它们将继续在较早的平台上工作。  
  
## <a name="syntax"></a>语法  
  
```  
class CGopherLocator : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CGopherLocator::CGopherLocator](#cgopherlocator)|构造 `CGopherLocator` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CGopherLocator::GetLocatorType](#getlocatortype)|分析 gopher 定位符并确定其属性。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CGopherLocator::operator lpctstr 来](#operator_lpctstr)|直接访问存储在字符`CGopherLocator`对象用作 C 样式字符串。|  
  
## <a name="remarks"></a>备注  
 应用程序必须获取 gopher 服务器的定位符，然后它才能从该服务器中检索信息。 定位符后，它必须将定位符视为不透明的令牌。  
  
 每个 gopher 定位符具有确定的文件服务器或服务器发现的类型的属性。 请参阅[GetLocatorType](#getlocatortype)有关 gopher 定位符类型的列表。  
  
 应用程序通常使用该定位符对的调用进行[CGopherFileFind::FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile)来检索特定的信息。  
  
 若要了解有关如何`CGopherLocator`工作与其他 MFC Internet 类，请参阅文章[Internet 编程与 WinInet](../../mfc/win32-internet-extensions-wininet.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CGopherLocator`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxinet.h  
  
##  <a name="a-namecgopherlocatora--cgopherlocatorcgopherlocator"></a><a name="cgopherlocator"></a>CGopherLocator::CGopherLocator  
 此成员函数调用来创建`CGopherLocator`对象。  
  
```  
CGopherLocator(const CGopherLocator& ref);
```  
  
### <a name="parameters"></a>参数  
 `ref`  
 与某个常量引用`CGopherLocator`对象。  
  
### <a name="remarks"></a>备注  
 切勿创建`CGopherLocator`直接对象。 而应调用[CGopherConnection::CreateLocator](../../mfc/reference/cgopherconnection-class.md#createlocator)创建并返回一个指向`CGopherLocator`对象。  
  
##  <a name="a-namegetlocatortypea--cgopherlocatorgetlocatortype"></a><a name="getlocatortype"></a>CGopherLocator::GetLocatorType  
 调用此成员函数可获取定位符类型。  
  
```  
BOOL GetLocatorType(DWORD& dwRef) const;  
```  
  
### <a name="parameters"></a>参数  
 *dwRef*  
 对引用`DWORD`中将接收定位符类型。 请参阅**备注**定位符类型的表。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 如果调用失败，Win32 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)可能调用以确定错误的原因。  
  
### <a name="remarks"></a>备注  
 可能的类型如下所示︰  
  
|值|含义|  
|-----------|-------------|  
|GOPHER_TYPE_TEXT_FILE|ASCII 文本文件。|  
|GOPHER_TYPE_DIRECTORY|Gopher 了附加项目目录。|  
|GOPHER_TYPE_CSO|CSO 的通讯簿服务器。|  
|GOPHER_TYPE_ERROR|指示错误条件。|  
|GOPHER_TYPE_MAC_BINHEX|一个 Macintosh BINHEX 格式文件。|  
|GOPHER_TYPE_DOS_ARCHIVE|一个 DOS 的存档文件。|  
|GOPHER_TYPE_UNIX_UUENCODED|一个容易被解码的文件。|  
|GOPHER_TYPE_INDEX_SERVER|索引服务器。|  
|GOPHER_TYPE_TELNET|Telnet 服务器。|  
|GOPHER_TYPE_BINARY|一个二进制文件。|  
|GOPHER_TYPE_REDUNDANT|重复的服务器。 中包含的信息是主服务器的副本。 主服务器是最后一个目录条目中没有 GOPHER_TYPE_REDUNDANT 类型。|  
|GOPHER_TYPE_TN3270|TN3270 服务器。|  
|GOPHER_TYPE_GIF|GIF 图形文件。|  
|GOPHER_TYPE_IMAGE|图像文件。|  
|GOPHER_TYPE_BITMAP|位图文件。|  
|GOPHER_TYPE_MOVIE|电影文件。|  
|GOPHER_TYPE_SOUND|声音文件。|  
|GOPHER_TYPE_HTML|一个 HTML 文档。|  
|GOPHER_TYPE_PDF|PDF 文件格式。|  
|GOPHER_TYPE_CALENDAR|一种日历文件。|  
|GOPHER_TYPE_INLINE|内联文件。|  
|GOPHER_TYPE_UNKNOWN|项类型是未知的。|  
|GOPHER_TYPE_ASK|询问 + 项。|  
|GOPHER_TYPE_GOPHER_PLUS|Gopher + 项。|  
  
##  <a name="a-nameoperatorlpctstra--cgopherlocatoroperator-lpctstr"></a><a name="operator_lpctstr"></a>CGopherLocator::operator lpctstr 来  
 这非常有用的强制转换运算符提供了一种有效的方法来访问的以 null 结尾的 C 字符串中包含`CGopherLocator`对象。  
  
```  
operator LPCTSTR () const;  
```  
  
### <a name="return-value"></a>返回值  
 指向字符串的数据的字符指针。  
  
### <a name="remarks"></a>备注  
 没有字符被复制;仅一个指针，则返回。  
  
## <a name="see-also"></a>另请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CGopherFileFind 类](../../mfc/reference/cgopherfilefind-class.md)

