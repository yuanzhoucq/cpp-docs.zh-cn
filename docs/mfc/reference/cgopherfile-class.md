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
ms.openlocfilehash: e157a4509fe30b814a1834690a675906ac82afe7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373694"
---
# <a name="cgopherfile-class"></a>CGopherFile 类

提供查找和读取 Gopher 服务器上文件的功能。

> [!NOTE]
> 类`CGopherConnection` `CGopherFile`、 `CGopherFileFind`、`CGopherLocator`及其成员已被弃用，因为它们在 Windows XP 平台上不工作，但它们将继续在较早的平台上工作。

## <a name="syntax"></a>语法

```
class CGopherFile : public CInternetFile
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|说明|
|----------|-----------------|
|[CGopher文件：CGopher文件](#cgopherfile)|构造 `CGopherFile` 对象。|

## <a name="remarks"></a>备注

gopher 服务不允许用户将数据写入 gopher 文件，因为此服务主要用作菜单驱动的用于查找信息的界面。 成员`CGopherFile`函数`Write`、`WriteString`和`Flush`未为`CGopherFile`实现 。 在`CGopherFile`对象上调用这些函数，返回[CNot 支持异常](../../mfc/reference/cnotsupportedexception-class.md)。

要了解有关如何`CGopherFile`与其他 MFC Internet 类合作，请参阅[WinInet](../../mfc/win32-internet-extensions-wininet.md)的 Internet 编程文章。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

[C互联网文件](../../mfc/reference/cinternetfile-class.md)

`CGopherFile`

## <a name="requirements"></a>要求

**标题：** afxinet.h

## <a name="cgopherfilecgopherfile"></a><a name="cgopherfile"></a>CGopher文件：CGopher文件

调用此成员函数以构造对象`CGopherFile`。

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
HINTERNET 文件的句柄。

*参考定位器*<br/>
对[CGopher 定位器对象的引用](../../mfc/reference/cgopherlocator-class.md)。

*p连接*<br/>
指向[Gopher 连接](../../mfc/reference/cgopherconnection-class.md)对象的指针。

*h 会话*<br/>
当前 Internet 会话的句柄。

*pstrLocator*<br/>
指向用于定位 gopher 服务器的字符串的指针。 有关 gopher 定位器的详细信息，请参阅[Gopher 会话](cgopherlocator-class.md)。

*德洛克伦*<br/>
包含*pstrLocator*中的字节数的 DWORD。

*dwContext*<br/>
指向要打开的文件的上下文标识符的指针。

### <a name="remarks"></a>备注

您需要一个`CGopherFile`对象在 gopher Internet 会话期间从文件中读取。

您从不直接创建`CGopherFile`对象。 相反，调用[CGopher 连接：：打开文件](../../mfc/reference/cgopherconnection-class.md#openfile)以在 gopher 服务器上打开文件。

## <a name="see-also"></a>另请参阅

[CInternetFile 类](../../mfc/reference/cinternetfile-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CInternetFile 类](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherLocator 类](../../mfc/reference/cgopherlocator-class.md)<br/>
[CGopher文件查找类](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CGopher 连接类](../../mfc/reference/cgopherconnection-class.md)
