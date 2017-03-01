---
title: "CPathT 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CPathT
- CPathT
- ATL::CPathT<StringType>
- ATL::CPathT
- ATL.CPathT<StringType>
dev_langs:
- C++
helpviewer_keywords:
- CPathT class
ms.assetid: eba4137d-1fd2-4b44-a2e1-0944db64df3c
caps.latest.revision: 20
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
ms.openlocfilehash: 8cbd91ae1c4318788b38b2daaa7721d1a29fca98
ms.lasthandoff: 02/24/2017

---
# <a name="cpatht-class"></a>CPathT 类
此类表示一个路径。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
template <typename StringType>
class CPathT
```  
  
#### <a name="parameters"></a>参数  
 `StringType`  
 ATL/MFC 字符串类使用的路径 (请参阅[CStringT](../../atl-mfc-shared/reference/cstringt-class.md))。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|说明|  
|----------|-----------------|  
|[CPathT::PCXSTR](#pcxstr)|一个常量字符串类型。|  
|[CPathT::PXSTR](#pxstr)|String 类型。|  
|[CPathT::XCHAR](#xchar)|一种字符类型。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CPathT::CPathT](#cpatht)|构造函数中的路径。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CPathT::AddBackslash](#addbackslash)|调用此方法以创建一个路径的正确语法的字符串的末尾添加反斜杠。|  
|[CPathT::AddExtension](#addextension)|调用此方法以将文件扩展名添加到的路径。|  
|[CPathT::Append](#append)|调用此方法以将一个字符串追加到当前路径。|  
|[CPathT::BuildRoot](#buildroot)|调用此方法从给定的驱动器号创建根路径。|  
|[CPathT::Canonicalize](#canonicalize)|调用此方法将路径转换为规范化格式。|  
|[CPathT::Combine](#combine)|调用此方法以将表示目录名称的字符串和一个到一条路径表示的文件路径名称的字符串连接起来。|  
|[CPathT::CommonPrefix](#commonprefix)|调用此方法以确定指定的路径是否为当前路径共享一个通用前缀。|  
|[CPathT::CompactPath](#compactpath)|调用此方法来截断以通过路径组件替换为省略号适合给定的像素宽度的文件路径。|  
|[CPathT::CompactPathEx](#compactpathex)|调用此方法来截断以适合通过路径组件替换为省略号给定数量的字符的文件路径。|  
|[CPathT::FileExists](#fileexists)|调用此方法以检查是否存在此路径名称中的文件。|  
|[CPathT::FindExtension](#findextension)|调用此方法找到文件扩展名的路径中的位置。|  
|[CPathT::FindFileName](#findfilename)|调用此方法以查找在该路径的文件名的位置。|  
|[CPathT::GetDriveNumber](#getdrivenumber)|调用此方法来搜索的 A 到 Z 范围内的驱动器号的路径并返回相应的驱动器号。|  
|[CPathT::GetExtension](#getextension)|调用此方法以获取文件扩展名的路径。|  
|[CPathT::IsDirectory](#isdirectory)|调用此方法来检查路径是否是有效的目录。|  
|[CPathT::IsFileSpec](#isfilespec)|调用此方法来搜索路径分隔的任何字符的路径 (例如，':' 或 '\\)。 如果存在任何路径分隔字符，该路径被认为可以文件规范路径。|  
|[CPathT::IsPrefix](#isprefix)|调用此方法来确定路径是否包含由传递的类型的有效前缀`pszPrefix`。|  
|[CPathT::IsRelative](#isrelative)|调用此方法以确定是相对路径。|  
|[CPathT::IsRoot](#isroot)|调用此方法来确定该路径是目录的根目录。|  
|[CPathT::IsSameRoot](#issameroot)|调用此方法以确定是否另一条路径具有公共根组件与当前路径。|  
|[CPathT::IsUNC](#isunc)|调用此方法来确定路径是否有效的 UNC （通用命名约定） 路径的服务器和共享。|  
|[CPathT::IsUNCServer](#isuncserver)|调用此方法以确定路径是否只能为服务器的有效 UNC （通用命名约定） 路径。|  
|[CPathT::IsUNCServerShare](#isuncservershare)|调用此方法来确定路径是否有效的 UNC （通用命名约定） 共享路径， \\ \ *服务器*\ *共享*。|  
|[CPathT::MakePretty](#makepretty)|调用此方法将路径转换为所有小写字符，以提供一致的外观的路径。|  
|[CPathT::MatchSpec](#matchspec)|调用此方法来搜索包含通配符匹配类型的字符串的路径。|  
|[CPathT::QuoteSpaces](#quotespaces)|调用此方法以将路径括在引号中，如果它包含任何空格。|  
|[CPathT::RelativePathTo](#relativepathto)|调用此方法来从一个文件或文件夹的相对路径创建指向另一个。|  
|[CPathT::RemoveArgs](#removeargs)|调用此方法以从路径中删除任何命令行参数。|  
|[CPathT::RemoveBackslash](#removebackslash)|调用此方法以从路径中删除尾部反斜杠。|  
|[CPathT::RemoveBlanks](#removeblanks)|调用此方法以从路径中删除所有前导和尾随空格。|  
|[CPathT::RemoveExtension](#removeextension)|如果存在，则调用此方法以从路径中，删除的文件扩展名。|  
|[CPathT::RemoveFileSpec](#removefilespec)|它是否调用此方法以从路径中，删除尾随的文件名和反斜杠。|  
|[CPathT::RenameExtension](#renameextension)|调用此方法将替换为一个新的扩展路径中的文件扩展名。 如果文件名不包含扩展名，该扩展将附加到字符串的末尾。|  
|[CPathT::SkipRoot](#skiproot)|调用此方法来分析忽略驱动器号或 UNC 路径部分服务器/共享的路径。|  
|[CPathT::StripPath](#strippath)|调用此方法来删除的完全限定的路径和文件名的路径部分。|  
|[CPathT::StripToRoot](#striptoroot)|调用此方法来删除除根目录信息的路径的所有部分。|  
|[CPathT::UnquoteSpaces](#unquotespaces)|调用此方法以开头和结尾的路径中删除引号标记。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CPathT::operator const StringType.](#operator_const_stringtype_amp)|此运算符使对象可以被当作一个字符串。|  
|[CPathT::operator CPathT::PCXSTR](#operator_cpatht__pcxstr)|此运算符使对象可以被当作一个字符串。|  
|[CPathT::operator StringType.](#operator_stringtype)|此运算符使对象可以被当作一个字符串。|  
|[CPathT::operator + =](#operator_add_eq)|此运算符将一个字符串追加到的路径。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CPathT::m_strPath](#m_strpath)|路径。|  
  
## <a name="remarks"></a>备注  
 `CPath``CPathA`，和`CPathW`是实例化的`CPathT`定义，如下所示︰  
  
 `typedef CPathT< CString > CPath;`  
  
 `typedef CPathT< CStringA > CPathA;`  
  
 `typedef CPathT< CStringW > CPathW;`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlpath.h  
  
##  <a name="a-nameaddbackslasha--cpathtaddbackslash"></a><a name="addbackslash"></a>CPathT::AddBackslash  
 调用此方法以创建一个路径的正确语法的字符串的末尾添加反斜杠。 如果该路径已具有尾部反斜杠，则将添加没有反斜杠。  
  
```
void AddBackslash();
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathAddBackSlash](http://msdn.microsoft.com/library/windows/desktop/bb773561)。  
  
##  <a name="a-nameaddextensiona--cpathtaddextension"></a><a name="addextension"></a>CPathT::AddExtension  
 调用此方法以将文件扩展名添加到的路径。  
  
```
BOOL AddExtension(PCXSTR pszExtension);
```  
  
### <a name="parameters"></a>参数  
 `pszExtension`  
 要添加的文件扩展名。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563)。  
  
