---
title: "CPathT Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CPathT"
  - "CPathT"
  - "ATL::CPathT<StringType>"
  - "ATL::CPathT"
  - "ATL.CPathT<StringType>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPathT class"
ms.assetid: eba4137d-1fd2-4b44-a2e1-0944db64df3c
caps.latest.revision: 20
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPathT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类表示路径。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template< typename   
      StringType  
      >   
class CPathT  
```  
  
#### 参数  
 `StringType`  
 使用的ATL\/MFC字符串选件类为轨迹\(请参见 [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)）。  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|说明|  
|--------|--------|  
|[CPathT::PCXSTR](../Topic/CPathT::PCXSTR.md)|常数字符串类型。|  
|[CPathT::PXSTR](../Topic/CPathT::PXSTR.md)|字符串类型。|  
|[CPathT::XCHAR](../Topic/CPathT::XCHAR.md)|字符类型|  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CPathT::CPathT](../Topic/CPathT::CPathT.md)|路径的构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CPathT::AddBackslash](../Topic/CPathT::AddBackslash.md)|调用此方法添加反斜杠到字符串的末尾创建路径的正确语法。|  
|[CPathT::AddExtension](../Topic/CPathT::AddExtension.md)|调用此方法将文件扩展名到路径。|  
|[CPathT::Append](../Topic/CPathT::Append.md)|调用此方法追加到当前路径。|  
|[CPathT::BuildRoot](../Topic/CPathT::BuildRoot.md)|调用此方法创建从特定提升数字的根路径。|  
|[CPathT::Canonicalize](../Topic/CPathT::Canonicalize.md)|调用此方法将路径转换规范格式。|  
|[CPathT::Combine](../Topic/CPathT::Combine.md)|调用此方法来串联字符串表示目录名的和表示文件路径名的字符串到一个路径。|  
|[CPathT::CommonPrefix](../Topic/CPathT::CommonPrefix.md)|调用此方法来确定指定的路径是否与当前路径共享公共前缀的。|  
|[CPathT::CompactPath](../Topic/CPathT::CompactPath.md)|调用此方法截断文件路径在给定像素宽度之内通过替换路径元素将椭圆。|  
|[CPathT::CompactPathEx](../Topic/CPathT::CompactPathEx.md)|调用此方法截断文件路径在字符串中的许多适合通过替换路径元素将椭圆。|  
|[CPathT::FileExists](../Topic/CPathT::FileExists.md)|调用此方法检查此路径名称的文件是否存在。|  
|[CPathT::FindExtension](../Topic/CPathT::FindExtension.md)|调用此方法可查找文件扩展名的位置路径内的。|  
|[CPathT::FindFileName](../Topic/CPathT::FindFileName.md)|调用此方法可查找文件名的位置路径内的。|  
|[CPathT::GetDriveNumber](../Topic/CPathT::GetDriveNumber.md)|调用此方法搜索路径在“到“Z的内的盘符并返回相应的提升数字。|  
|[CPathT::GetExtension](../Topic/CPathT::GetExtension.md)|调用此方法获取路径的文件扩展名。|  
|[CPathT::IsDirectory](../Topic/CPathT::IsDirectory.md)|调用此方法检查路径是否为有效的内容。|  
|[CPathT::IsFileSpec](../Topic/CPathT::IsFileSpec.md)|调用此方法搜索路径所有分隔的路径字符\(例如，“: ”或“\\”）。  如果没有当前路径分隔字符，路径视为文件规范路径。|  
|[CPathT::IsPrefix](../Topic/CPathT::IsPrefix.md)|调用此方法确保路径是否包含 `pszPrefix`传入的类型的有效的标题。|  
|[CPathT::IsRelative](../Topic/CPathT::IsRelative.md)|调用此方法确保路径是否是相对的。|  
|[CPathT::IsRoot](../Topic/CPathT::IsRoot.md)|调用此方法确保路径是否为内容根。|  
|[CPathT::IsSameRoot](../Topic/CPathT::IsSameRoot.md)|调用此方法来确定另一个路径是否与当前路径的一个常见根元素。|  
|[CPathT::IsUNC](../Topic/CPathT::IsUNC.md)|调用此方法确保路径是否是服务器和共享的有效UNC \(通用命名约定\)路径。|  
|[CPathT::IsUNCServer](../Topic/CPathT::IsUNCServer.md)|调用此方法确保路径是仅由服务器上的有效UNC \(通用命名约定\)路径。|  
|[CPathT::IsUNCServerShare](../Topic/CPathT::IsUNCServerShare.md)|调用此方法确保路径是否为有效的UNC \(通用命名约定\)共享路径，\\ \\*server*\\*share*。|  
|[CPathT::MakePretty](../Topic/CPathT::MakePretty.md)|调用此方法将路径转换为全部小写字母提供路径一致的外观。|  
|[CPathT::MatchSpec](../Topic/CPathT::MatchSpec.md)|调用此方法搜索路径包含通配符与类型的字符串。|  
|[CPathT::QuoteSpaces](../Topic/CPathT::QuoteSpaces.md)|如果它包含有任何空格，则调用此方法将路径放在引号内。|  
|[CPathT::RelativePathTo](../Topic/CPathT::RelativePathTo.md)|调用此方法将创建一个文件或文件夹的相对路径到另一个。|  
|[CPathT::RemoveArgs](../Topic/CPathT::RemoveArgs.md)|调用此方法从路径移除任何命令行参数。|  
|[CPathT::RemoveBackslash](../Topic/CPathT::RemoveBackslash.md)|调用此方法从路径删除尾部斜杠。|  
|[CPathT::RemoveBlanks](../Topic/CPathT::RemoveBlanks.md)|调用此方法从路径取消任何前导和尾随空格。|  
|[CPathT::RemoveExtension](../Topic/CPathT::RemoveExtension.md)|如果有一个，会调用此方法从路径移除文件扩展名。|  
|[CPathT::RemoveFileSpec](../Topic/CPathT::RemoveFileSpec.md)|如果有，则调用此方法从路径删除尾部斜杠和文件名。|  
|[CPathT::RenameExtension](../Topic/CPathT::RenameExtension.md)|在路径调用此方法替换文件扩展名用新的扩展。  如果文件名不包含一个扩展，该扩展将附加到该字符串的末尾。|  
|[CPathT::SkipRoot](../Topic/CPathT::SkipRoot.md)|调用此方法分析路径，则忽略盘符或UNC服务器\/共享路径部件。|  
|[CPathT::StripPath](../Topic/CPathT::StripPath.md)|调用此方法会移除完全限定的路径和文件名的路径部分。|  
|[CPathT::StripToRoot](../Topic/CPathT::StripToRoot.md)|调用此方法会移除路径中的所有部件除了根信息。|  
|[CPathT::UnquoteSpaces](../Topic/CPathT::UnquoteSpaces.md)|调用此方法以移除路径的引号和结尾。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CPathT::operator const StringType &](../Topic/CPathT::operator%20const%20StringType%20&.md)|此运算符允许对象作为字符串。|  
|[CPathT::operator CPathT::PCXSTR](../Topic/CPathT::operator%20CPathT::PCXSTR.md)|此运算符允许对象作为字符串。|  
|[CPathT::operator StringType &](../Topic/CPathT::operator%20StringType%20&.md)|此运算符允许对象作为字符串。|  
|[CPathT::operator \+\=](../Topic/CPathT::operator%20+=.md)|此运算符追加字符串。路径。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CPathT::m\_strPath](../Topic/CPathT::m_strPath.md)|路径。|  
  
## 备注  
 `CPath`、 `CPathA`和 `CPathW` 是 `CPathT` 的实例化定义如下:  
  
 `typedef CPathT< CString > CPath;`  
  
 `typedef CPathT< CStringA > CPathA;`  
  
 `typedef CPathT< CStringW > CPathW;`  
  
## 要求  
 **Header:** atlpath.h  
  
## 请参阅  
 [类](../../atl/reference/atl-classes.md)   
 [CStringT Class](../../atl-mfc-shared/reference/cstringt-class.md)