---
title: "Exporting String Classes Using CStringT | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStringT class, exporting strings"
ms.assetid: bdfc441e-8d2a-461c-9885-46178066c09f
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Exporting String Classes Using CStringT
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

过去，MFC开发人员从派生 `CString` 专用其字符串选件类。  Microsoft Visual C\+\+ .NET \(MFC 8.0\)，[CString](../atl-mfc-shared/using-cstring.md) 选件类通过调用 [CStringT](../atl-mfc-shared/reference/cstringt-class.md)的模板选件类取代。  这提供了几个好处:  
  
-   使MFC `CString` 选件类用于ATL项目，但不链接在较大的MFC静态库或DLL。  
  
-   新 `CStringT` 模板选件类，可以自定义 `CString` 行为使用指定特征功能的模板参数，类似于模板在标准模板库\(STL\)中。  
  
-   使用 `CStringT`时，当从DLL导出您的字符串选件类，编译器会自动导出 `CString` 基类。  因为 `CString` 本身模板选件类，它可能是由编译器实例化，当使用，因此，除非编译器知道 `CString` 从DLL导入。  如果迁移从Visual C\+\+ 6.0的项目中对Visual C\+\+ .NET中，从DLL和在本地实例化的版本可能会多次定义的 `CString` 已经了解了链接器符号错误由于 `CString` 的冲突导入的。  适当的方式执行此下述。  有关此问题的更多信息，请参见知识库文章，“链接错误，当您导入CString派生的选件类” \(Q309801\)时在MSDN Library CD\-ROM上 [http:\/\/support.microsoft.com\/default.aspx](http://support.microsoft.com/default.aspx)或。  
  
 以下情况会导致链接器生成符号错误为而定义的选件类。  假定，可导出 `CString`派生类\(`CMyString`\)从MFC扩展DLL:  
  
 [!code-cpp[NVC_MFC_DLL#6](../atl-mfc-shared/codesnippet/CPP/exporting-string-classes-using-cstringt_1.cpp)]  
  
 使用者代码使用 `CString` 和 `CMyString`杂注。"  MyString.h”在预编译标头不包含，并且，`CString` 一些用法没有可见的 `CMyString`。  
  
 假定，可以在单独的源文件，Source1.cpp和Source2.cpp使用 `CString` 和 `CMyString` 选件类。  在Source1.cpp，请使用 `CMyString` 和\#include MyString.h。  在Source2.cpp，请使用 `CString`，但是，不包括MyString.h。  在这种情况下，链接器将提出问题是的 `CStringT` 多次定义。  导出 `CMyString`为由编译器导入从DLL和实例化的局部 `CString` 引起通过 `CStringT` 模板。  
  
 若要解决此问题，请执行下列操作:  
  
 从MFC90.DLL导出 `CStringA` 和 `CStringW` \(和必要的基类）。  包括MFC的项目在前面的MFC实现总是使用MFC DLL导出的 `CStringA` 和 `CStringW`。  
  
 使用 `CStringT` 模板，然后创建一个可导出派生类，那么，当 `CStringT_Exported` 在下，例如:  
  
 [!code-cpp[NVC_MFC_DLL#7](../atl-mfc-shared/codesnippet/CPP/exporting-string-classes-using-cstringt_2.cpp)]  
  
 在AfxStr.h，请替换以前 `CString`、 `CStringA`和 `CStringW` typedef如下所示:  
  
 [!code-cpp[NVC_MFC_DLL#8](../atl-mfc-shared/codesnippet/CPP/exporting-string-classes-using-cstringt_3.cpp)]  
  
 有几个警告:  
  
-   因为这将使ATL项目导出专用 `CStringT` 选件类，您不应导出 `CStringT`。  
  
-   使用从 `CStringT` 的一个可导出派生类使必须重新实现 `CStringT` 功能。  附加代码绑定到前进到 `CStringT` 基类的构造函数。  
  
-   在使用MFC的共享DLL时，生成`CString`、 `CStringA`和 `CStringW` 只应标记为 `__declspec(dllexport/dllimport)`。  如果链接到MFC静态库，则不应将这些选件类如导出;否则，使用 `CString`、 `CStringA`和 `CStringW` 内使用在用户DLL内将指示 `CString` 如导出。  
  
## 相关主题  
 [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md)  
  
## 请参阅  
 [Using CStringT](../atl-mfc-shared/using-cstringt.md)   
 [Using CString](../atl-mfc-shared/using-cstring.md)