##  <a name="a-nameappenda--cpathtappend"></a><a name="append"></a>CPathT::Append  
 调用此方法以将一个字符串追加到当前路径。  
  
```
BOOL Append(PCXSTR pszMore);
```  
  
### <a name="parameters"></a>参数  
 `pszMore`  
 要追加的字符串。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565)。  
  
##  <a name="a-namebuildroota--cpathtbuildroot"></a><a name="buildroot"></a>CPathT::BuildRoot  
 调用此方法从给定的驱动器号创建根路径。  
  
```
void BuildRoot(int iDrive);
```  
  
### <a name="parameters"></a>参数  
 *iDrive*  
 驱动器数量 （0 表示 a:，1 是 b:，依此类推）。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567)。  
  
##  <a name="a-namecanonicalizea--cpathtcanonicalize"></a><a name="canonicalize"></a>CPathT::Canonicalize  
 调用此方法将路径转换为规范化格式。  
  
```
void Canonicalize();
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569)。  
  
##  <a name="a-namecombinea--cpathtcombine"></a><a name="combine"></a>CPathT::Combine  
 调用此方法以将表示目录名称的字符串和一个到一条路径表示的文件路径名称的字符串连接起来。  
  
```
void Combine(PCXSTR pszDir, PCXSTR  pszFile);
```  
  
### <a name="parameters"></a>参数  
 `pszDir`  
 目录路径中。  
  
 *pszFile*  
 文件路径中。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathCombine](http://msdn.microsoft.com/library/windows/desktop/bb773571)。  
  
##  <a name="a-namecommonprefixa--cpathtcommonprefix"></a><a name="commonprefix"></a>CPathT::CommonPrefix  
 调用此方法以确定指定的路径是否为当前路径共享一个通用前缀。  
  
```
CPathT<StringType> CommonPrefix(PCXSTR pszOther);
```  
  
### <a name="parameters"></a>参数  
 `pszOther`  
 要与当前进行比较的路径。  
  
### <a name="return-value"></a>返回值  
 返回的通用前缀。  
  
### <a name="remarks"></a>备注  
 前缀为这些类型之一:"c:\\\\"，"。"，".."，"...\\\\". 有关详细信息，请参阅[PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574)。  
  
##  <a name="a-namecompactpatha--cpathtcompactpath"></a><a name="compactpath"></a>CPathT::CompactPath  
 调用此方法来截断以通过路径组件替换为省略号适合给定的像素宽度的文件路径。  
  
```
BOOL CompactPath(HDC hDC, UINT nWidth);
```  
  
### <a name="parameters"></a>参数  
 `hDC`  
 用于字体规格的设备上下文。  
  
 `nWidth`  
 宽度，以像素为单位，将强制该字符串中容纳不下。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575)。  
  
##  <a name="a-namecompactpathexa--cpathtcompactpathex"></a><a name="compactpathex"></a>CPathT::CompactPathEx  
 调用此方法来截断以适合通过路径组件替换为省略号给定数量的字符的文件路径。  
  
```
BOOL CompactPathEx(UINT nMaxChars, DWORD dwFlags = 0);
```  
  
### <a name="parameters"></a>参数  
 `nMaxChars`  
 最大字符要包含在新的字符串，包括终止 NULL 字符数。  
  
 `dwFlags`  
 保留。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578)。  
  
##  <a name="a-namecpathta--cpathtcpatht"></a><a name="cpatht"></a>CPathT::CPathT  
 构造函数。  
  
```
CPathT(PCXSTR pszPath);
CPathT(const CPathT<StringType>& path);
CPathT() throw();
```  
  
### <a name="parameters"></a>参数  
 *pszPath*  
 指向将路径字符串的指针。  
  
 *path*  
 路径字符串中。  
  
##  <a name="a-namefileexistsa--cpathtfileexists"></a><a name="fileexists"></a>CPathT::FileExists  
 调用此方法以检查是否存在此路径名称中的文件。  
  
```
BOOL FileExists() const;
```  
  
### <a name="return-value"></a>返回值  
 如果该文件存在，则返回 FALSE 否则，则返回 TRUE。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584)。  
  
##  <a name="a-namefindextensiona--cpathtfindextension"></a><a name="findextension"></a>CPathT::FindExtension  
 调用此方法找到文件扩展名的路径中的位置。  
  
```
int FindExtension() const;
```  
  
### <a name="return-value"></a>返回值  
 返回的位置"。"前面的扩展。 如果不找到任何扩展，则返回-1。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587)。  
  
##  <a name="a-namefindfilenamea--cpathtfindfilename"></a><a name="findfilename"></a>CPathT::FindFileName  
 调用此方法以查找在该路径的文件名的位置。  
  
```
int FindFileName() const;
```  
  
### <a name="return-value"></a>返回值  
 返回的文件名的位置。 如果不找到任何文件的名称，则返回 –&1;。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589)。  
  
##  <a name="a-namegetdrivenumbera--cpathtgetdrivenumber"></a><a name="getdrivenumber"></a>CPathT::GetDriveNumber  
 调用此方法来搜索的 A 到 Z 范围内的驱动器号的路径并返回相应的驱动器号。  
  
```
int GetDriveNumber() const;
```  
  
### <a name="return-value"></a>返回值  
 返回驱动器号作为一个整数，介于 0 到 25 （对应于 A 到 Z） 如果该路径否则包含驱动器号，则为-1。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612)。  
  
##  <a name="a-namegetextensiona--cpathtgetextension"></a><a name="getextension"></a>CPathT::GetExtension  
 调用此方法以获取文件扩展名的路径。  
  
```
StringType GetExtension() const;
```  
  
### <a name="return-value"></a>返回值  
 返回的文件扩展名。  
  
##  <a name="a-nameisdirectorya--cpathtisdirectory"></a><a name="isdirectory"></a>CPathT::IsDirectory  
 调用此方法来检查路径是否是有效的目录。  
  
```
BOOL IsDirectory() const;
```  
  
### <a name="return-value"></a>返回值  
 如果路径是目录，则返回非零值 (16)`FALSE`否则为。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathIsDirectory](http://msdn.microsoft.com/library/windows/desktop/bb773621)。  
  
##  <a name="a-nameisfilespeca--cpathtisfilespec"></a><a name="isfilespec"></a>CPathT::IsFileSpec  
 调用此方法来搜索路径分隔的任何字符的路径 (例如，':' 或 '\\)。 如果存在任何路径分隔字符，该路径被认为可以文件规范路径。  
  
```
BOOL IsFileSpec() const;
```  
  
### <a name="return-value"></a>返回值  
 如果没有路径分隔字符，在该路径，则为 TRUE 或 FALSE 路径分隔字符是否返回。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627)。  
  
##  <a name="a-nameisprefixa--cpathtisprefix"></a><a name="isprefix"></a>CPathT::IsPrefix  
 调用此方法来确定路径是否包含由传递的类型的有效前缀`pszPrefix`。  
  
```
BOOL IsPrefix(PCXSTR pszPrefix) const;
```  
  
### <a name="parameters"></a>参数  
 `pszPrefix`  
 要搜索前缀。 前缀为这些类型之一:"c:\\\\"，"。"，".."，"...\\\\".  
  
### <a name="return-value"></a>返回值  
 如果路径中包含 FALSE 的前缀，否则，则返回 TRUE。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650)。  
  
##  <a name="a-nameisrelativea--cpathtisrelative"></a><a name="isrelative"></a>CPathT::IsRelative  
 调用此方法以确定是相对路径。  
  
```
BOOL IsRelative() const;
```  
  
### <a name="return-value"></a>返回值  
 如果路径为相对值，则或 FALSE，如果它是绝对路径，则返回 TRUE。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660)。  
  
##  <a name="a-nameisroota--cpathtisroot"></a><a name="isroot"></a>CPathT::IsRoot  
 调用此方法来确定该路径是目录的根目录。  
  
```
BOOL IsRoot() const;
```  
  
### <a name="return-value"></a>返回值  
 如果该路径否则是根或 FALSE，则返回 TRUE。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674)。  
  
##  <a name="a-nameissameroota--cpathtissameroot"></a><a name="issameroot"></a>CPathT::IsSameRoot  
 调用此方法以确定是否另一条路径具有公共根组件与当前路径。  
  
```
BOOL IsSameRoot(PCXSTR pszOther) const;
```  
  
### <a name="parameters"></a>参数  
 `pszOther`  
 另一条路径。  
  
### <a name="return-value"></a>返回值  
 如果这两个字符串否则具有相同的根组件或 FALSE，则返回 TRUE。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687)。  
  
##  <a name="a-nameisunca--cpathtisunc"></a><a name="isunc"></a>CPathT::IsUNC  
 调用此方法来确定路径是否有效的 UNC （通用命名约定） 路径的服务器和共享。  
  
```
BOOL IsUNC() const;
```  
  
### <a name="return-value"></a>返回值  
 如果该路径是有效的 UNC 路径或 FALSE 否则，返回 TRUE。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712)。  
  
##  <a name="a-nameisuncservera--cpathtisuncserver"></a><a name="isuncserver"></a>CPathT::IsUNCServer  
 调用此方法以确定路径是否只能为服务器的有效 UNC （通用命名约定） 路径。  
  
```
BOOL IsUNCServer() const;
```  
  
### <a name="return-value"></a>返回值  
 如果字符串是有效的 UNC 路径只能为服务器 （没有共享名称） 或 FALSE 否则，则返回 TRUE。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722)。  
  
##  <a name="a-nameisuncserversharea--cpathtisuncservershare"></a><a name="isuncservershare"></a>CPathT::IsUNCServerShare  
 调用此方法来确定路径是否有效的 UNC （通用命名约定） 共享路径， \\ \ *服务器*\ *共享*。  
  
```
BOOL IsUNCServerShare() const;
```  
  
### <a name="return-value"></a>返回值  
 如果该路径是在窗体，则返回 TRUE \\ \ *服务器*\ *共享*，或假否则为。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723)。  
  
##  <a name="a-namemstrpatha--cpathtmstrpath"></a><a name="m_strpath"></a>CPathT::m_strPath  
 路径。  
  
```
StringType m_strPath;
```  
  
### <a name="remarks"></a>备注  
 `StringType`为模板参数`CPathT`。  
  
##  <a name="a-namemakeprettya--cpathtmakepretty"></a><a name="makepretty"></a>CPathT::MakePretty  
 调用此方法将路径转换为所有小写字符，以提供一致的外观的路径。  
  
```
BOOL MakePretty();
```  
  
### <a name="return-value"></a>返回值  
 否则，返回如果被转换路径，则为 TRUE 或 FALSE。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725)。  
  
##  <a name="a-namematchspeca--cpathtmatchspec"></a><a name="matchspec"></a>CPathT::MatchSpec  
 调用此方法来搜索包含通配符匹配类型的字符串的路径。  
  
```
BOOL MatchSpec(PCXSTR pszSpec) const;
```  
  
### <a name="parameters"></a>参数  
 `pszSpec`  
 以 null 结尾的字符串与要搜索的文件类型的指针。 例如，若要测试是否位于当前路径的文件是 DOC 文件，`pszSpec`应设置为"*.doc"。  
  
### <a name="return-value"></a>返回值  
 否则，返回的字符串与匹配，如果为 TRUE 或 FALSE。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727)。  
  
##  <a name="a-nameoperatoraddeqa--cpathtoperator-"></a><a name="operator_add_eq"></a>CPathT::operator + =  
 此运算符将一个字符串追加到的路径。  
  
```
CPathT<StringType>& operator+=(PCXSTR pszMore);
```  
  
### <a name="parameters"></a>参数  
 `pszMore`  
 要追加的字符串。  
  
### <a name="return-value"></a>返回值  
 返回的已更新的路径。  
  
##  <a name="a-nameoperatorconststringtypeampa--cpathtoperator-const-stringtype-amp"></a><a name="operator_const_stringtype_amp"></a>CPathT::operator const StringType&amp;  
 此运算符使对象可以被当作一个字符串。  
  
```
 operatorconst StringType&() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回表示由该对象的当前路径的字符串。  
  
