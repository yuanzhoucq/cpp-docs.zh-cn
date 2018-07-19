---
title: CPathT 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CPathT class
ms.assetid: eba4137d-1fd2-4b44-a2e1-0944db64df3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a7b19cff6e4f90485946521824bb0fd2f6358372
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37885229"
---
# <a name="cpatht-class"></a>CPathT 类
此类表示的路径。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。  
  
## <a name="syntax"></a>语法  
  
```
template <typename StringType>
class CPathT
```  
  
#### <a name="parameters"></a>参数  
 *StringType*  
 要使用的路径的 ATL/MFC 字符串类 (请参阅[CStringT](../../atl-mfc-shared/reference/cstringt-class.md))。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|[CPathT::PCXSTR](#pcxstr)|常量字符串类型。|  
|[CPathT::PXSTR](#pxstr)|字符串类型。|  
|[CPathT::XCHAR](#xchar)|一个字符类型。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CPathT::CPathT](#cpatht)|路径的构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CPathT::AddBackslash](#addbackslash)|调用此方法可为要创建正确的语法的路径字符串的末尾添加反斜杠。|  
|[CPathT::AddExtension](#addextension)|调用此方法以将文件扩展名添加到路径。|  
|[CPathT::Append](#append)|调用此方法以将字符串追加到当前路径。|  
|[CPathT::BuildRoot](#buildroot)|调用此方法以从给定的驱动器号创建根路径。|  
|[CPathT::Canonicalize](#canonicalize)|调用此方法将路径转换为规范化形式。|  
|[CPathT::Combine](#combine)|调用此方法来连接表示目录名称的字符串和一个到一个路径表示文件路径名称的字符串。|  
|[CPathT::CommonPrefix](#commonprefix)|调用此方法以确定指定的路径是否与当前路径共享公共前缀。|  
|[CPathT::CompactPath](#compactpath)|调用此方法来截断以适合给定的像素宽度由路径组件替换为省略号的文件路径。|  
|[CPathT::CompactPathEx](#compactpathex)|调用此方法来截断以适合给定数目的字符的路径组件替换为省略号的文件路径。|  
|[CPathT::FileExists](#fileexists)|调用此方法来检查是否存在，此路径名称中的文件。|  
|[CPathT::FindExtension](#findextension)|调用此方法来查找在该路径的文件扩展名的位置。|  
|[CPathT::FindFileName](#findfilename)|调用此方法来查找在该路径的文件名称的位置。|  
|[CPathT::GetDriveNumber](#getdrivenumber)|调用此方法来搜索的 A 到 Z 范围内的驱动器号的路径，并返回相应的驱动器号。|  
|[CPathT::GetExtension](#getextension)|调用此方法以从路径获取文件扩展名。|  
|[CPathT::IsDirectory](#isdirectory)|调用此方法来检查路径是否是有效的目录。|  
|[CPathT::IsFileSpec](#isfilespec)|调用此方法来搜索任何路径分隔字符的路径 (例如，':' 或 '\\)。 如果存在任何路径分隔字符，被考虑使用该路径为文件规范路径。|  
|[CPathT::IsPrefix](#isprefix)|调用此方法来确定路径是否包含所传递类型的有效前缀*pszPrefix*。|  
|[CPathT::IsRelative](#isrelative)|调用此方法以确定该路径是相对。|  
|[CPathT::IsRoot](#isroot)|调用此方法来确定路径是目录的根目录。|  
|[CPathT::IsSameRoot](#issameroot)|调用此方法来确定另一个路径是否具有当前路径的常见根组件。|  
|[CPathT::IsUNC](#isunc)|调用此方法来确定路径是否有效的 UNC （通用命名约定） 路径的服务器和共享。|  
|[CPathT::IsUNCServer](#isuncserver)|调用此方法来确定路径是否只能为服务器的有效 UNC （通用命名约定） 路径。|  
|[CPathT::IsUNCServerShare](#isuncservershare)|调用此方法来确定路径是否有效的 UNC （通用命名约定） 共享路径， \\ \ *服务器*\ *共享*。|  
|[CPathT::MakePretty](#makepretty)|调用此方法以将路径转换为所有小写字符，以提供一致的外观的路径。|  
|[CPathT::MatchSpec](#matchspec)|调用此方法搜索的路径包含通配符匹配类型的字符串。|  
|[CPathT::QuoteSpaces](#quotespaces)|调用此方法以将该路径括在引号中，如果它包含任何空格。|  
|[CPathT::RelativePathTo](#relativepathto)|调用此方法创建的相对路径从一个文件或文件夹。|  
|[CPathT::RemoveArgs](#removeargs)|调用此方法以从路径中删除任何命令行参数。|  
|[CPathT::RemoveBackslash](#removebackslash)|调用此方法以从路径中删除尾随反斜杠。|  
|[CPathT::RemoveBlanks](#removeblanks)|调用此方法以从路径中删除所有前导和尾随空格。|  
|[CPathT::RemoveExtension](#removeextension)|如果有，则调用此方法以从路径中，删除文件扩展名。|  
|[CPathT::RemoveFileSpec](#removefilespec)|它是否调用此方法以从路径中删除尾随的文件名和反斜杠。|  
|[CPathT::RenameExtension](#renameextension)|调用此方法将在路径中的文件扩展名替换为一个新的扩展。 如果文件名称不包含扩展，扩展将附加到字符串的末尾。|  
|[CPathT::SkipRoot](#skiproot)|调用此方法要分析的路径，忽略驱动器号或 UNC 共享服务器/路径部分。|  
|[CPathT::StripPath](#strippath)|调用此方法，若要删除的完全限定的路径和文件名的路径部分。|  
|[CPathT::StripToRoot](#striptoroot)|调用此方法来删除除根信息的路径的所有部分。|  
|[CPathT::UnquoteSpaces](#unquotespaces)|调用此方法的开头和结尾的路径中删除引号标记。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CPathT::operator const StringType （& a)](#operator_const_stringtype_amp)|此运算符使对象可以被视为字符串。|  
|[CPathT::operator CPathT::PCXSTR](#operator_cpatht__pcxstr)|此运算符使对象可以被视为字符串。|  
|[CPathT::operator StringType （& a)](#operator_stringtype)|此运算符使对象可以被视为字符串。|  
|[CPathT::operator + =](#operator_add_eq)|此运算符将字符串追加到路径。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CPathT::m_strPath](#m_strpath)|路径。|  
  
## <a name="remarks"></a>备注  
 `CPath``CPathA`，并`CPathW`是实例化的`CPathT`定义，如下所示：  
  
 `typedef CPathT< CString > CPath;`  
  
 `typedef CPathT< CStringA > CPathA;`  
  
 `typedef CPathT< CStringW > CPathW;`  
  
## <a name="requirements"></a>要求  
 **标头：** atlpath.h  
  
##  <a name="addbackslash"></a>  CPathT::AddBackslash  
 调用此方法可为要创建正确的语法的路径字符串的末尾添加反斜杠。 如果路径已具有尾部反斜杠，则将添加没有反斜杠。  
  
```
void AddBackslash();
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathAddBackSlash](http://msdn.microsoft.com/library/windows/desktop/bb773561)。  
  
##  <a name="addextension"></a>  CPathT::AddExtension  
 调用此方法以将文件扩展名添加到路径。  
  
```
BOOL AddExtension(PCXSTR pszExtension);
```  
  
### <a name="parameters"></a>参数  
 *pszExtension*  
 要添加的文件扩展名。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563)。  
  
##  <a name="append"></a>  CPathT::Append  
 调用此方法以将字符串追加到当前路径。  
  
```
BOOL Append(PCXSTR pszMore);
```  
  
### <a name="parameters"></a>参数  
 *pszMore*  
 要追加的字符串。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565)。  
  
##  <a name="buildroot"></a>  CPathT::BuildRoot  
 调用此方法以从给定的驱动器号创建根路径。  
  
```
void BuildRoot(int iDrive);
```  
  
### <a name="parameters"></a>参数  
 *iDrive*  
 驱动器数量 （0 表示答:，1 是 b:，依此类推）。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567)。  
  
##  <a name="canonicalize"></a>  CPathT::Canonicalize  
 调用此方法将路径转换为规范化形式。  
  
```
void Canonicalize();
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569)。  
  
##  <a name="combine"></a>  CPathT::Combine  
 调用此方法来连接表示目录名称的字符串和一个到一个路径表示文件路径名称的字符串。  
  
```
void Combine(PCXSTR pszDir, PCXSTR  pszFile);
```  
  
### <a name="parameters"></a>参数  
 *pszDir*  
 目录路径中。  
  
 *pszFile*  
 文件路径中。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathCombine](http://msdn.microsoft.com/library/windows/desktop/bb773571)。  
  
##  <a name="commonprefix"></a>  CPathT::CommonPrefix  
 调用此方法以确定指定的路径是否与当前路径共享公共前缀。  
  
```
CPathT<StringType> CommonPrefix(PCXSTR pszOther);
```  
  
### <a name="parameters"></a>参数  
 *pszOther*  
 要比较为当前的路径。  
  
### <a name="return-value"></a>返回值  
 返回的通用前缀。  
  
### <a name="remarks"></a>备注  
 前缀是这些类型之一:"c:\\\\"，"。"，"..."，"...\\\\". 有关详细信息，请参阅[PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574)。  
  
##  <a name="compactpath"></a>  CPathT::CompactPath  
 调用此方法来截断以适合给定的像素宽度由路径组件替换为省略号的文件路径。  
  
```
BOOL CompactPath(HDC hDC, UINT nWidth);
```  
  
### <a name="parameters"></a>参数  
 *hDC*  
 使用的字体规格的设备上下文。  
  
 *nWidth*  
 宽度，以像素为单位，将强制在字符串中容纳不下。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575)。  
  
##  <a name="compactpathex"></a>  CPathT::CompactPathEx  
 调用此方法来截断以适合给定数目的字符的路径组件替换为省略号的文件路径。  
  
```
BOOL CompactPathEx(UINT nMaxChars, DWORD dwFlags = 0);
```  
  
### <a name="parameters"></a>参数  
 *nMaxChars*  
 要包含在包括终止 NULL 字符的新字符串的字符数目上限。  
  
 *dwFlags*  
 保留。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578)。  
  
##  <a name="cpatht"></a>  CPathT::CPathT  
 构造函数。  
  
```
CPathT(PCXSTR pszPath);
CPathT(const CPathT<StringType>& path);
CPathT() throw();
```  
  
### <a name="parameters"></a>参数  
 *pszPath*  
 指向的路径字符串的指针。  
  
 *path*  
 路径字符串中。  
  
##  <a name="fileexists"></a>  CPathT::FileExists  
 调用此方法来检查是否存在，此路径名称中的文件。  
  
```
BOOL FileExists() const;
```  
  
### <a name="return-value"></a>返回值  
 如果该文件存在，则返回 FALSE 否则，则返回 TRUE。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584)。  
  
##  <a name="findextension"></a>  CPathT::FindExtension  
 调用此方法来查找在该路径的文件扩展名的位置。  
  
```
int FindExtension() const;
```  
  
### <a name="return-value"></a>返回值  
 返回的位置"。"前面的扩展。 如果不找到任何扩展，则返回-1。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587)。  
  
##  <a name="findfilename"></a>  CPathT::FindFileName  
 调用此方法来查找在该路径的文件名称的位置。  
  
```
int FindFileName() const;
```  
  
### <a name="return-value"></a>返回值  
 返回文件名称的位置。 如果不找到任何文件名称，则返回-1。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589)。  
  
##  <a name="getdrivenumber"></a>  CPathT::GetDriveNumber  
 调用此方法来搜索的 A 到 Z 范围内的驱动器号的路径，并返回相应的驱动器号。  
  
```
int GetDriveNumber() const;
```  
  
### <a name="return-value"></a>返回值  
 驱动器号作为整数返回从 0 到 25 （对应于 A 到 Z） 如果该路径否则包含驱动器号，则为-1。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612)。  
  
##  <a name="getextension"></a>  CPathT::GetExtension  
 调用此方法以从路径获取文件扩展名。  
  
```
StringType GetExtension() const;
```  
  
### <a name="return-value"></a>返回值  
 返回的文件扩展名。  
  
##  <a name="isdirectory"></a>  CPathT::IsDirectory  
 调用此方法来检查路径是否是有效的目录。  
  
```
BOOL IsDirectory() const;
```  
  
### <a name="return-value"></a>返回值  
 如果路径是目录，则返回 FALSE 否则，返回非零值 (16)。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathIsDirectory](http://msdn.microsoft.com/library/windows/desktop/bb773621)。  
  
##  <a name="isfilespec"></a>  CPathT::IsFileSpec  
 调用此方法来搜索任何路径分隔字符的路径 (例如，':' 或 '\\)。 如果存在任何路径分隔字符，被考虑使用该路径为文件规范路径。  
  
```
BOOL IsFileSpec() const;
```  
  
### <a name="return-value"></a>返回值  
 如果没有路径分隔字符，在该路径，则为 TRUE 或 FALSE 路径分隔字符是否返回。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627)。  
  
##  <a name="isprefix"></a>  CPathT::IsPrefix  
 调用此方法来确定路径是否包含所传递类型的有效前缀*pszPrefix*。  
  
```
BOOL IsPrefix(PCXSTR pszPrefix) const;
```  
  
### <a name="parameters"></a>参数  
 *pszPrefix*  
 要搜索前缀。 前缀是这些类型之一:"c:\\\\"，"。"，"..."，"...\\\\".  
  
### <a name="return-value"></a>返回值  
 如果路径中包含 FALSE 的前缀，否则，则返回 TRUE。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650)。  
  
##  <a name="isrelative"></a>  CPathT::IsRelative  
 调用此方法以确定该路径是相对。  
  
```
BOOL IsRelative() const;
```  
  
### <a name="return-value"></a>返回值  
 如果该路径是相对或 FALSE，如果它是绝对路径，则返回 TRUE。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660)。  
  
##  <a name="isroot"></a>  CPathT::IsRoot  
 调用此方法来确定路径是目录的根目录。  
  
```
BOOL IsRoot() const;
```  
  
### <a name="return-value"></a>返回值  
 如果该路径否则是 root 或 FALSE，则返回 TRUE。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674)。  
  
##  <a name="issameroot"></a>  CPathT::IsSameRoot  
 调用此方法来确定另一个路径是否具有当前路径的常见根组件。  
  
```
BOOL IsSameRoot(PCXSTR pszOther) const;
```  
  
### <a name="parameters"></a>参数  
 *pszOther*  
 另一条路径。  
  
### <a name="return-value"></a>返回值  
 如果这两个字符串否则具有相同的根组件或 FALSE，则返回 TRUE。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687)。  
  
##  <a name="isunc"></a>  CPathT::IsUNC  
 调用此方法来确定路径是否有效的 UNC （通用命名约定） 路径的服务器和共享。  
  
```
BOOL IsUNC() const;
```  
  
### <a name="return-value"></a>返回值  
 如果该路径是有效的 UNC 路径或 FALSE 否则，返回 TRUE。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712)。  
  
##  <a name="isuncserver"></a>  CPathT::IsUNCServer  
 调用此方法来确定路径是否只能为服务器的有效 UNC （通用命名约定） 路径。  
  
```
BOOL IsUNCServer() const;
```  
  
### <a name="return-value"></a>返回值  
 如果字符串是有效的 UNC 路径仅限服务器 （无共享名称） 或 FALSE 否则，则返回 TRUE。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722)。  
  
##  <a name="isuncservershare"></a>  CPathT::IsUNCServerShare  
 调用此方法来确定路径是否有效的 UNC （通用命名约定） 共享路径， \\ \ *服务器*\ *共享*。  
  
```
BOOL IsUNCServerShare() const;
```  
  
### <a name="return-value"></a>返回值  
 如果该路径是在窗体中，则返回 TRUE \\ \ *服务器*\ *共享*，或 FALSE 否则为。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723)。  
  
##  <a name="m_strpath"></a>  CPathT::m_strPath  
 路径。  
  
```
StringType m_strPath;
```  
  
### <a name="remarks"></a>备注  
 `StringType` 是模板参数到`CPathT`。  
  
##  <a name="makepretty"></a>  CPathT::MakePretty  
 调用此方法以将路径转换为所有小写字符，以提供一致的外观的路径。  
  
```
BOOL MakePretty();
```  
  
### <a name="return-value"></a>返回值  
 否则返回已转换的路径，如果为 TRUE 或 FALSE。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725)。  
  
##  <a name="matchspec"></a>  CPathT::MatchSpec  
 调用此方法搜索的路径包含通配符匹配类型的字符串。  
  
```
BOOL MatchSpec(PCXSTR pszSpec) const;
```  
  
### <a name="parameters"></a>参数  
 *pszSpec*  
 与要搜索的文件类型的以 null 结尾的字符串指针。 例如，若要测试是否在当前路径的文件为文档文件， *pszSpec*应设置为"*.doc"。  
  
### <a name="return-value"></a>返回值  
 否则返回的字符串与匹配，如果为 TRUE 或 FALSE。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727)。  
  
##  <a name="operator_add_eq"></a>  CPathT::operator + =  
 此运算符将字符串追加到路径。  
  
```
CPathT<StringType>& operator+=(PCXSTR pszMore);
```  
  
### <a name="parameters"></a>参数  
 *pszMore*  
 要追加的字符串。  
  
### <a name="return-value"></a>返回值  
 返回已更新的路径。  
  
##  <a name="operator_const_stringtype_amp"></a>  CPathT::operator const StringType &amp;  
 此运算符使对象可以被视为字符串。  
  
```
 operatorconst StringType&() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回表示此对象管理的当前路径的字符串。  
  
##  <a name="operator_cpatht__pcxstr"></a>  CPathT::operator CPathT::PCXSTR  
 此运算符使对象可以被视为字符串。  
  
```
 operatorPCXSTR() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回表示此对象管理的当前路径的字符串。  
  
##  <a name="operator_stringtype__amp"></a>  CPathT::operator StringType &amp;  
 此运算符使对象可以被视为字符串。  
  
```
 operatorStringType&() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回表示此对象管理的当前路径的字符串。  
  
##  <a name="pcxstr"></a>  CPathT::PCXSTR  
 常量字符串类型。  
  
```
typedef StringType::PCXSTR PCXSTR;
```  
  
### <a name="remarks"></a>备注  
 `StringType` 是模板参数到`CPathT`。  
  
##  <a name="pxstr"></a>  CPathT::PXSTR  
 字符串类型。  
  
```
typedef StringType::PXSTR PXSTR;
```  
  
### <a name="remarks"></a>备注  
 `StringType` 是模板参数到`CPathT`。  
  
##  <a name="quotespaces"></a>  CPathT::QuoteSpaces  
 调用此方法以将该路径括在引号中，如果它包含任何空格。  
  
```
void QuoteSpaces();
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739)。  
  
##  <a name="relativepathto"></a>  CPathT::RelativePathTo  
 调用此方法创建的相对路径从一个文件或文件夹。  
  
```
BOOL RelativePathTo(
    PCXSTR pszFrom,
    DWORD dwAttrFrom,
    PCXSTR pszTo,
    DWORD dwAttrTo);
```  
  
### <a name="parameters"></a>参数  
 *pszFrom*  
 相对路径的开头。  
  
 *dwAttrFrom*  
 文件属性*pszFrom*。 如果此值包含 FILE_ATTRIBUTE_DIRECTORY， *pszFrom*假定是一个目录; 否则为*pszFrom*被假定为一个文件。  
  
 *pszTo*  
 相对路径的终结点。  
  
 *dwAttrTo*  
 文件属性*pszTo*。 如果此值包含 FILE_ATTRIBUTE_DIRECTORY， *pszTo*假定是一个目录; 否则为*pszTo*被假定为一个文件。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740)。  
  
##  <a name="removeargs"></a>  CPathT::RemoveArgs  
 调用此方法以从路径中删除任何命令行参数。  
  
```
void RemoveArgs();
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742)。  
  
##  <a name="removebackslash"></a>  CPathT::RemoveBackslash  
 调用此方法以从路径中删除尾随反斜杠。  
  
```
void RemoveBackslash();
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743)。  
  
##  <a name="removeblanks"></a>  CPathT::RemoveBlanks  
 调用此方法以从路径中删除所有前导和尾随空格。  
  
```
void RemoveBlanks();
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745)。  
  
##  <a name="removeextension"></a>  CPathT::RemoveExtension  
 如果有，则调用此方法以从路径中，删除文件扩展名。  
  
```
void RemoveExtension();
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746)。  
  
##  <a name="removefilespec"></a>  CPathT::RemoveFileSpec  
 它是否调用此方法以从路径中删除尾随的文件名和反斜杠。  
  
```
BOOL RemoveFileSpec();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748)。  
  
##  <a name="renameextension"></a>  CPathT::RenameExtension  
 调用此方法将在路径中的文件扩展名替换为一个新的扩展。 如果文件名称不包含扩展，扩展将附加到路径的末尾。  
  
```
BOOL RenameExtension(PCXSTR pszExtension);
```  
  
### <a name="parameters"></a>参数  
 *pszExtension*  
 新的文件扩展名，前面有"。"字符。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749)。  
  
##  <a name="skiproot"></a>  CPathT::SkipRoot  
 调用此方法来分析忽略驱动器号或 UNC （通用命名约定） 路径部分服务器/共享的路径。  
  
```
int SkipRoot() const;
```  
  
### <a name="return-value"></a>返回值  
 返回遵循 （驱动器号或 UNC 服务器/共享） 的根的子路径的开头位置。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754)。  
  
##  <a name="strippath"></a>  CPathT::StripPath  
 调用此方法，若要删除的完全限定的路径和文件名的路径部分。  
  
```
void StripPath();
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756)。  
  
##  <a name="striptoroot"></a>  CPathT::StripToRoot  
 调用此方法来删除除根信息的路径的所有部分。  
  
```
BOOL StripToRoot();
```  
  
### <a name="return-value"></a>返回值  
 返回 TRUE，如果有效的驱动器号找否则在路径中，或 FALSE。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757)。  
  
##  <a name="unquotespaces"></a>  CPathT::UnquoteSpaces  
 调用此方法的开头和结尾的路径中删除引号标记。  
  
```
void UnquoteSpaces();
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763)。  
  
##  <a name="xchar"></a>  CPathT::XCHAR  
 一个字符类型。  
  
```
typedef StringType::XCHAR XCHAR;
```  
  
### <a name="remarks"></a>备注  
 `StringType` 是模板参数到`CPathT`。  
  
## <a name="see-also"></a>请参阅  
 [类](../../atl/reference/atl-classes.md)   
 [CStringT 类](../../atl-mfc-shared/reference/cstringt-class.md)