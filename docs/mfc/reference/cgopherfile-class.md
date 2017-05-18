---
title: "CGopherFile 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CGopherFile
- AFXINET/CGopherFile
- AFXINET/CGopherFile::CGopherFile
dev_langs:
- C++
helpviewer_keywords:
- gopher protocol files
- Internet, gopher
- CGopherFile class
ms.assetid: 3ca9898f-8cdb-4495-bbde-46d40100feda
caps.latest.revision: 23
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 40c1e385d0f58095c2aa79cc23168fc00f48ed9b
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cgopherfile-class"></a>CGopherFile 类
提供查找和读取 Gopher 服务器上文件的功能。  
  
> [!NOTE]
>  这些类`CGopherConnection`， `CGopherFile`， `CGopherFileFind`，`CGopherLocator`和其成员已被否决，因为它们不能在 Windows XP 平台上，但它们将继续在较早的平台上工作。  
  
## <a name="syntax"></a>语法  
  
```  
class CGopherFile : public CInternetFile  
```  
  
## <a name="members"></a>成员  
  
### <a name="protected-constructors"></a>受保护的构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CGopherFile::CGopherFile](#cgopherfile)|构造 `CGopherFile` 对象。|  
  
## <a name="remarks"></a>备注  
 Gopher 服务不允许用户对 gopher 文件写入数据，因为此服务主要用作查找信息的菜单驱动式界面。 `CGopherFile`成员函数**编写**， `WriteString`，和`Flush`未向实施`CGopherFile`。 在调用这些函数`CGopherFile`对象返回[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。  
  
 若要了解有关如何`CGopherFile`工作与其他 MFC Internet 类，请参阅文章[Internet 编程与 WinInet](../../mfc/win32-internet-extensions-wininet.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [CStdioFile](../../mfc/reference/cstdiofile-class.md)  
  
 [CInternetFile](../../mfc/reference/cinternetfile-class.md)  
  
 `CGopherFile`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxinet.h  
  
##  <a name="cgopherfile"></a>CGopherFile::CGopherFile  
 调用此成员函数来构造`CGopherFile`对象。  
  
```  
CGopherFile(
    HINTERNET hFile,  
    CGopherLocator& refLocator,  
    CGopherConnection* pConnection);

 
CGopherFile(
    HINTERNET hFile,  
    HINTERNET hSession,  
    LPCTSTR pstrLocator,  
    DWORD dwLocLen,  
    DWORD_PTR dwContext);
```  
  
### <a name="parameters"></a>参数  
 `hFile`  
 句柄`HINTERNET`文件。  
  
 `refLocator`  
 对引用[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)对象。  
  
 `pConnection`  
 一个指向[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)对象。  
  
 `hSession`  
 当前 Internet 会话句柄。  
  
 `pstrLocator`  
 指向用来定位 gopher 服务器的字符串的指针。 请参阅[Gopher 会话](https://msdn.microsoft.com/library/24wz8xze.aspx)有关 gopher 定位符的详细信息。  
  
 *dwLocLen*  
 一个包含中的字节数的 dword 值`pstrLocator`。  
  
 `dwContext`  
 指向所打开的文件的上下文标识符的指针。  
  
### <a name="remarks"></a>备注  
 您需要`CGopherFile`对象，以便从文件读取 gopher Internet 会话期间。  
  
 切勿创建`CGopherFile`直接对象。 而应调用[CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile)若要打开 gopher 服务器上的文件。  
  
## <a name="see-also"></a>另请参阅  
 [CInternetFile 类](../../mfc/reference/cinternetfile-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CInternetFile 类](../../mfc/reference/cinternetfile-class.md)   
 [CGopherLocator 类](../../mfc/reference/cgopherlocator-class.md)   
 [CGopherFileFind 类](../../mfc/reference/cgopherfilefind-class.md)   
 [CGopherConnection 类](../../mfc/reference/cgopherconnection-class.md)

