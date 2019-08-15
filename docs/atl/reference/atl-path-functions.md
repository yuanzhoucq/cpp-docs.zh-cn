---
title: ATL 路径函数
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, path
f1_keywords:
- ATLPATH/ATL::ATLPath::AddBackslash
- ATLPATH/ATL::ATLPath::AddExtension
- ATLPATH/ATL::ATLPath::Append
- ATLPATH/ATL::ATLPath::BuildRoot
- ATLPATH/ATL::ATLPath::Canonicalize
- ATLPATH/ATL::ATLPath::Combine
- ATLPATH/ATL::ATLPath::CommonPrefix
- ATLPATH/ATL::ATLPath::CompactPath
- ATLPATH/ATL::ATLPath::CompactPathEx
- ATLPATH/ATL::ATLPath::FileExists
- ATLPATH/ATL::ATLPath::FindExtension
- ATLPATH/ATL::ATLPath::FindFileName
- ATLPATH/ATL::ATLPath::GetDriveNumber
- ATLPATH/ATL::ATLPath::IsDirectory
- ATLPATH/ATL::ATLPath::IsFileSpec
- ATLPATH/ATL::ATLPath::IsPrefix
- ATLPATH/ATL::ATLPath::IsRelative
- ATLPATH/ATL::ATLPath::IsRoot
- ATLPATH/ATL::ATLPath::IsSameRoot
- ATLPATH/ATL::ATLPath::IsUNC
- ATLPATH/ATL::ATLPath::IsUNCServer
- ATLPATH/ATL::ATLPath::IsUNCServerShare
- ATLPATH/ATL::ATLPath::MakePretty
- ATLPATH/ATL::ATLPath::MatchSpec
- ATLPATH/ATL::ATLPath::QuoteSpaces
- ATLPATH/ATL::ATLPath::RelativePathTo
- ATLPATH/ATL::ATLPath::RemoveArgs
- ATLPATH/ATL::ATLPath::RemoveBackslash
- ATLPATH/ATL::ATLPath::RemoveBlanks
- ATLPATH/ATL::ATLPath::RemoveExtension
- ATLPATH/ATL::ATLPath::RemoveFileSpec
- ATLPATH/ATL::ATLPath::RenameExtension
- ATLPATH/ATL::ATLPath::SkipRoot
- ATLPATH/ATL::ATLPath::StripPath
- ATLPATH/ATL::ATLPath::StripToRoot
- ATLPATH/ATL::ATLPath::UnquoteSpaces
ms.assetid: d1ec2b8d-7ec7-43ea-90dd-0a740d2a742b
ms.openlocfilehash: 76efbb0bd43b800f186eac1afa168fc2a0c939f6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497986"
---
# <a name="atl-path-functions"></a>ATL 路径函数

ATL 提供 Atlpath.h 类, 用于以[CPathT](cpatht-class.md)的形式操作路径。 此代码可在 atlpath.h 中找到。

### <a name="related-classes"></a>相关类

|||
|-|-|
|[CPathT 类](cpatht-class.md)|此类表示一个路径。|

### <a name="related-typedefs"></a>相关的 Typedef

|||
|-|-|
|`CPath`|使用`CString`的[CPathT](cpatht-class.md)的专用化。|
|`CPathA`|使用`CStringA`的[CPathT](cpatht-class.md)的专用化。|
|`CPathW`|使用`CStringW`的[CPathT](cpatht-class.md)的专用化。|

### <a name="functions"></a>函数

