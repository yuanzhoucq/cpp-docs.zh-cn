---
title: "导出字符串类使用 CStringT |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CStringT class, exporting strings
ms.assetid: bdfc441e-8d2a-461c-9885-46178066c09f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dd662b149f56cf0d6bd5e7a3c912e0ecd14f21b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="exporting-string-classes-using-cstringt"></a>导出使用 CStringT 字符串类
在过去，MFC 开发人员有派生自`CString`特别指明它们自己的字符串类。 在 Microsoft Visual c + +.NET (MFC 8.0) [CString](../atl-mfc-shared/using-cstring.md)类被取代调用一种模板类[CStringT](../atl-mfc-shared/reference/cstringt-class.md)。 这提供以下几个好处：  
  
-   它允许 MFC`CString`类用于 ATL 项目链接到更大的 MFC 静态库或 DLL 的情况下。  
  
-   与新`CStringT`模板类，可以自定义`CString`使用指定字符特征，类似于 c + + 标准库中的模板的模板参数的行为。  
  
-   当将您自己的字符串类导出从 DLL 使用`CStringT`，编译器也会自动导出`CString`基类。 由于`CString`本身是一种模板类，它可能被实例化由编译器时使用，除非编译器已注意到，`CString`从 DLL 导入。 如果你迁移项目从 Visual c + + 6.0 到 Visual c + +.NET，你可能看到的乘定义的链接器的符号错误`CString`由于的冲突`CString`从一个 DLL 和本地实例化的版本导入。 下面描述了执行此操作的正确方法。 有关此问题的详细信息，请参阅知识库文章中，"链接错误，当你导入 CString 派生类"(Q309801) 在[http://support.microsoft.com/default.aspx](http://support.microsoft.com/default.aspx)。  
  
 以下方案将导致链接器以生成乘定义类的符号错误。 假设你要导出`CString`-派生类 (`CMyString`) 从 MFC 扩展 DLL:  
  
 [!code-cpp[NVC_MFC_DLL#6](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_1.cpp)]  
  
 使用者代码使用的混合`CString`和`CMyString`。 预编译标头和的一些用法中不包括"MyString.h"`CString`没有`CMyString`可见。  
  
 假设你使用`CString`和`CMyString`Source1.cpp 和 Source2.cpp 单独的源代码文件中的类。 在 Source1.cpp，你使用`CMyString`和 #include MyString.h。 在 Source2.cpp，你使用`CString`，但却没有 #include MyString.h。 在这种情况下，链接器将抱怨`CStringT`被多次定义。 这引起`CString`正在同时从将导出的 DLL 导入`CMyString`，和由通过编译器的本地实例化`CStringT`模板。  
  
 若要解决此问题，请执行以下操作：  
  
 导出`CStringA`和`CStringW`（和必需的基本类） 从 MFC90。DLL。 包含 MFC 项目将始终使用 MFC DLL 导出`CStringA`和`CStringW`，如下所示以前 MFC 实现。  
  
 然后创建可导出的派生的类使用`CStringT`模板，作为`CStringT_Exported`低于，例如：  
  
 [!code-cpp[NVC_MFC_DLL#7](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_2.cpp)]  
  
 在 AfxStr.h，将上一个`CString`， `CStringA`，和`CStringW`typedef，如下所示：  
  
 [!code-cpp[NVC_MFC_DLL#8](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_3.cpp)]  
  
 有几个注意事项：  
  
-   不应导出`CStringT`本身因为这会导致仅 ATL 项目将导出一个专用`CStringT`类。  
  
-   使用可导出派生类从`CStringT`最大程度减少无需重新实现`CStringT`功能。 其他代码被限制于转发到的构造函数`CStringT`基类。  
  
-   `CString``CStringA`，和`CStringW`应仅将标记为`__declspec(dllexport/dllimport)`在您生成使用 MFC 共享 DLL。 如果链接 MFC 静态库，你应将标记这些类为导出;否则为内部使用`CString`， `CStringA`，和`CStringW`内用户 Dll 会将标记`CString`以及导出。  
  
## <a name="related-topics"></a>相关主题  
 [CStringT 类](../atl-mfc-shared/reference/cstringt-class.md)  
  
## <a name="see-also"></a>请参阅  
 [使用 CStringT](../atl-mfc-shared/using-cstringt.md)   
 [使用 CString](../atl-mfc-shared/using-cstring.md)

