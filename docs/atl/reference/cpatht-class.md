---
title: CPathT 类
ms.date: 03/27/2019
f1_keywords:
- CPathT
- ATLPATH/ATL::CPathT
- ATLPATH/ATL::CPathT::PCXSTR
- ATLPATH/ATL::CPathT::PXSTR
- ATLPATH/ATL::CPathT::XCHAR
- ATLPATH/ATL::CPathT::CPathT
- ATLPATH/ATL::CPathT::AddBackslash
- ATLPATH/ATL::CPathT::AddExtension
- ATLPATH/ATL::CPathT::Append
- ATLPATH/ATL::CPathT::BuildRoot
- ATLPATH/ATL::CPathT::Canonicalize
- ATLPATH/ATL::CPathT::Combine
- ATLPATH/ATL::CPathT::CommonPrefix
- ATLPATH/ATL::CPathT::CompactPath
- ATLPATH/ATL::CPathT::CompactPathEx
- ATLPATH/ATL::CPathT::FileExists
- ATLPATH/ATL::CPathT::FindExtension
- ATLPATH/ATL::CPathT::FindFileName
- ATLPATH/ATL::CPathT::GetDriveNumber
- ATLPATH/ATL::CPathT::GetExtension
- ATLPATH/ATL::CPathT::IsDirectory
- ATLPATH/ATL::CPathT::IsFileSpec
- ATLPATH/ATL::CPathT::IsPrefix
- ATLPATH/ATL::CPathT::IsRelative
- ATLPATH/ATL::CPathT::IsRoot
- ATLPATH/ATL::CPathT::IsSameRoot
- ATLPATH/ATL::CPathT::IsUNC
- ATLPATH/ATL::CPathT::IsUNCServer
- ATLPATH/ATL::CPathT::IsUNCServerShare
- ATLPATH/ATL::CPathT::MakePretty
- ATLPATH/ATL::CPathT::MatchSpec
- ATLPATH/ATL::CPathT::QuoteSpaces
- ATLPATH/ATL::CPathT::RelativePathTo
- ATLPATH/ATL::CPathT::RemoveArgs
- ATLPATH/ATL::CPathT::RemoveBackslash
- ATLPATH/ATL::CPathT::RemoveBlanks
- ATLPATH/ATL::CPathT::RemoveExtension
- ATLPATH/ATL::CPathT::RemoveFileSpec
- ATLPATH/ATL::CPathT::RenameExtension
- ATLPATH/ATL::CPathT::SkipRoot
- ATLPATH/ATL::CPathT::StripPath
- ATLPATH/ATL::CPathT::StripToRoot
- ATLPATH/ATL::CPathT::UnquoteSpaces
- ATLPATH/ATL::CPathT::m_strPath
helpviewer_keywords:
- CPathT class
ms.assetid: eba4137d-1fd2-4b44-a2e1-0944db64df3c
ms.openlocfilehash: c10b854ae5c2d7167a067675b1391be24b6a8122
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746593"
---
# <a name="cpatht-class"></a>CPathT 类