|||
|-|-|
|[ATLPath::AddBackslash](#addbackslash)|此函数是[PathAddBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw)的重载包装。|
|[ATLPath::AddExtension](#addextension)|此函数是[PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw)的重载包装。|
|[ATLPath::Append](#append)|此函数是[PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw)的重载包装。|
|[ATLPath::BuildRoot](#buildroot)|此函数是[PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw)的重载包装。|
|[ATLPath::Canonicalize](#canonicalize)|此函数是[PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew)的重载包装。|
|[ATLPath::Combine](#combine)|此函数是[PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew)的重载包装。|
|[ATLPath::CommonPrefix](#commonprefix)|此函数是[PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw)的重载包装。|
|[ATLPath::CompactPath](#compactpath)|此函数是[PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw)的重载包装。|
|[ATLPath::CompactPathEx](#compactpathex)|此函数是[PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw)的重载包装。|
|[ATLPath::FileExists](#fileexists)|此函数是[PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw)的重载包装。|
|[ATLPath::FindExtension](#findextension)|此函数是[PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw)的重载包装。|
|[ATLPath::FindFileName](#findfilename)|此函数是[PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)的重载包装。|
|[ATLPath::GetDriveNumber](#getdrivenumber)|此函数是[PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw)的重载包装。|
|[ATLPath::IsDirectory](#isdirectory)|此函数是[PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw)的重载包装。|
|[ATLPath::IsFileSpec](#isfilespec)|此函数是[PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw)的重载包装。|
|[ATLPath::IsPrefix](#isprefix)|此函数是[PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw)的重载包装。|
|[ATLPath::IsRelative](#isrelative)|此函数是[PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew)的重载包装。|
|[ATLPath::IsRoot](#isroot)|此函数是[PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw)的重载包装。|
|[ATLPath::IsSameRoot](#issameroot)|此函数是[PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw)的重载包装。|
|[ATLPath::IsUNC](#isunc)|此函数是[PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw)的重载包装。|
|[ATLPath::IsUNCServer](#isuncserver)|此函数是[PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw)的重载包装。|
|[ATLPath::IsUNCServerShare](#isuncservershare)|此函数是[PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew)的重载包装。|
|[ATLPath::MakePretty](#makepretty)|此函数是[PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw)的重载包装。|
|[ATLPath::MatchSpec](#matchspec)|此函数是[PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw)的重载包装。|
|[ATLPath::QuoteSpaces](#quotespaces)|此函数是[PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw)的重载包装。|
|[ATLPath::RelativePathTo](#relativepathto)|此函数是[PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow)的重载包装。|
|[ATLPath::RemoveArgs](#removeargs)|此函数是[PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw)的重载包装。|
|[ATLPath::RemoveBackslash](#removebackslash)|此函数是[PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw)的重载包装。|
|[ATLPath::RemoveBlanks](#removeblanks)|此函数是[PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw)的重载包装。|
|[ATLPath::RemoveExtension](#removeextension)|此函数是[PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw)的重载包装。|
|[ATLPath::RemoveFileSpec](#removefilespec)|此函数是[PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw)的重载包装。|
|[ATLPath::RenameExtension](#renameextension)|此函数是[PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw)的重载包装。|
|[ATLPath::SkipRoot](#skiproot)|此函数是[PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw)的重载包装。|
|[ATLPath::StripPath](#strippath)|此函数是[PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw)的重载包装。|
|[ATLPath::StripToRoot](#striptoroot)|此函数是[PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw)的重载包装。|
|[ATLPath::UnquoteSpaces](#unquotespaces)|此函数是[PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw)的重载包装。|

## <a name="requirements"></a>要求

**标头:** atlpath。h

## <a name="addbackslash"></a>Atlpath.h:: AddBackSlash

此函数是[PathAddBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw)的重载包装。

### <a name="syntax"></a>语法

```
inline char* AddBackslash(char* pszPath);
inline wchar_t* AddBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathAddBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw) 。

## <a name="addextension"></a>Atlpath.h:: AddExtension

此函数是[PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw)的重载包装。

### <a name="syntax"></a>语法

```
inline BOOL AddExtension(char* pszPath, const char* pszExtension);
inline BOOL AddExtension(wchar_t* pszPath, const wchar_t* pszExtension);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw) 。

## <a name="append"></a>Atlpath.h:: Append

此函数是[PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw)的重载包装。

### <a name="syntax"></a>语法

```
inline BOOL Append(char* pszPath, const char* pszMore);
inline BOOL Append(wchar_t* pszPath, const wchar_t* pszMore);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw) 。

## <a name="buildroot"></a> ATLPath::BuildRoot

此函数是[PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw)的重载包装。

### <a name="syntax"></a>语法

```
inline char* BuildRoot(char* pszPath, int iDrive);
inline wchar_t* BuildRoot(wchar_t* pszPath, int iDrive);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw) 。

## <a name="canonicalize"></a>Atlpath.h:: 规范化

此函数是[PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew)的重载包装。

### <a name="syntax"></a>语法

```
inline BOOL Canonicalize(char* pszDest, const char* pszSrc);
inline BOOL Canonicalize(wchar_t* pszDest, const wchar_t* pszSrc);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew) 。

## <a name="combine"></a>Atlpath.h:: 合并

此函数是[PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew)的重载包装。

### <a name="syntax"></a>语法

```
inline char* Combine(
   char* pszDest,
   const char* pszDir,
   const char* pszFile
);

inline wchar_t* Combine(
   wchar_t* pszDest,
   const wchar_t* pszDir,
   const wchar_t* pszFile);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅 PathCombine。

## <a name="commonprefix"></a> ATLPath::CommonPrefix

此函数是[PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw)的重载包装。

### <a name="syntax"></a>语法

```
inline int CommonPrefix(
   const char* pszFile1,
   const char* pszFile2,
   char* pszDest);

inline int CommonPrefix(
   const wchar_t* pszFile1,
   const wchar_t* pszFile2,
   wchar_t* pszDest);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw) 。

## <a name="compactpath"></a> ATLPath::CompactPath

此函数是[PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw)的重载包装。

### <a name="syntax"></a>语法

```
inline BOOL CompactPath(
   HDC hDC,
   char* pszPath,
   UINT dx);

inline BOOL CompactPath(
   HDC hDC,
   wchar_t* pszPath,
   UINT dx);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw) 。

## <a name="compactpathex"></a> ATLPath::CompactPathEx

此函数是[PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw)的重载包装。

### <a name="syntax"></a>语法

```
inline BOOL CompactPathEx(
   char* pszDest,
   const char* pszSrc,
   UINT nMaxChars,
   DWORD dwFlags);

inline BOOL CompactPathEx(
   wchar_t* pszDest,
   const wchar_t* pszSrc,
   UINT nMaxChars,
   DWORD dwFlags);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw) 。

## <a name="fileexists"></a>Atlpath.h:: FileExists

此函数是[PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw)的重载包装。

### <a name="syntax"></a>语法

```
inline BOOL FileExists(const char* pszPath);
inline BOOL FileExists(const wchar_t* pszPath);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw) 。

## <a name="findextension"></a>Atlpath.h:: FindExtension

此函数是[PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw)的重载包装。

### <a name="syntax"></a>语法

```
inline char* FindExtension(const char* pszPath);
inline wchar_t* FindExtension(const wchar_t* pszPath);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw) 。

## <a name="findfilename"></a> ATLPath::FindFileName

此函数是[PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)的重载包装。

### <a name="syntax"></a>语法

```
inline char* FindFileName(const char* pszPath);
inline wchar_t* FindFileName(const wchar_t* pszPath);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew) 。

## <a name="getdrivenumber"></a> ATLPath::GetDriveNumber

此函数是[PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw)的重载包装。

### <a name="syntax"></a>语法

```
inline int GetDriveNumber(const char* pszPath);
inline int GetDriveNumber(const wchar_t* pszPath);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw) 。

## <a name="isdirectory"></a>  ATLPath::IsDirectory

此函数是[PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw)的重载包装。

```
inline BOOL IsDirectory(const char* pszPath);
inline BOOL IsDirectory(const wchar_t* pszPath);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅 PathIsDirectory。

## <a name="isfilespec"></a> ATLPath::IsFileSpec

此函数是[PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw)的重载包装。

### <a name="syntax"></a>语法

```
inline BOOL IsFileSpec(const char* pszPath);
inline BOOL IsFileSpec(const wchar_t* pszPath);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw) 。

## <a name="isprefix"></a> ATLPath::IsPrefix

此函数是[PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw)的重载包装。

### <a name="syntax"></a>语法

```
inline BOOL IsPrefix(const char* pszPrefix, const char* pszPath);
inline BOOL IsPrefix(const wchar_t* pszPrefix, const wchar_t* pszPath);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw) 。

## <a name="isrelative"></a> ATLPath::IsRelative

此函数是[PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew)的重载包装。

### <a name="syntax"></a>语法

```
inline BOOL IsRelative(const char* pszPath);
inline BOOL IsRelative(const wchar_t* pszPath);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew) 。

## <a name="isroot"></a> ATLPath::IsRoot

此函数是[PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw)的重载包装。

### <a name="syntax"></a>语法

```
inline BOOL IsRoot(const char* pszPath);
inline BOOL IsRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw) 。

## <a name="issameroot"></a> ATLPath::IsSameRoot

此函数是[PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw)的重载包装。

### <a name="syntax"></a>语法

```
inline BOOL IsSameRoot(const char* pszPath1, const char* pszPath2);
inline BOOL IsSameRoot(const wchar_t* pszPath1, const wchar_t* pszPath2);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw) 。

## <a name="isunc"></a> ATLPath::IsUNC

此函数是[PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw)的重载包装。

### <a name="syntax"></a>语法

```
inline BOOL IsUNC(const char* pszPath);
inline BOOL IsUNC(const wchar_t* pszPath);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw) 。

## <a name="isuncserver"></a> ATLPath::IsUNCServer

此函数是[PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw)的重载包装。

### <a name="syntax"></a>语法

```
inline BOOL IsUNCServer(const char* pszPath);
inline BOOL IsUNCServer(const wchar_t* pszPath);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw) 。

## <a name="isuncservershare"></a>Atlpath.h:: IsUNCServerShare

此函数是[PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew)的重载包装。

### <a name="syntax"></a>语法

```
inline BOOL IsUNCServerShare(const char* pszPath);
inline BOOL IsUNCServerShare(const wchar_t* pszPath);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew) 。

## <a name="makepretty"></a> ATLPath::MakePretty

此函数是[PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw)的重载包装。

### <a name="syntax"></a>语法

```
inline BOOL MakePretty(char* pszPath);
inline BOOL MakePretty(wchar_t* pszPath);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw) 。

## <a name="matchspec"></a> ATLPath::MatchSpec

此函数是[PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw)的重载包装。

### <a name="syntax"></a>语法

```
inline BOOL MatchSpec(const char* pszPath, const char* pszSpec);
inline BOOL MatchSpec(const wchar_t* pszPath, const wchar_t* pszSpec);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw) 。

## <a name="quotespaces"></a> ATLPath::QuoteSpaces

此函数是[PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw)的重载包装。

### <a name="syntax"></a>语法

```
inline void QuoteSpaces(char* pszPath);
inline void QuoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw) 。

## <a name="relativepathto"></a>Atlpath.h:: RelativePathTo

此函数是[PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow)的重载包装。

### <a name="syntax"></a>语法

```
inline BOOL RelativePathTo(
   char* pszPath,
   const char* pszFrom,
   DWORD dwAttrFrom,
   const char* pszTo,
   DWORD dwAttrTo);

inline BOOL RelativePathTo(
   wchar_t* pszPath,
   const wchar_t* pszFrom,
   DWORD dwAttrFrom,
   const wchar_t* pszTo,
   DWORD dwAttrTo);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow) 。

## <a name="removeargs"></a>Atlpath.h:: RemoveArgs

此函数是[PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw)的重载包装。

### <a name="syntax"></a>语法

```
inline void RemoveArgs(char* pszPath);
inline void RemoveArgs(wchar_t* pszPath);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw) 。

## <a name="removebackslash"></a>Atlpath.h:: RemoveBackslash

此函数是[PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw)的重载包装。

### <a name="syntax"></a>语法

```
inline char* RemoveBackslash(char* pszPath);
inline wchar_t* RemoveBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw) 。

## <a name="removeblanks"></a>Atlpath.h:: RemoveBlanks

此函数是[PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw)的重载包装。

### <a name="syntax"></a>语法

```
inline void RemoveBlanks(char* pszPath);
inline void RemoveBlanks(wchar_t* pszPath);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw) 。

## <a name="removeextension"></a>Atlpath.h:: RemoveExtension

此函数是[PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw)的重载包装。

### <a name="syntax"></a>语法

```
inline void RemoveExtension(char* pszPath);
inline void RemoveExtension(wchar_t* pszPath);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw) 。

## <a name="removefilespec"></a> ATLPath::RemoveFileSpec

此函数是[PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw)的重载包装。

### <a name="syntax"></a>语法

```
inline BOOL RemoveFileSpec(char* pszPath);
inline BOOL RemoveFileSpec(wchar_t* pszPath);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw) 。

## <a name="renameextension"></a> ATLPath::RenameExtension

此函数是[PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw)的重载包装。

### <a name="syntax"></a>语法

```
inline BOOL RenameExtension(char* pszPath, const char* pszExt);
inline BOOL RenameExtension(wchar_t* pszPath, const wchar_t* pszExt);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw) 。

## <a name="skiproot"></a> ATLPath::SkipRoot

此函数是[PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw)的重载包装。

### <a name="syntax"></a>语法

```
inline char* SkipRoot(const char* pszPath);
inline wchar_t* SkipRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw) 。

## <a name="strippath"></a> ATLPath::StripPath

此函数是[PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw)的重载包装。

### <a name="syntax"></a>语法

```
inline void StripPath(char* pszPath);
inline void StripPath(wchar_t* pszPath);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw) 。

## <a name="striptoroot"></a> ATLPath::StripToRoot

此函数是[PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw)的重载包装。

### <a name="syntax"></a>语法

```
inline BOOL StripToRoot(char* pszPath);
inline BOOL StripToRoot(wchar_t* pszPath);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw) 。

## <a name="unquotespaces"></a>Atlpath.h:: UnquoteSpaces

此函数是[PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw)的重载包装。

### <a name="syntax"></a>语法

```
inline void UnquoteSpaces(char* pszPath);
inline void UnquoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>备注

有关详细信息, 请参阅[PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw) 。
