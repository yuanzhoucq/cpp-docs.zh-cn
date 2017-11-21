---
title: "使用 ccombstr 进行 (ATL) 编程 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CComBSTR class, programming with
- Unicode, using CComBSTR [ATL]
ms.assetid: d3bd0851-d132-4be9-9c4c-6ccba17acb2b
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4d75d2df47f69384ead62712836eee057aed94f3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="programming-with-ccombstr-atl"></a>使用 CComBSTR 进行编程 (ATL)
ATL 类[CComBSTR](../atl/reference/ccombstr-class.md)提供的包装`BSTR`数据类型。 虽然`CComBSTR`是有用的工具，需要注意的几种情况。  
  
-   [转换问题](#programmingwithccombstr_conversionissues)  
  
-   [作用域问题](#programmingwithccombstr_scopeissues)  
  
-   [显式释放 CComBSTR 对象](#programmingwithccombstr_explicitlyfreeing)  
  
-   [在循环中使用 CComBSTR 对象](#programmingwithccombstr_usingloops)  
  
-   [内存泄漏问题](#programmingwithccombstr_memoryleaks)  
  
##  <a name="programmingwithccombstr_conversionissues"></a>转换问题  
 尽管几个`CComBSTR`方法会自动将 ANSI 字符串自变量转换为 Unicode，方法将始终返回 Unicode 格式字符串。 若要将输出字符串转换回 ANSI，使用 ATL 转换类。 ATL 转换类的详细信息，请参阅[ATL 和 MFC 字符串转换宏](reference/string-conversion-macros.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#114](../atl/codesnippet/cpp/programming-with-ccombstr-atl_1.cpp)]  
  
 如果使用字符串文本来修改`CComBSTR`对象，请使用宽字符字符串。 这将减少不必要的转换。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#115](../atl/codesnippet/cpp/programming-with-ccombstr-atl_2.cpp)]  
  
##  <a name="programmingwithccombstr_scopeissues"></a>作用域问题  
 与任何功能良好的类，`CComBSTR`超出范围时将释放其资源。 如果函数返回一个指向`CComBSTR`字符串，这可能导致问题，如指针将引用已释放的内存。 在这些情况下，使用**复制**方法，如下所示。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#116](../atl/codesnippet/cpp/programming-with-ccombstr-atl_3.cpp)]  
  
##  <a name="programmingwithccombstr_explicitlyfreeing"></a>显式释放 CComBSTR 对象  
 可以显式释放中包含的字符串`CComBSTR`对象，然后对象超出作用域。 如果将释放该字符串，`CComBSTR`对象无效。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#117](../atl/codesnippet/cpp/programming-with-ccombstr-atl_4.cpp)]  
  
##  <a name="programmingwithccombstr_usingloops"></a>在循环中使用 CComBSTR 对象  
 作为`CComBSTR`类分配缓冲区以执行某些操作，如`+=`运算符或**追加**方法，不建议你执行在紧凑循环内的字符串操作。 在这些情况下，`CStringT`提供更好的性能。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#118](../atl/codesnippet/cpp/programming-with-ccombstr-atl_5.cpp)]  
  
##  <a name="programmingwithccombstr_memoryleaks"></a>内存泄漏问题  
 传递的已初始化地址`CComBSTR`用作**[out 一个]**参数会导致内存泄漏。  
  
 在下面的示例中，字符串分配为保存字符串`"Initialized"`泄露时函数`MyGoodFunction`替换字符串。  
  
 [!code-cpp[NVC_ATL_Utilities#119](../atl/codesnippet/cpp/programming-with-ccombstr-atl_6.cpp)]  
  
 若要避免泄漏，调用**空**方法现有`CComBSTR`对象，然后再传递的地址与**[out 一个]**参数。  
  
 请注意，是否该函数的参数，相同的代码将不导致了泄漏**[中，out]**。  
  
## <a name="see-also"></a>另请参阅  
 [概念](../atl/active-template-library-atl-concepts.md)   
 [CStringT 类](../atl-mfc-shared/reference/cstringt-class.md)   
 [wstring](../standard-library/basic-string-class.md)   
 [字符串转换宏](../atl/reference/string-conversion-macros.md)