##  <a name="a-nameoperatorcpathtpcxstra--cpathtoperator-cpathtpcxstr"></a><a name="operator_cpatht__pcxstr"></a>CPathT::operator CPathT::PCXSTR  
 此运算符使对象可以被当作一个字符串。  
  
```
 operatorPCXSTR() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回表示由该对象的当前路径的字符串。  
  
##  <a name="a-nameoperatorstringtypeampa--cpathtoperator-stringtype-amp"></a><a name="operator_stringtype__amp"></a>CPathT::operator StringType&amp;  
 此运算符使对象可以被当作一个字符串。  
  
```
 operatorStringType&() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回表示由该对象的当前路径的字符串。  
  
##  <a name="a-namepcxstra--cpathtpcxstr"></a><a name="pcxstr"></a>CPathT::PCXSTR  
 一个常量字符串类型。  
  
```
typedef StringType::PCXSTR PCXSTR;
```  
  
### <a name="remarks"></a>备注  
 `StringType`为模板参数`CPathT`。  
  
##  <a name="a-namepxstra--cpathtpxstr"></a><a name="pxstr"></a>CPathT::PXSTR  
 String 类型。  
  
```
typedef StringType::PXSTR PXSTR;
```  
  
### <a name="remarks"></a>备注  
 `StringType`为模板参数`CPathT`。  
  