此类表示路径。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template <typename StringType>
class CPathT
```

#### <a name="parameters"></a>参数

*StringType*<br/>
用于路径的 ATL/MFC 字符串类（请参阅[CStringT）。](../../atl-mfc-shared/reference/cstringt-class.md)

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|[CPathT：:PCXSTR](#pcxstr)|常量字符串类型。|
|[CPathT：:PXSTR](#pxstr)|一种字符串类型。|
|[CPathT：XCHAR](#xchar)|一个字符类型。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CPathT：CPathT](#cpatht)|路径的构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CPathT：：添加反斜杠](#addbackslash)|调用此方法向字符串的末尾添加反斜杠，以创建路径的正确语法。|
|[CPathT：：添加扩展](#addextension)|调用此方法以向路径添加文件扩展名。|
|[CPathT：：附加](#append)|调用此方法以将字符串追加到当前路径。|
|[CPathT：：构建根](#buildroot)|调用此方法从给定驱动器号创建根路径。|
|[CPathT：规范化](#canonicalize)|调用此方法将路径转换为规范形式。|
|[CPathT：：合并](#combine)|调用此方法将表示目录名称的字符串和表示文件路径名称的字符串串联到一个路径中。|
|[CPathT：：通用前缀](#commonprefix)|调用此方法以确定指定的路径是否与当前路径共享公共前缀。|
|[CPathT：：紧凑路径](#compactpath)|调用此方法可截取文件路径，方法是将路径组件替换为椭圆，以适合给定像素宽度。|
|[CPathT：：压缩路径](#compactpathex)|调用此方法，通过将路径组件替换为椭圆来截取文件路径以适合给定数量的字符。|
|[CPathT：文件存在](#fileexists)|调用此方法以检查此路径名称下的文件是否存在。|
|[CPathT：：查找扩展](#findextension)|调用此方法以查找路径中文件扩展名的位置。|
|[CPathT：：查找文件名](#findfilename)|调用此方法以查找文件名在路径中的位置。|
|[CPathT：获取驱动器号码](#getdrivenumber)|调用此方法以在"A"到"Z"范围内搜索驱动器号路径并返回相应的驱动器号。|
|[CPathT：获取扩展](#getextension)|调用此方法从路径获取文件扩展名。|
|[CPathT：是目录](#isdirectory)|调用此方法以检查路径是否为有效目录。|
|[CPathT：是文件规格](#isfilespec)|调用此方法以搜索路径以查找任何路径分隔字符（例如，"："或''）。\\ 如果不存在路径分隔字符，则路径被视为文件规格路径。|
|[CPathT：isprefix](#isprefix)|调用此方法以确定路径是否包含*pszPrefix*传递的类型的有效前缀。|
|[CPathT：相对](#isrelative)|调用此方法以确定路径是否相对。|
|[CPathT：是根](#isroot)|调用此方法以确定路径是否为目录根。|
|[CPathT：：IsSameRoot](#issameroot)|调用此方法以确定另一个路径是否具有与当前路径的通用根组件。|
|[CPathT：ISUNC](#isunc)|调用此方法以确定路径是否是服务器和共享的有效 UNC（通用命名约定）路径。|
|[CPathT：isUNCServer](#isuncserver)|调用此方法以确定路径是否仅是服务器的有效 UNC（通用命名约定）路径。|
|[CPathT：isUNCServer共享](#isuncservershare)|调用此方法以确定路径是否是有效的 UNC（通用命名约定）共享路径、\\\ *服务器*\ *共享*。|
|[CPathT：：制作漂亮](#makepretty)|调用此方法可将路径转换为所有小写字符，以使路径的外观一致。|
|[CPathT：：匹配规格](#matchspec)|调用此方法以搜索包含通配符匹配类型的字符串的路径。|
|[CPathT：：报价空间](#quotespaces)|如果路径包含任何空格，则调用此方法以引号括上路径。|
|[CPatht：：相对路径](#relativepathto)|调用此方法以创建从一个文件或文件夹到另一个文件或文件夹的相对路径。|
|[CPathT：：删除阿格](#removeargs)|调用此方法从路径中删除任何命令行参数。|
|[CPathT：：删除反斜杠](#removebackslash)|调用此方法以从路径中删除尾随反斜杠。|
|[CPathT：：删除空白](#removeblanks)|调用此方法从路径中删除所有前导空格和尾随空格。|
|[CPathT：：删除扩展](#removeextension)|调用此方法以从路径中删除文件扩展名（如果有）。|
|[CPathT：：删除文件规格](#removefilespec)|调用此方法以从路径中删除尾随文件名和反斜杠（如果有）。|
|[CPathT：：重命名扩展](#renameextension)|调用此方法以将路径中的文件名扩展名替换为新的扩展名。 如果文件名不包含扩展名，则扩展名将附加到字符串的末尾。|
|[CPathT：：跳过根](#skiproot)|调用此方法以分析路径，忽略驱动器号或 UNC 服务器/共享路径部件。|
|[CPathT：：条带路径](#strippath)|调用此方法以删除完全限定的路径和文件名的路径部分。|
|[CPatht：：条纹根](#striptoroot)|调用此方法以删除路径的所有部分，但根信息除外。|
|[CPathT：无引号空格](#unquotespaces)|调用此方法以从路径的开头和结尾删除引号。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CPathT：：运算符 const 字符串类型&](#operator_const_stringtype_amp)|此运算符允许将对象视为字符串。|
|[CPathT：：操作员 CPathT：:PCXSTR](#operator_cpatht__pcxstr)|此运算符允许将对象视为字符串。|
|[CPathT：：运算符字符串类型&](#operator_stringtype_amp)|此运算符允许将对象视为字符串。|
|[CPathT：：操作员 |](#operator_add_eq)|此运算符将字符串追加到路径中。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CPathT：m_strPath](#m_strpath)|路径。|

## <a name="remarks"></a>备注

`CPath``CPathA`，并且`CPathW`是定义的实例化，`CPathT`如下所示：

`typedef CPathT< CString > CPath;`

`typedef CPathT< CStringA > CPathA;`

`typedef CPathT< CStringW > CPathW;`

## <a name="requirements"></a>要求

**标题：** atlpath.h

## <a name="cpathtaddbackslash"></a><a name="addbackslash"></a>CPathT：：添加反斜杠

调用此方法向字符串的末尾添加反斜杠，以创建路径的正确语法。 如果路径已具有尾随反斜杠，则不会添加反斜杠。

```cpp
void AddBackslash();
```

### <a name="remarks"></a>备注

有关详细信息，请参阅[路径添加回斜杠](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw)。

## <a name="cpathtaddextension"></a><a name="addextension"></a>CPathT：：添加扩展

调用此方法以向路径添加文件扩展名。

```
BOOL AddExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>参数

