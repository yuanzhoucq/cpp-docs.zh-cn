---
title: "部分 （c + + 组件扩展） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: partial_CPP
dev_langs: C++
helpviewer_keywords:
- partial
- C++/CX, partial
ms.assetid: 43adf1f5-10c5-44aa-a66f-7507e2bdabf8
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dd2debe47b0c60907c1a75f4e8b96d227468a345
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="partial--c-component-extensions"></a>部分（C++ 组件扩展）
`partial`关键字允许相同的 ref 类，以编写独立地在不同的文件的不同部分。  
  
## <a name="all-runtimes"></a>所有运行时  
 （此语言功能仅适用于 Windows 运行时。）  
  
## <a name="windows-runtime"></a>Windows 运行时  
 具有两个分部定义，ref 类`partial`关键字应用于相应的定义，第一个匹配项，这通常通过自动生成的代码，以便人工代码编写者不会非常频繁使用关键字。 有关类的所有后续部分定义，省略`partial`修饰符从*类键*关键字和类标识符。 当编译器遇到以前定义的 ref 类和类标识符但不是`partial`关键字，它在内部将所有到一个定义的 ref 类定义的组成部分合并。  
  
### <a name="syntax"></a>语法  
  
```cpp  
partial class-key identifier {  
   /* The first part of the partial class definition. 
      This is typically auto-generated */  
}  
// ...  
class-key identifier {  
   /* The subsequent part(s) of the class definition. The same 
      identifier is specified, but the "partial" keyword is omitted. */  
}  
```  
  
### <a name="parameters"></a>参数  
 *类别键*  
 声明一个类或结构，它支持的 Windows 运行时关键字。 任一`ref class`， `value class`， `ref struct`，或`value struct`。  
  
 *identifier*  
 定义类型的名称。  
  
### <a name="remarks"></a>备注  
 分部类支持在其中修改一个文件，而自动代码生成软件中的类定义的一部分的方案-例如 XAML 设计器 — 修改同一类中另一个文件中的代码。 通过使用分部类，可以防止自动代码生成器，器重写代码。 在 Visual Studio 项目中， `partial` 修饰符自动应用于生成的文件。  
  
 中的内容： 有两个例外的分部类定义可以包含的任何内容可能包含完整类定义，如果`partial`关键字被省略。 但是，您不能指定类可访问性（例如 `public partial class X { ... };`）或 `declspec`。  
  
 访问说明符的分部类定义中使用*标识符*不会影响后续的分部或完整类定义中的默认可访问性*标识符*。 允许静态数据成员的内联定义。  
  
 声明： 类的部分定义*标识符*只引入名称*标识符*，但*标识符*不能以需要类的方式使用定义。 名称*标识符*不能用于知道的大小*标识符*，或使用的基或成员的*标识符*直到编译器遇到的完整定义后*标识符*。  
  
 编号和排序： 可以有零个或多个分部类定义*标识符*。 每个分部类定义*标识符*必须词法排在前一个完整定义*标识符*(如果没有完整定义; 否则，类不能用于除就像前向声明） 但不是需要前面的前向声明*标识符*。 所有类密钥必须都匹配。  
  
 完整定义： 类的完整定义点*标识符*，行为都是相同就像的定义*标识符*声明了所有基类、 成员等中的顺序它们遇到和定义在分部类中。  
  
 模板： 分部类不能为模板。  
  
 泛型： 如果完整的定义可能是泛型，分部类可以是泛型。 但是，每个部分和完整类必须具有完全相同泛型参数，包括形式参数名称。  
  
 有关如何使用`partial`关键字，请参阅[分部类 (C + + /cli CX)](http://go.microsoft.com/fwlink/p/?LinkId=249023)。  
  
### <a name="requirements"></a>惠?  
 编译器选项： **/ZW**  
  
## <a name="common-language-runtime"></a>公共语言运行时  
 （此语言功能不适用于公共语言运行时。）  
  
## <a name="see-also"></a>请参阅  
 [分部类 (C + + /cli CX)](http://go.microsoft.com/fwlink/p/?LinkId=249023)