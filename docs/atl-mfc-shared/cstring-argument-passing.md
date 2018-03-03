---
title: "CString 自变量传递 |Microsoft 文档"
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
- strings [C++], as function input/output
- argument passing [C++]
- arguments [C++], passing
- functions [C++], strings as input/output
- argument passing [C++], C strings
- passing arguments, C strings
- CString objects, passing arguments
- string arguments
ms.assetid: a67bebff-edf1-4cf4-bbff-d1cc6a901099
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3d33c8cc46ada41f851c90aaae0cabfadb1466d0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cstring-argument-passing"></a>CString 自变量传递
此文章介绍了如何将传递[CString](../atl-mfc-shared/reference/cstringt-class.md)对象序列化为函数和如何返回`CString`从函数的对象。  
  
##  <a name="_core_cstring_argument.2d.passing_conventions"></a>CString 自变量传递约定  
 当你定义的类接口时，必须为成员函数来确定自变量传递约定。 有一些标准的规则，以传递和返回`CString`对象。 如果你遵循中所述的规则[作为函数输入的字符串](#_core_strings_as_function_inputs)和[字符串作为函数输出](#_core_strings_as_function_outputs)，你将具有有效的正确代码。  
  
##  <a name="_core_strings_as_function_inputs"></a>作为函数输入的字符串  
 最有效且安全的方法使用`CString`中调用的函数对象是将传递`CString`函数的对象。 不管名称如何，`CString`对象不会存储一个字符串在内部用作 C 样式字符串具有 null 终止符的占用。 相反，`CString`对象需要小心跟踪它具有的字符数。 具有`CString`提供`LPCTSTR`指向以 null 结尾的字符串是少量的工作可能会很高，如果你的代码必须不断地执行。 结果是临时的因为对进行任何更改`CString`内容失效的旧副本`LPCTSTR`指针。  
  
 在某些情况下提供的 C 样式字符串，它确实很有作用。 例如，可以有被调用的函数，在 C 中编写的并不支持对象。 在这种情况下，强制`CString`参数`LPCTSTR`，并且该函数将收到以 C 样式 null 结尾的字符串。 此外可以转到另一个方向，并创建`CString`通过使用对象`CString`接受 C 样式字符串参数的构造函数。  
  
 如果要更改函数的字符串内容，将参数声明为非常数`CString`引用 (**CString &**)。  
  
##  <a name="_core_strings_as_function_outputs"></a>为函数输出的字符串  
 通常，你可以返回`CString`对象从函数，因为`CString`对象遵循如基元类型的值语义。 若要返回的只读字符串，使用的常量`CString`引用 (**const CString &**)。 下面的示例演示如何使用`CString`参数和返回类型：  
  
 [!code-cpp[NVC_ATLMFC_Utilities#197](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_1.cpp)]  
  
 [!code-cpp[NVC_ATLMFC_Utilities#198](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_2.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [字符串 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)