*psz 扩展*<br/>
要添加的文件扩展名。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅[路径添加扩展](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw)。

## <a name="cpathtappend"></a><a name="append"></a>CPathT：：附加

调用此方法以将字符串追加到当前路径。

```
BOOL Append(PCXSTR pszMore);
```

### <a name="parameters"></a>参数

*pszMore*<br/>
要追加的字符串。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅[路径应用](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw)。

## <a name="cpathtbuildroot"></a><a name="buildroot"></a>CPathT：：构建根

调用此方法从给定驱动器号创建根路径。

```cpp
void BuildRoot(int iDrive);
```

### <a name="parameters"></a>参数

*iDrive*<br/>
驱动器号（0 为 A：，1 表示 B：，等等）。

### <a name="remarks"></a>备注

有关详细信息，请参阅[路径构建根](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw)。

## <a name="cpathtcanonicalize"></a><a name="canonicalize"></a>CPathT：规范化

调用此方法将路径转换为规范形式。

```cpp
void Canonicalize();
```

### <a name="remarks"></a>备注

有关详细信息，请参阅[路径化](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew)。

## <a name="cpathtcombine"></a><a name="combine"></a>CPathT：：合并

调用此方法将表示目录名称的字符串和表示文件路径名称的字符串串联到一个路径中。

```cpp
void Combine(PCXSTR pszDir, PCXSTR  pszFile);
```

### <a name="parameters"></a>参数

*皮兹迪尔*<br/>
目录路径。

*pszFile*<br/>
文件路径。

### <a name="remarks"></a>备注

有关详细信息，请参阅[路径合并](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew)。

## <a name="cpathtcommonprefix"></a><a name="commonprefix"></a>CPathT：：通用前缀

调用此方法以确定指定的路径是否与当前路径共享公共前缀。

```
CPathT<StringType> CommonPrefix(PCXSTR pszOther);
```

