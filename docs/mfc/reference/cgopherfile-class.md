---
title: CGopherFile 类
ms.date: 11/04/2016
f1_keywords:
- CGopherFile
- AFXINET/CGopherFile
- AFXINET/CGopherFile::CGopherFile
helpviewer_keywords:
- CGopherFile [MFC], CGopherFile
ms.assetid: 3ca9898f-8cdb-4495-bbde-46d40100feda
ms.openlocfilehash: 9e5fbdcd14c0f988e894718f357d40e4b238c7c7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658193"
---
# <a name="cgopherfile-class"></a>CGopherFile 类

提供查找和读取 Gopher 服务器上文件的功能。

> [!NOTE]
>  类`CGopherConnection`， `CGopherFile`， `CGopherFileFind`，`CGopherLocator`和它们的成员具有已弃用，因为它们不能在 Windows XP 平台上，但它们将继续在早期版本的平台上工作。

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

Gopher 服务不允许用户将数据写入到 gopher 文件，因为此服务主要用作菜单驱动的界面，用于查找信息。 `CGopherFile`成员函数`Write`， `WriteString`，和`Flush`未实现的`CGopherFile`。 在调用这些函数`CGopherFile`对象，返回[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。

若要详细了解如何`CGopherFile`适用于其他 MFC Internet 类，请参阅文章[Internet 编程与 WinInet](../../mfc/win32-internet-extensions-wininet.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

[CInternetFile](../../mfc/reference/cinternetfile-class.md)

`CGopherFile`

## <a name="requirements"></a>要求

**标头：** afxinet.h

##  <a name="cgopherfile"></a>  CGopherFile::CGopherFile

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

*hFile*<br/>
HINTERNET 文件句柄。

*refLocator*<br/>
对引用[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)对象。

*pConnection*<br/>
一个指向[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)对象。

*hSession*<br/>
当前 Internet 会话句柄。

*pstrLocator*<br/>
指向用来定位 gopher 服务器的字符串的指针。 请参阅[Gopher 会话](cgopherlocator-class.md)有关 gopher 定位符的详细信息。

*dwLocLen*<br/>
包含中的字节数的 DWORD *pstrLocator*。

*dwContext*<br/>
指向所打开的文件的上下文标识符的指针。

### <a name="remarks"></a>备注

您需要`CGopherFile`对象，以便从文件读取 gopher Internet 会话期间。

永远不会创建`CGopherFile`直接对象。 改为调用[CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile)打开 gopher 服务器上的文件。

## <a name="see-also"></a>请参阅

[CInternetFile 类](../../mfc/reference/cinternetfile-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CInternetFile 类](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherLocator 类](../../mfc/reference/cgopherlocator-class.md)<br/>
[CGopherFileFind 类](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CGopherConnection 类](../../mfc/reference/cgopherconnection-class.md)