##  <a name="a-namequotespacesa--cpathtquotespaces"></a><a name="quotespaces"></a>CPathT::QuoteSpaces  
 调用此方法以将路径括在引号中，如果它包含任何空格。  
  
```
void QuoteSpaces();
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739)。  
  
##  <a name="a-namerelativepathtoa--cpathtrelativepathto"></a><a name="relativepathto"></a>CPathT::RelativePathTo  
 调用此方法来从一个文件或文件夹的相对路径创建指向另一个。  
  
```
BOOL RelativePathTo(
    PCXSTR pszFrom,
    DWORD dwAttrFrom,
    PCXSTR pszTo,
    DWORD dwAttrTo);
```  
  
### <a name="parameters"></a>参数  
 `pszFrom`  
 相对路径的开头。  
  
 *dwAttrFrom*  
 文件属性的`pszFrom`。 如果此值包含 FILE_ATTRIBUTE_DIRECTORY，`pszFrom`假定是一个目录; 否则为`pszFrom`被假定为一个文件。  
  
 `pszTo`  
 相对路径的终结点。  
  
 *dwAttrTo*  
 文件属性的`pszTo`。 如果此值包含 FILE_ATTRIBUTE_DIRECTORY，`pszTo`假定是一个目录; 否则为`pszTo`被假定为一个文件。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740)。  
  
##  <a name="a-nameremoveargsa--cpathtremoveargs"></a><a name="removeargs"></a>CPathT::RemoveArgs  
 调用此方法以从路径中删除任何命令行参数。  
  
```
void RemoveArgs();
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742)。  
  