### <a name="parameters"></a>参数

*pszOther*<br/>
要与当前路径进行比较的路径。

### <a name="return-value"></a>返回值

返回公共前缀。

### <a name="remarks"></a>备注

前缀是以下类型之一："C："，"."，"."，"."，"."."."."."."\\\\\\\\". 有关详细信息，请参阅[路径公共前缀](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw)。

## <a name="cpathtcompactpath"></a><a name="compactpath"></a>CPathT：：紧凑路径

调用此方法可截取文件路径，方法是将路径组件替换为椭圆，以适合给定像素宽度。

```
BOOL CompactPath(HDC hDC, UINT nWidth);
```

### <a name="parameters"></a>参数

*hDC*<br/>
用于字体指标的设备上下文。

*n 宽度*<br/>
字符串将强制拟合的宽度（以像素为单位）。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅[路径压缩路径](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw)。

## <a name="cpathtcompactpathex"></a><a name="compactpathex"></a>CPathT：：压缩路径

调用此方法，通过将路径组件替换为椭圆来截取文件路径以适合给定数量的字符。

```
BOOL CompactPathEx(UINT nMaxChars, DWORD dwFlags = 0);
```

### <a name="parameters"></a>参数

*nMaxChars*<br/>
新字符串中要包含的最大字符数，包括终止 NULL 字符。

dwFlags**<br/>
保留。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅[路径压缩路径Ex](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw)。

## <a name="cpathtcpatht"></a><a name="cpatht"></a>CPathT：CPathT

构造函数。

```
CPathT(PCXSTR pszPath);
CPathT(const CPathT<StringType>& path);
CPathT() throw();
```

### <a name="parameters"></a>参数

*pszPath*<br/>
指向路径字符串的指针。

*路径*<br/>
路径字符串。

## <a name="cpathtfileexists"></a><a name="fileexists"></a>CPathT：文件存在

调用此方法以检查此路径名称下的文件是否存在。

```
BOOL FileExists() const;
```

### <a name="return-value"></a>返回值

如果文件存在，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅[路径文件存在](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw)。

## <a name="cpathtfindextension"></a><a name="findextension"></a>CPathT：：查找扩展

调用此方法以查找路径中文件扩展名的位置。

```
int FindExtension() const;
```

### <a name="return-value"></a>返回值

返回扩展之前的"" 的位置。 如果未找到扩展，则返回 -1。

### <a name="remarks"></a>备注

有关详细信息，请参阅[路径查找扩展](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw)。

## <a name="cpathtfindfilename"></a><a name="findfilename"></a>CPathT：：查找文件名

调用此方法以查找文件名在路径中的位置。

```
int FindFileName() const;
```

### <a name="return-value"></a>返回值

返回文件名的位置。 如果未找到文件名，则返回 -1。

### <a name="remarks"></a>备注

有关详细信息，请参阅[路径查找文件名称](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)。

## <a name="cpathtgetdrivenumber"></a><a name="getdrivenumber"></a>CPathT：获取驱动器号码

调用此方法以在"A"到"Z"范围内搜索驱动器号路径并返回相应的驱动器号。

```
int GetDriveNumber() const;
```

### <a name="return-value"></a>返回值

如果路径具有驱动器号，则将驱动器号作为从 0 到 25 的整数（对应于"A"到"Z"）返回，否则为 -1。

### <a name="remarks"></a>备注

有关详细信息，请参阅[路径获取驱动器编号](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw)。

## <a name="cpathtgetextension"></a><a name="getextension"></a>CPathT：获取扩展

调用此方法从路径获取文件扩展名。

```
StringType GetExtension() const;
```

### <a name="return-value"></a>返回值

返回文件扩展名。

## <a name="cpathtisdirectory"></a><a name="isdirectory"></a>CPathT：是目录

调用此方法以检查路径是否为有效目录。

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>返回值

如果路径是目录，则返回非零值 （16），否则为 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅[PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw)。

