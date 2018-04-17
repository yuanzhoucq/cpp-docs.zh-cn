---
title: "C++ 类中使用 dllimport 和 dllexport |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- exporting classes [C++]
- declarations [C++], class
- exportable classes [C++]
- classes [C++], declaring
- classes [C++], exportable and inheritance
- inheritance [C++], exportable classes [C++]
- dllimport attribute [C++], classes
- declaring classes [C++]
- dllexport attribute [C++]
- dllexport attribute [C++], classes [C++]
ms.assetid: 8d7d1303-b9e9-47ca-96cc-67bf444a08a9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d8f9434387efcf3377cdc983116a51b524d16662
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="using-dllimport-and-dllexport-in-c-classes"></a>在 C++ 类中使用 dllimport 和 dllexport
## <a name="microsoft-specific"></a>Microsoft 专用  
 你可以声明具有 C++ 类**dllimport**或`dllexport`属性。 这些形式表示已导入或导出整个类。 以这种方式导出的类称为可导出类。  
  
 以下示例定义了可导出类。 将导出其所有成员函数和静态数据：  
  
```  
#define DllExport   __declspec( dllexport )  
  
class DllExport C {  
   int i;  
   virtual int func( void ) { return 1; }  
};  
```  
  
 请注意该显式使用**dllimport**和`dllexport`禁止可导出类的成员上的属性。  
  
##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bdllexportclasses"></a>dllexport 类  
 在声明类 `dllexport` 时，所有其成员函数和静态数据成员都将导出。 您必须在同一程序中提供所有此类成员的定义。 否则，将生成链接器错误。 此规则有一个例外情况，即对于纯虚函数，您无需为其提供显式定义。 但是，由于基类的析构函数始终在调用抽象类的析构函数，因此纯虚拟析构函数必须始终提供定义。 请注意，这些规则对不可导出的类是相同的。  
  
 如果导出类类型的数据或返回类的函数，请务必导出类。  
  
##  <a name="_pluslang_dllexport_classesdllexportclasses"></a>dllimport 类  
 当你声明一个类**dllimport**，导入所有其成员函数和静态数据成员。 与不同的行为**dllimport**和`dllexport`非类类型上静态数据成员不能在同一程序中指定的定义**dllimport**定义类。  
  
##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2binheritanceandexportableclasses"></a>继承和可导出类  
 可导出类的所有基类都必须是可导出的。 否则，会生成编译器警告。 此外，同样是类的所有可访问成员必须是可导出的。 此规则只允许`dllexport`类继承自**dllimport**类，和一个**dllimport**类继承自`dllexport`类 （但不推荐后者）。 通常来说，对 DLL 客户端可访问的所有内容（根据 C++ 访问规则）都应该是可导出接口的一部分。 这包括在内联函数中引用的私有数据成员。  
  
##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bselectivememberimportexport"></a>选择性成员导入/导出  
 成员函数和类中的静态数据隐式具有外部链接，因为可以将其与声明**dllimport**或`dllexport`属性，除非导出整个类。 如果整个类导入或导出，显式声明成员函数和数据作为**dllimport**或`dllexport`禁止。 如果在类定义中将静态数据成员声明为 `dllexport`，定义一定会在同一程序中的某处出现（就像非类外部链接一样）。  
  
 同样，可以声明具有函数成员**dllimport**或`dllexport`属性。 在这种情况下，您必须在同一程序中的某处提供 `dllexport` 定义。  
  
 有关选择性成员导入和导出的某些要点值得注意：  
  
-   选择性成员导入/导出最适合用于提供具有更强限制的导出类接口版本；即，您可以为该版本设计一个 DLL，该 DLL 公开的公用和专用功能比本应允许的语言公开的更少。 这对于优化可导出接口也很有用：当通过定义知道客户端无法访问某些私有数据时，您不需要导出整个类。  
  
-   如果导出了某个类中的一个虚函数，则必须导出其中的所有虚函数，或者至少必须提供客户端可直接使用的版本。  
  
-   如果有在其中将选择性成员导入/导出用于虚函数的类，则这些函数必须在可导出接口或已定义内联中（对客户端可见）。  
  
-   如果将某个成员定义为 `dllexport`，但不在类定义中包含它，则会产生编译器错误。 必须在类头中定义成员。  
  
-   尽管作为类成员的定义**dllimport**或`dllexport`是允许使用，不能重写的类定义中指定的接口。  
  
-   如果你在其中声明它的类定义的主体以外的地方定义成员函数，则会生成警告函数定义为`dllexport`或**dllimport** （如果此定义不同于指定的类声明中）。  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [dllexport、dllimport](../cpp/dllexport-dllimport.md)