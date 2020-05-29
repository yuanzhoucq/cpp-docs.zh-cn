---
title: CGopherLocator 类
ms.date: 11/04/2016
f1_keywords:
- CGopherLocator
- AFXINET/CGopherLocator
- AFXINET/CGopherLocator::CGopherLocator
- AFXINET/CGopherLocator::GetLocatorType
helpviewer_keywords:
- CGopherLocator [MFC], CGopherLocator
- CGopherLocator [MFC], GetLocatorType
ms.assetid: 6fcc015f-5ae6-4959-b936-858634c71019
ms.openlocfilehash: d23ef3dad68c62e74ec64454953ca372b8c31114
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373669"
---
# <a name="cgopherlocator-class"></a>CGopherLocator 类

从 gopher 服务器获取 gopher"定位器"，确定定位器的类型，并使定位器可供[CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)使用。

> [!NOTE]
> 类`CGopherConnection` `CGopherFile`、 `CGopherFileFind`、`CGopherLocator`及其成员已被弃用，因为它们在 Windows XP 平台上不工作，但它们将继续在较早的平台上工作。

## <a name="syntax"></a>语法

```
class CGopherLocator : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CGopher定位器：：CGopher定位器](#cgopherlocator)|构造 `CGopherLocator` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CGopher定位器：：获取定位器类型](#getlocatortype)|解析 gopher 定位器并确定其属性。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CGopher定位器：：操作员LPCTSTR](#operator_lpctstr)|直接访问作为 C 样式`CGopherLocator`字符串存储在对象中的字符。|

## <a name="remarks"></a>备注

应用程序必须先获取 gopher 服务器的定位器，然后才能从该服务器检索信息。 一旦它具有定位器，它必须将定位器视为不透明标记。

每个 gopher 定位器都有确定找到的文件或服务器类型的属性。 有关 gopher 定位器类型的列表，请参阅[GetLocatorType。](#getlocatortype)

应用程序通常使用定位器调用[CGopherFileFind：：FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile)检索特定信息。

要了解有关如何`CGopherLocator`与其他 MFC Internet 类合作，请参阅[WinInet](../../mfc/win32-internet-extensions-wininet.md)的 Internet 编程文章。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CGopherLocator`

## <a name="requirements"></a>要求

**标题：** afxinet.h

## <a name="cgopherlocatorcgopherlocator"></a><a name="cgopherlocator"></a>CGopher定位器：：CGopher定位器

调用此成员函数以创建对象`CGopherLocator`。

```
CGopherLocator(const CGopherLocator& ref);
```

### <a name="parameters"></a>参数

*ref*<br/>
对常量`CGopherLocator`对象的引用。

### <a name="remarks"></a>备注

您从不直接创建`CGopherLocator`对象。 相反，调用[CGopherConnection：：创建定位器](../../mfc/reference/cgopherconnection-class.md#createlocator)以创建并返回指向`CGopherLocator`对象的指针。

## <a name="cgopherlocatorgetlocatortype"></a><a name="getlocatortype"></a>CGopher定位器：：获取定位器类型

调用此成员函数获取定位器类型。

```
BOOL GetLocatorType(DWORD& dwRef) const;
```

### <a name="parameters"></a>参数

*德夫里夫*<br/>
对将接收定位器类型的 DWORD 的引用。 有关定位器类型表，请参阅**备注**。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。 如果调用失败，可能会调用 Win32 函数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以确定错误的原因。

### <a name="remarks"></a>备注

可能的类型如下：

|“值”|含义|
|-----------|-------------|
|GOPHER_TYPE_TEXT_FILE|ASCII 文本文件。|
|GOPHER_TYPE_DIRECTORY|其他 Gopher 项的目录。|
|GOPHER_TYPE_CSO|CSO 电话簿服务器。|
|GOPHER_TYPE_ERROR|指示错误条件。|
|GOPHER_TYPE_MAC_BINHEX|BINHEX 格式的 Macintosh 文件。|
|GOPHER_TYPE_DOS_ARCHIVE|DOS 存档文件。|
|GOPHER_TYPE_UNIX_UUENCODED|UUENCODED 文件。|
|GOPHER_TYPE_INDEX_SERVER|索引服务器。|
|GOPHER_TYPE_TELNET|电话网服务器。|
|GOPHER_TYPE_BINARY|二进制文件。|
|GOPHER_TYPE_REDUNDANT|复制的服务器。 中包含的信息是主服务器的重复项。 主服务器是最后一个没有GOPHER_TYPE_REDUNDANT类型的目录条目。|
|GOPHER_TYPE_TN3270|TN3270 服务器。|
|GOPHER_TYPE_GIF|GIF 图形文件。|
|GOPHER_TYPE_IMAGE|图像文件。|
|GOPHER_TYPE_BITMAP|位图文件。|
|GOPHER_TYPE_MOVIE|影片文件。|
|GOPHER_TYPE_SOUND|声音文件。|
|GOPHER_TYPE_HTML|一个 HTML 文档。|
|GOPHER_TYPE_PDF|PDF 文件。|
|GOPHER_TYPE_CALENDAR|日历文件。|
|GOPHER_TYPE_INLINE|内联文件。|
|GOPHER_TYPE_UNKNOWN|项类型未知。|
|GOPHER_TYPE_ASK|问+项目。|
|GOPHER_TYPE_GOPHER_PLUS|戈弗斯*项目。|

## <a name="cgopherlocatoroperator-lpctstr"></a><a name="operator_lpctstr"></a>CGopher定位器：：操作员LPCTSTR

此有用的强制转换运算符提供了访问`CGopherLocator`对象中包含的空端接 C 字符串的有效方法。

```
operator LPCTSTR () const;
```

### <a name="return-value"></a>返回值

指向字符串数据的字符指针。

### <a name="remarks"></a>备注

不复制任何字符;仅返回指针。

## <a name="see-also"></a>另请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CGopher文件查找类](../../mfc/reference/cgopherfilefind-class.md)