## <a name="cpathtisfilespec"></a><a name="isfilespec"></a>CPathT：是文件规格

调用此方法以搜索路径以查找任何路径分隔字符（例如，"："或''）。\\ 如果不存在路径分隔字符，则路径被视为文件规格路径。

```
BOOL IsFileSpec() const;
```

### <a name="return-value"></a>返回值

如果路径中没有路径分隔字符，则返回 TRUE;如果存在路径分隔字符，则返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅[PathisFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw)。

## <a name="cpathtisprefix"></a><a name="isprefix"></a>CPathT：isprefix

调用此方法以确定路径是否包含*pszPrefix*传递的类型的有效前缀。

```
BOOL IsPrefix(PCXSTR pszPrefix) const;
```

### <a name="parameters"></a>参数

*pszPrefix*<br/>
要为其搜索的前缀。 前缀是以下类型之一："C："，"."，"."，"."，"."."."."."."\\\\\\\\".

### <a name="return-value"></a>返回值

如果路径包含前缀，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅[路径前缀](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw)。

## <a name="cpathtisrelative"></a><a name="isrelative"></a>CPathT：相对

调用此方法以确定路径是否相对。

```
BOOL IsRelative() const;
```

### <a name="return-value"></a>返回值

如果路径是相对的，则返回 TRUE;如果路径是绝对的，则返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅[路径相关](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew)。

## <a name="cpathtisroot"></a><a name="isroot"></a>CPathT：是根

调用此方法以确定路径是否为目录根。

```
BOOL IsRoot() const;
```

### <a name="return-value"></a>返回值

如果路径是根，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅[PathIsroot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw)。

## <a name="cpathtissameroot"></a><a name="issameroot"></a>CPathT：：IsSameRoot

调用此方法以确定另一个路径是否具有与当前路径的通用根组件。

```
BOOL IsSameRoot(PCXSTR pszOther) const;
```

### <a name="parameters"></a>参数

*pszOther*<br/>
另一条路径。

### <a name="return-value"></a>返回值

如果两个字符串具有相同的根组件，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅[路径IsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw)。

## <a name="cpathtisunc"></a><a name="isunc"></a>CPathT：ISUNC

调用此方法以确定路径是否是服务器和共享的有效 UNC（通用命名约定）路径。

```
BOOL IsUNC() const;
```

### <a name="return-value"></a>返回值

如果路径是有效的 UNC 路径，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅[PathisUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw)。

## <a name="cpathtisuncserver"></a><a name="isuncserver"></a>CPathT：isUNCServer

调用此方法以确定路径是否仅是服务器的有效 UNC（通用命名约定）路径。

```
BOOL IsUNCServer() const;
```

### <a name="return-value"></a>返回值

如果字符串仅针对服务器（无共享名称）或 FALSE 为"FALSE"，则返回 TRUE。

### <a name="remarks"></a>备注

有关详细信息，请参阅[PathisUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw)。

## <a name="cpathtisuncservershare"></a><a name="isuncservershare"></a>CPathT：isUNCServer共享

调用此方法以确定路径是否是有效的 UNC（通用命名约定）共享路径、\\\ *服务器*\ *共享*。

```
BOOL IsUNCServerShare() const;
```

### <a name="return-value"></a>返回值

如果路径\\\ *位于服务器*\ *共享*窗体中，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅[PathisUNCServer 共享](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew)。

## <a name="cpathtm_strpath"></a><a name="m_strpath"></a>CPathT：m_strPath

路径。

```
StringType m_strPath;
```

### <a name="remarks"></a>备注

`StringType`是 的`CPathT`模板参数。

## <a name="cpathtmakepretty"></a><a name="makepretty"></a>CPathT：：制作漂亮

调用此方法可将路径转换为所有小写字符，以使路径的外观一致。

```
BOOL MakePretty();
```

### <a name="return-value"></a>返回值