##  <a name="a-nameremovebackslasha--cpathtremovebackslash"></a><a name="removebackslash"></a>CPathT::RemoveBackslash  
 调用此方法以从路径中删除尾部反斜杠。  
  
```
void RemoveBackslash();
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743)。  
  
##  <a name="a-nameremoveblanksa--cpathtremoveblanks"></a><a name="removeblanks"></a>CPathT::RemoveBlanks  
 调用此方法以从路径中删除所有前导和尾随空格。  
  
```
void RemoveBlanks();
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745)。  
  
##  <a name="a-nameremoveextensiona--cpathtremoveextension"></a><a name="removeextension"></a>CPathT::RemoveExtension  
 如果存在，则调用此方法以从路径中，删除的文件扩展名。  
  
```
void RemoveExtension();
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746)。  
  
##  <a name="a-nameremovefilespeca--cpathtremovefilespec"></a><a name="removefilespec"></a>CPathT::RemoveFileSpec  
 它是否调用此方法以从路径中，删除尾随的文件名和反斜杠。  
  
```
BOOL RemoveFileSpec();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748)。  
  
##  <a name="a-namerenameextensiona--cpathtrenameextension"></a><a name="renameextension"></a>CPathT::RenameExtension  
 调用此方法将替换为一个新的扩展路径中的文件扩展名。 如果文件名不包含扩展名，该扩展将附加到路径的末尾。  
  
