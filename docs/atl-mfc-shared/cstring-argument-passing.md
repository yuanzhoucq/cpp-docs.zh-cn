---
title: CString 自变量传递 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 86e89a0f4af28606abef8804aeab5d1e2f62e8d8
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882446"
---
# <a name="cstring-argument-passing"></a>CString 自变量传递
此文章介绍了如何将传递[CString](../atl-mfc-shared/reference/cstringt-class.md)对象的功能和如何返回`CString`函数中的对象。  
  
##  <a name="_core_cstring_argument.2d.passing_conventions"></a> CString 参数传递约定  
 在定义类接口时，必须确定成员函数的参数传递约定。 有一些标准规则对传递和返回`CString`对象。 如果您按照中所述的规则[作为函数的输入字符串](#_core_strings_as_function_inputs)并[为函数的输出字符串](#_core_strings_as_function_outputs)，将具有有效的正确代码。  
  
##  <a name="_core_strings_as_function_inputs"></a> 作为函数的输入字符串  
 最高效和安全的方法使用`CString`中调用的函数对象是传递`CString`函数的对象。 不管名称如何，`CString`对象不会存储一个字符串在内部作为具有 null 终止符的 C 样式字符串。 相反，`CString`对象需要仔细跟踪它具有的字符数。 具有`CString`提供指向以 null 结尾的字符串的 LPCTSTR 是少量的工作可能会较长，如果你的代码必须不断地执行。 结果是临时的因为任何更改为`CString`内容使 LPCTSTR 指针的旧副本。  
  
 在某些情况下提供的 C 样式字符串，它确实使有意义。 例如，可以是被调用的函数的以 C 编写的且不支持对象。 在这种情况下，强制`CString`给 LPCTSTR 和函数的参数将获取以 C 样式 null 结尾的字符串。 此外可以转到另一个方向，并创建`CString`对象使用`CString`接受 C 样式字符串参数的构造函数。  
  
 如果要更改函数字符串内容，将参数声明为非常数`CString`引用 (`CString&`)。  
  
##  <a name="_core_strings_as_function_outputs"></a> 为函数的输出的字符串  
 通常可以返回`CString`对象从函数，因为`CString`对象遵循等基元类型的值语义。 若要返回只读的字符串，使用的常量`CString`引用 (`const CString&`)。 下面的示例演示如何使用`CString`参数和返回类型：  
  
 [!code-cpp[NVC_ATLMFC_Utilities#197](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_1.cpp)]  
  
 [!code-cpp[NVC_ATLMFC_Utilities#198](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_2.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [字符串 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)