如果路径已转换，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅[PathMake"美丽](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw)"。

## <a name="cpathtmatchspec"></a><a name="matchspec"></a>CPathT：：匹配规格

调用此方法以搜索包含通配符匹配类型的字符串的路径。

```
BOOL MatchSpec(PCXSTR pszSpec) const;
```

### <a name="parameters"></a>参数

*pszSpec*<br/>
指向具有要搜索的文件类型的 null 终止字符串的指针。 例如，要测试当前路径上的文件是否是 DOC 文件，应将*pszSpec*设置为"*.doc"。

### <a name="return-value"></a>返回值

如果字符串匹配，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅[路径匹配Spec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw)。

## <a name="cpathtoperator-"></a><a name="operator_add_eq"></a>CPathT：：操作员 |

此运算符将字符串追加到路径中。

```
CPathT<StringType>& operator+=(PCXSTR pszMore);
```

### <a name="parameters"></a>参数

*pszMore*<br/>
要追加的字符串。

### <a name="return-value"></a>返回值

返回更新的路径。

## <a name="cpathtoperator-const-stringtype-amp"></a><a name="operator_const_stringtype_amp"></a>CPathT：：运算符 const 字符串类型&amp;

此运算符允许将对象视为字符串。

```
operator const StringType&() const throw();
```

### <a name="return-value"></a>返回值

返回表示此对象管理的当前路径的字符串。

## <a name="cpathtoperator-cpathtpcxstr"></a><a name="operator_cpatht__pcxstr"></a>CPathT：：操作员 CPathT：:PCXSTR

此运算符允许将对象视为字符串。

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>返回值

返回表示此对象管理的当前路径的字符串。

## <a name="cpathtoperator-stringtype-amp"></a><a name="operator_stringtype_amp"></a>CPathT：：运算符字符串类型&amp;

此运算符允许将对象视为字符串。

```
operator StringType&() throw();
```

### <a name="return-value"></a>返回值

返回表示此对象管理的当前路径的字符串。

## <a name="cpathtpcxstr"></a><a name="pcxstr"></a>CPathT：:PCXSTR

常量字符串类型。

```
typedef StringType::PCXSTR PCXSTR;
```

### <a name="remarks"></a>备注

`StringType`是 的`CPathT`模板参数。

## <a name="cpathtpxstr"></a><a name="pxstr"></a>CPathT：:PXSTR

一种字符串类型。

```
typedef StringType::PXSTR PXSTR;
```

### <a name="remarks"></a>备注

`StringType`是 的`CPathT`模板参数。

## <a name="cpathtquotespaces"></a><a name="quotespaces"></a>CPathT：：报价空间

如果路径包含任何空格，则调用此方法以引号括上路径。

```cpp
void QuoteSpaces();
```

### <a name="remarks"></a>备注

有关详细信息，请参阅[路径报价空间](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw)。

## <a name="cpathtrelativepathto"></a><a name="relativepathto"></a>CPatht：：相对路径

调用此方法以创建从一个文件或文件夹到另一个文件或文件夹的相对路径。

```
BOOL RelativePathTo(
    PCXSTR pszFrom,
    DWORD dwAttrFrom,
    PCXSTR pszTo,
    DWORD dwAttrTo);
```

### <a name="parameters"></a>参数

*psz 从*<br/>
相对路径的开头。

*dwAttr 从*<br/>
*pszfrom*的文件属性。 如果此值包含FILE_ATTRIBUTE_DIRECTORY，则*pszFrom*假定为目录;如果此值包含 FILE_ATTRIBUTE_DIRECTORY，则 pszFrom 假定为目录。否则 *，pszFrom*假定为文件。

*pszto*<br/>
相对路径的终点。

*德沃特尔托*<br/>
*pszTo*的文件属性。 如果此值包含FILE_ATTRIBUTE_DIRECTORY，则*pszTo*假定为目录;如果此值包含 FILE_ATTRIBUTE_DIRECTORY，则 pszTo 假定为目录。否则 *，pszTo*假定为文件。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅[路径相对路径。](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow)

## <a name="cpathtremoveargs"></a><a name="removeargs"></a>CPathT：：删除阿格

调用此方法从路径中删除任何命令行参数。

```cpp
void RemoveArgs();
```

### <a name="remarks"></a>备注

有关详细信息，请参阅[路径删除 。](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw)

## <a name="cpathtremovebackslash"></a><a name="removebackslash"></a>CPathT：：删除反斜杠

调用此方法以从路径中删除尾随反斜杠。

```cpp
void RemoveBackslash();
```

### <a name="remarks"></a>备注

有关详细信息，请参阅[路径删除反斜杠](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw)。

## <a name="cpathtremoveblanks"></a><a name="removeblanks"></a>CPathT：：删除空白

调用此方法从路径中删除所有前导空格和尾随空格。

```cpp
void RemoveBlanks();
```

### <a name="remarks"></a>备注

有关详细信息，请参阅[路径删除空白](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw)。

## <a name="cpathtremoveextension"></a><a name="removeextension"></a>CPathT：：删除扩展

调用此方法以从路径中删除文件扩展名（如果有）。

```cpp
void RemoveExtension();
```

### <a name="remarks"></a>备注

有关详细信息，请参阅[路径删除扩展](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw)。

## <a name="cpathtremovefilespec"></a><a name="removefilespec"></a>CPathT：：删除文件规格

调用此方法以从路径中删除尾随文件名和反斜杠（如果有）。

```
BOOL RemoveFileSpec();
```

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅[路径删除文件Spec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw)。

## <a name="cpathtrenameextension"></a><a name="renameextension"></a>CPathT：：重命名扩展

调用此方法以将路径中的文件名扩展名替换为新的扩展名。 如果文件名不包含扩展名，则扩展名将附加到路径的末尾。

```
BOOL RenameExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>参数

*psz 扩展*<br/>
新的文件名扩展名，前面有一个"." 字符。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅[路径重新命名扩展](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw)。

## <a name="cpathtskiproot"></a><a name="skiproot"></a>CPathT：：跳过根

调用此方法以分析路径，忽略驱动器号或 UNC（通用命名约定）服务器/共享路径部件。

```
int SkipRoot() const;
```

### <a name="return-value"></a>返回值

返回根（驱动器号或 UNC 服务器/共享）后面的子路径的开头的位置。

### <a name="remarks"></a>备注

有关详细信息，请参阅[路径跳过根](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw)。

## <a name="cpathtstrippath"></a><a name="strippath"></a>CPathT：：条带路径

调用此方法以删除完全限定的路径和文件名的路径部分。

```cpp
void StripPath();
```

### <a name="remarks"></a>备注

有关详细信息，请参阅[路径条带路径](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw)。

## <a name="cpathtstriptoroot"></a><a name="striptoroot"></a>CPatht：：条纹根

调用此方法以删除路径的所有部分，但根信息除外。

```
BOOL StripToRoot();
```

### <a name="return-value"></a>返回值

如果在路径中找到有效的驱动器号，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

有关详细信息，请参阅[路径条块](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw)。

## <a name="cpathtunquotespaces"></a><a name="unquotespaces"></a>CPathT：无引号空格

调用此方法以从路径的开头和结尾删除引号。

```cpp
void UnquoteSpaces();
```

### <a name="remarks"></a>备注

有关详细信息，请参阅[路径取消引用空格](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw)。

## <a name="cpathtxchar"></a><a name="xchar"></a>CPathT：XCHAR

一个字符类型。

```
typedef StringType::XCHAR XCHAR;
```

### <a name="remarks"></a>备注

`StringType`是 的`CPathT`模板参数。

## <a name="see-also"></a>请参阅

[类](../../atl/reference/atl-classes.md)<br/>
[CStringT 类](../../atl-mfc-shared/reference/cstringt-class.md)
