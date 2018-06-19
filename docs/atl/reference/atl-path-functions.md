---
title: ATL 路径函数 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 38286d169591dd55f7a2618332b6f5d5c9c86719
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366531"
---
# <a name="atl-path-functions"></a>ATL 路径函数

ATL 提供用于操作的窗体中的路径 ATLPath 类[CPathT](cpatht-class.md)。 此代码可在 atlpath.h。  
  
### <a name="related-classes"></a>相关的类  
  
|||  
|-|-|  
|[CPathT 类](cpatht-class.md)|此类表示的路径。|  

### <a name="related-typedefs"></a>相关的 Typedef  
  
|||  
|-|-|  
|`CPath`|专用化[CPathT](cpatht-class.md)使用`CString`。|  
|`CPathA`|专用化[CPathT](cpatht-class.md)使用`CStringA`。|  
|`CPathW`|专用化[CPathT](cpatht-class.md)使用`CStringW`。|  
  
### <a name="functions"></a>函数  
  
|||  
|-|-|  
|[ATLPath::AddBackslash](#addbackslash)|此函数是的重载的包装器[PathAddBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773561)。|  
|[ATLPath::AddExtension](#addextension)|此函数是的重载的包装器[PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563)。|  
|[ATLPath::Append](#append)|此函数是的重载的包装器[PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565)。|  
|[ATLPath::BuildRoot](#buildroot)|此函数是的重载的包装器[PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567)。|  
|[ATLPath::Canonicalize](#canonicalize)|此函数是的重载的包装器[PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569)。|  
|[ATLPath::Combine](#combine)|此函数是的重载的包装器[PathCombine](http://msdn.microsoft.com/library/windows/desktop/bb773571)。|  
|[ATLPath::CommonPrefix](#commonprefix)|此函数是的重载的包装器[PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574)。|  
|[ATLPath::CompactPath](#compactpath)|此函数是的重载的包装器[PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575)。|  
|[ATLPath::CompactPathEx](#compactpathex)|此函数是的重载的包装器[PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578)。|  
|[ATLPath::FileExists](#fileexists)|此函数是的重载的包装器[PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584)。|  
|[ATLPath::FindExtension](#findextension)|此函数是的重载的包装器[PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587)。|  
|[ATLPath::FindFileName](#findfilename)|此函数是的重载的包装器[PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589)。|  
|[ATLPath::GetDriveNumber](#getdrivenumber)|此函数是的重载的包装器[PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612)。|  
|[ATLPath::IsDirectory](#isdirectory)|此函数是的重载的包装器[PathIsDirectory](http://msdn.microsoft.com/library/windows/desktop/bb773621)。|  
|[ATLPath::IsFileSpec](#isfilespec)|此函数是的重载的包装器[PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627)。|  
|[ATLPath::IsPrefix](#isprefix)|此函数是的重载的包装器[PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650)。|  
|[ATLPath::IsRelative](#isrelative)|此函数是的重载的包装器[PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660)。|  
|[ATLPath::IsRoot](#isroot)|此函数是的重载的包装器[PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674)。|  
|[ATLPath::IsSameRoot](#issameroot)|此函数是的重载的包装器[PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687)。|  
|[ATLPath::IsUNC](#isunc)|此函数是的重载的包装器[PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712)。|  
|[ATLPath::IsUNCServer](#isuncserver)|此函数是的重载的包装器[PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722)。|  
|[ATLPath::IsUNCServerShare](#isuncservershare)|此函数是的重载的包装器[PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723)。|  
|[ATLPath::MakePretty](#makepretty)|此函数是的重载的包装器[PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725)。|  
|[ATLPath::MatchSpec](#matchspec)|此函数是的重载的包装器[PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727)。|  
|[ATLPath::QuoteSpaces](#quotespaces)|此函数是的重载的包装器[PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739)。|  
|[ATLPath::RelativePathTo](#relativepathto)|此函数是的重载的包装器[PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740)。|  
|[ATLPath::RemoveArgs](#removeargs)|此函数是的重载的包装器[PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742)。|  
|[ATLPath::RemoveBackslash](#removebackslash)|此函数是的重载的包装器[PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743)。|  
|[ATLPath::RemoveBlanks](#removeblanks)|此函数是的重载的包装器[PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745)。|  
|[ATLPath::RemoveExtension](#removeextension)|此函数是的重载的包装器[PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746)。|  
|[ATLPath::RemoveFileSpec](#removefilespec)|此函数是的重载的包装器[PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748)。|  
|[ATLPath::RenameExtension](#renameextension)|此函数是的重载的包装器[PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749)。|  
|[ATLPath::SkipRoot](#skiproot)|此函数是的重载的包装器[PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754)。|  
|[ATLPath::StripPath](#strippath)|此函数是的重载的包装器[PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756)。|  
|[ATLPath::StripToRoot](#striptoroot)|此函数是的重载的包装器[PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757)。|  
|[ATLPath::UnquoteSpaces](#unquotespaces)|此函数是的重载的包装器[PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763)。|  
  
## <a name="requirements"></a>要求  
 **标头：** atlpath.h  

## <a name="addbackslash"></a> ATLPath::AddBackSlash

此函数是的重载的包装器[PathAddBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773561)。  
  
### <a name="syntax"></a>语法  
  
```  
inline char* AddBackslash(char* pszPath);  
inline wchar_t* AddBackslash(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>备注  
 请参阅[PathAddBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773561)有关详细信息。  
  
 
  

## <a name="addextension"></a> ATLPath::AddExtension
 此函数是的重载的包装器[PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563)。  
  
### <a name="syntax"></a>语法  
  
```  
inline BOOL AddExtension(char* pszPath, const char* pszExtension);  
inline BOOL AddExtension(wchar_t* pszPath, const wchar_t* pszExtension);  
```  
  
### <a name="remarks"></a>备注  
 请参阅[PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563)有关详细信息。 
  
## <a name="append"></a> ATLPath::Append
 此函数是的重载的包装器[PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565)。  
  
### <a name="syntax"></a>语法  
  
```  
inline BOOL Append(char* pszPath, const char* pszMore);  
inline BOOL Append(wchar_t* pszPath, const wchar_t* pszMore);  
```  
  
### <a name="remarks"></a>备注  
 请参阅[PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565)有关详细信息。  
  
 
  

## <a name="buildroot"></a> ATLPath::BuildRoot
 此函数是的重载的包装器[PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567)。  
  
### <a name="syntax"></a>语法  
  
```  
inline char* BuildRoot(char* pszPath, int iDrive);  
inline wchar_t* BuildRoot(wchar_t* pszPath, int iDrive);  
```  
  
### <a name="remarks"></a>备注  
 请参阅[PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567)有关详细信息。  
  
 
  

## <a name="canonicalize"></a> ATLPath::Canonicalize
 此函数是的重载的包装器[PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569)。  
  
### <a name="syntax"></a>语法  
  
```  
inline BOOL Canonicalize(char* pszDest, const char* pszSrc);  
inline BOOL Canonicalize(wchar_t* pszDest, const wchar_t* pszSrc);  
```  
  
### <a name="remarks"></a>备注  
 请参阅[PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569)有关详细信息。  
  
 
  

## <a name="combine"></a> ATLPath::Combine 
此函数是的重载的包装器[PathCombine](https://msdn.microsoft.com/en-us/library/windows/desktop/bb773571)。  

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
有关详细信息，请参阅 PathCombine。


## <a name="commonprefix"></a> ATLPath::CommonPrefix
 此函数是的重载的包装器[PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574)。  
  
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
 请参阅[PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574)有关详细信息。  
  
 
  

## <a name="compactpath"></a> ATLPath::CompactPath
 此函数是的重载的包装器[PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575)。  
  
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
 请参阅[PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575)有关详细信息。  
  
 
  

## <a name="compactpathex"></a> ATLPath::CompactPathEx
 此函数是的重载的包装器[PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578)。  
  
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
 请参阅[PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578)有关详细信息。  
  
 
  

## <a name="fileexists"></a> ATLPath::FileExists
 此函数是的重载的包装器[PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584)。  
  
### <a name="syntax"></a>语法  
  
```  
inline BOOL FileExists(const char* pszPath);  
inline BOOL FileExists(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>备注  
 请参阅[PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584)有关详细信息。  
  
 
  

## <a name="findextension"></a> ATLPath::FindExtension
 此函数是的重载的包装器[PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587)。  
  
### <a name="syntax"></a>语法  
  
```  
inline char* FindExtension(const char* pszPath);  
inline wchar_t* FindExtension(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>备注  
 请参阅[PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587)有关详细信息。  
  
 
  

## <a name="findfilename"></a> ATLPath::FindFileName
 此函数是的重载的包装器[PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589)。  
  
### <a name="syntax"></a>语法  
  
```  
inline char* FindFileName(const char* pszPath);  
inline wchar_t* FindFileName(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>备注  
 请参阅[PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589)有关详细信息。  
  
 
  

## <a name="getdrivenumber"></a> ATLPath::GetDriveNumber  
 此函数是的重载的包装器[PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612)。  
  
### <a name="syntax"></a>语法  
  
```  
inline int GetDriveNumber(const char* pszPath);  
inline int GetDriveNumber(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>备注  
 请参阅[PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612)有关详细信息。  
  
 


## <a name="isdirectory"></a>  ATLPath::IsDirectory 
此函数是的重载的包装器[PathIsDirectory](https://msdn.microsoft.com/en-us/library/windows/desktop/bb773621)。

```  
inline BOOL IsDirectory(const char* pszPath);
inline BOOL IsDirectory(const wchar_t* pszPath);
```  
### <a name="remarks"></a>备注
有关详细信息，请参阅 PathIsDirectory。  

## <a name="isfilespec"></a> ATLPath::IsFileSpec
 此函数是的重载的包装器[PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627)。  
  
### <a name="syntax"></a>语法  
  
```  
inline BOOL IsFileSpec(const char* pszPath);  
inline BOOL IsFileSpec(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>备注  
 请参阅[PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627)有关详细信息。  
  
 
  

## <a name="isprefix"></a> ATLPath::IsPrefix
 此函数是的重载的包装器[PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650)。  
  
### <a name="syntax"></a>语法  
  
```  
inline BOOL IsPrefix(const char* pszPrefix, const char* pszPath);  
inline BOOL IsPrefix(const wchar_t* pszPrefix, const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>备注  
 请参阅[PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650)有关详细信息。  
  
 
  

## <a name="isrelative"></a> ATLPath::IsRelative
 此函数是的重载的包装器[PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660)。  
  
### <a name="syntax"></a>语法  
  
```  
inline BOOL IsRelative(const char* pszPath);  
inline BOOL IsRelative(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>备注  
 请参阅[PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660)有关详细信息。  
  
 
  

## <a name="isroot"></a> ATLPath::IsRoot
 此函数是的重载的包装器[PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674)。  
  
### <a name="syntax"></a>语法  
  
```  
inline BOOL IsRoot(const char* pszPath);  
inline BOOL IsRoot(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>备注  
 请参阅[PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674)有关详细信息。  
  
 
  

## <a name="issameroot"></a> ATLPath::IsSameRoot
 此函数是的重载的包装器[PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687)。  
  
### <a name="syntax"></a>语法  
  
```  
inline BOOL IsSameRoot(const char* pszPath1, const char* pszPath2);  
inline BOOL IsSameRoot(const wchar_t* pszPath1, const wchar_t* pszPath2);  
```  
  
### <a name="remarks"></a>备注  
 请参阅[PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687)有关详细信息。  
  
 
  

## <a name="isunc"></a> ATLPath::IsUNC
 此函数是的重载的包装器[PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712)。  
  
### <a name="syntax"></a>语法  
  
```  
inline BOOL IsUNC(const char* pszPath);  
inline BOOL IsUNC(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>备注  
 请参阅[PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712)有关详细信息。  
  
 
  

## <a name="isuncserver"></a> ATLPath::IsUNCServer
 此函数是的重载的包装器[PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722)。  
  
### <a name="syntax"></a>语法  
  
```  
inline BOOL IsUNCServer(const char* pszPath);  
inline BOOL IsUNCServer(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>备注  
 请参阅[PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722)有关详细信息。  
  
 
  

## <a name="isuncservershare"></a> ATLPath::IsUNCServerShare
 此函数是的重载的包装器[PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723)。  
  
### <a name="syntax"></a>语法  
  
```  
inline BOOL IsUNCServerShare(const char* pszPath);  
inline BOOL IsUNCServerShare(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>备注  
 请参阅[PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723)有关详细信息。  
  
 
  

## <a name="makepretty"></a> ATLPath::MakePretty
 此函数是的重载的包装器[PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725)。  
  
### <a name="syntax"></a>语法  
  
```  
inline BOOL MakePretty(char* pszPath);  
inline BOOL MakePretty(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>备注  
 请参阅[PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725)有关详细信息。  
  
 
  

## <a name="matchspec"></a> ATLPath::MatchSpec  
 此函数是的重载的包装器[PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727)。  
  
### <a name="syntax"></a>语法  
  
```  
inline BOOL MatchSpec(const char* pszPath, const char* pszSpec);  
inline BOOL MatchSpec(const wchar_t* pszPath, const wchar_t* pszSpec);  
```  
  
### <a name="remarks"></a>备注  
 请参阅[PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727)有关详细信息。  
  
 
  

## <a name="quotespaces"></a> ATLPath::QuoteSpaces  
 此函数是的重载的包装器[PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739)。  
  
### <a name="syntax"></a>语法  
  
```  
inline void QuoteSpaces(char* pszPath);  
inline void QuoteSpaces(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>备注  
 请参阅[PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739)有关详细信息。  
  
 
  

## <a name="relativepathto"></a> ATLPath::RelativePathTo
 此函数是的重载的包装器[PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740)。  
  
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
 请参阅[PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740)有关详细信息。  
  
 
  

## <a name="removeargs"></a> ATLPath::RemoveArgs  
 此函数是的重载的包装器[PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742)。  
  
### <a name="syntax"></a>语法  
  
```  
inline void RemoveArgs(char* pszPath);  
inline void RemoveArgs(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>备注  
 请参阅[PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742)有关详细信息。  
  
 
  

## <a name="removebackslash"></a> ATLPath::RemoveBackslash
 此函数是的重载的包装器[PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743)。  
  
### <a name="syntax"></a>语法  
  
```  
inline char* RemoveBackslash(char* pszPath);  
inline wchar_t* RemoveBackslash(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>备注  
 请参阅[PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743)有关详细信息。  
  
 
  

## <a name="removeblanks"></a> ATLPath::RemoveBlanks
 此函数是的重载的包装器[PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745)。  
  
### <a name="syntax"></a>语法  
  
```  
inline void RemoveBlanks(char* pszPath);  
inline void RemoveBlanks(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>备注  
 请参阅[PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745)有关详细信息。  
  
 
  

## <a name="removeextension"></a> ATLPath::RemoveExtension
 此函数是的重载的包装器[PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746)。  
  
### <a name="syntax"></a>语法  
  
```  
inline void RemoveExtension(char* pszPath);  
inline void RemoveExtension(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>备注  
 请参阅[PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746)有关详细信息。  
  
 
  

## <a name="removefilespec"></a> ATLPath::RemoveFileSpec
 此函数是的重载的包装器[PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748)。  
  
### <a name="syntax"></a>语法  
  
```  
inline BOOL RemoveFileSpec(char* pszPath);  
inline BOOL RemoveFileSpec(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>备注  
 请参阅[PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748)有关详细信息。  
  
 
  

## <a name="renameextension"></a> ATLPath::RenameExtension
 此函数是的重载的包装器[PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749)。  
  
### <a name="syntax"></a>语法  
  
```  
inline BOOL RenameExtension(char* pszPath, const char* pszExt);  
inline BOOL RenameExtension(wchar_t* pszPath, const wchar_t* pszExt);  
```  
  
### <a name="remarks"></a>备注  
 请参阅[PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749)有关详细信息。  
  
 
  

## <a name="skiproot"></a> ATLPath::SkipRoot
 此函数是的重载的包装器[PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754)。  
  
### <a name="syntax"></a>语法  
  
```  
inline char* SkipRoot(const char* pszPath);  
inline wchar_t* SkipRoot(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>备注  
 请参阅[PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754)有关详细信息。  
  
 
  

## <a name="strippath"></a> ATLPath::StripPath
 此函数是的重载的包装器[PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756)。  
  
### <a name="syntax"></a>语法  
  
```  
inline void StripPath(char* pszPath);  
inline void StripPath(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>备注  
 请参阅[PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756)有关详细信息。  
  
 
  


## <a name="striptoroot"></a> ATLPath::StripToRoot
 此函数是的重载的包装器[PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757)。  
  
### <a name="syntax"></a>语法  
  
```  
inline BOOL StripToRoot(char* pszPath);  
inline BOOL StripToRoot(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>备注  
 请参阅[PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757)有关详细信息。  
  
 
  

## <a name="unquotespaces"></a> ATLPath::UnquoteSpaces
 此函数是的重载的包装器[PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763)。  
  
### <a name="syntax"></a>语法  
  
```  
inline void UnquoteSpaces(char* pszPath);  
inline void UnquoteSpaces(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>备注  
 请参阅[PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763)有关详细信息。  
  
 
  
 