```
BOOL RenameExtension(PCXSTR pszExtension);
```  
  
### <a name="parameters"></a>参数  
 `pszExtension`  
 新的文件扩展名，前面有"。"字符。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749)。  
  
##  <a name="a-nameskiproota--cpathtskiproot"></a><a name="skiproot"></a>CPathT::SkipRoot  
 调用此方法来分析忽略驱动器号或 UNC （通用命名约定） 路径部分服务器/共享的路径。  
  
```
int SkipRoot() const;
```  
  
### <a name="return-value"></a>返回值  
 返回的后面 （驱动器号或 UNC 服务器/共享） 的根的子路径开头的位置。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754)。  
  
##  <a name="a-namestrippatha--cpathtstrippath"></a><a name="strippath"></a>CPathT::StripPath  
 调用此方法来删除的完全限定的路径和文件名的路径部分。  
  
```
void StripPath();
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756)。  
  
##  <a name="a-namestriptoroota--cpathtstriptoroot"></a><a name="striptoroot"></a>CPathT::StripToRoot  
 调用此方法来删除除根目录信息的路径的所有部分。  
  
```
BOOL StripToRoot();
```  
  
### <a name="return-value"></a>返回值  
 如果有效的驱动器号，则返回 TRUE 返回找否则在路径中，或 FALSE。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757)。  
  
##  <a name="a-nameunquotespacesa--cpathtunquotespaces"></a><a name="unquotespaces"></a>CPathT::UnquoteSpaces  
 调用此方法以开头和结尾的路径中删除引号标记。  
  
```
void UnquoteSpaces();
```  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763)。  
  
##  <a name="a-namexchara--cpathtxchar"></a><a name="xchar"></a>CPathT::XCHAR  
 一种字符类型。  
  
```
typedef StringType::XCHAR XCHAR;
```  
  
### <a name="remarks"></a>备注  
 `StringType`为模板参数`CPathT`。  
  
## <a name="see-also"></a>另请参阅  
 [类](../../atl/reference/atl-classes.md)   
 [CStringT 类](../../atl-mfc-shared/reference/cstringt-class.md)
