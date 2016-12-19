---
title: "在 C++ 类中使用 dllimport 和 dllexport | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "类 [C++], 声明"
  - "类 [C++], 可导出和继承"
  - "声明 [C++], class"
  - "声明类"
  - "dllexport 特性 [C++]"
  - "dllexport 特性 [C++], 类"
  - "dllimport 特性 [C++], 类"
  - "可导出类 [C++]"
  - "导出类"
  - "继承 [C++], 可导出类"
ms.assetid: 8d7d1303-b9e9-47ca-96cc-67bf444a08a9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在 C++ 类中使用 dllimport 和 dllexport
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
 可以使用 **dllimport** 或 `dllexport` 特性来声明 C\+\+ 类。  这些形式表示已导入或导出整个类。  以这种方式导出的类称为可导出类。  
  
 以下示例定义了可导出类。  将导出其所有成员函数和静态数据：  
  
```  
#define DllExport   __declspec( dllexport )  
  
class DllExport C {  
   int i;  
   virtual int func( void ) { return 1; }  
};  
```  
  
 请注意，禁止对可导出类的成员显式使用 **dllimport** 和 `dllexport` 特性。  
  
##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bdllexportclasses"></a> dllexport 类  
 在声明类 `dllexport` 时，所有其成员函数和静态数据成员都将导出。  您必须在同一程序中提供所有此类成员的定义。  否则，将生成链接器错误。  此规则有一个例外情况，即对于纯虚函数，您无需为其提供显式定义。  但是，由于基类的析构函数始终在调用抽象类的析构函数，因此纯虚拟析构函数必须始终提供定义。  请注意，这些规则对不可导出的类是相同的。  
  
 如果导出类类型的数据或返回类的函数，请务必导出类。  
  
##  <a name="_pluslang_dllexport_classesdllexportclasses"></a> dllimport 类  
 当声明类 **dllimport** 时，将导入所有其成员函数和静态数据成员。  与非类类型上的 **dllimport** 和 `dllexport` 的行为不同，静态数据成员无法在定义 **dllimport** 类的同一程序中指定定义。  
  
##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2binheritanceandexportableclasses"></a> 继承和可导出类  
 可导出类的所有基类都必须是可导出的。  否则，会生成编译器警告。  此外，同样是类的所有可访问成员必须是可导出的。  此规则只允许 `dllexport` 类从 **dllimport** 类继承，**dllimport** 类从 `dllexport` 类继承（但不建议后一种方式）。  通常来说，对 DLL 客户端可访问的所有内容（根据 C\+\+ 访问规则）都应该是可导出接口的一部分。  这包括在内联函数中引用的私有数据成员。  
  
##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bselectivememberimportexport"></a> 选择性成员导入\/导出  
 由于类中的成员函数和静态数据隐式包含了外部链接，因此您可以使用 **dllimport** 或 `dllexport` 特性声明它们，除非整个类都已导出。  如果整个类都已导入或导出，则禁止将成员函数和数据显式声明为 **dllimport** 或 `dllexport`。  如果在类定义中将静态数据成员声明为 `dllexport`，定义一定会在同一程序中的某处出现（就像非类外部链接一样）。  
  
 同样，您可以使用 **dllimport** 或 `dllexport` 特性声明成员函数。  在这种情况下，您必须在同一程序中的某处提供 `dllexport` 定义。  
  
 有关选择性成员导入和导出的某些要点值得注意：  
  
-   选择性成员导入\/导出最适合用于提供具有更强限制的导出类接口版本；即，您可以为该版本设计一个 DLL，该 DLL 公开的公用和专用功能比本应允许的语言公开的更少。  这对于优化可导出接口也很有用：当通过定义知道客户端无法访问某些私有数据时，您不需要导出整个类。  
  
-   如果导出了某个类中的一个虚函数，则必须导出其中的所有虚函数，或者至少必须提供客户端可直接使用的版本。  
  
-   如果有在其中将选择性成员导入\/导出用于虚函数的类，则这些函数必须在可导出接口或已定义内联中（对客户端可见）。  
  
-   如果将某个成员定义为 `dllexport`，但不在类定义中包含它，则会产生编译器错误。  必须在类头中定义成员。  
  
-   尽管允许将类成员定义为 **dllimport** 或 `dllexport`，但无法重写在类定义中指定的接口。  
  
-   如果在声明成员函数的类定义的主体以外的地方定义成员函数，并且将函数定义为 `dllexport` 或 **dllimport**（如果此定义不同于类声明中指定的定义），则会生成警告。  
  
### 结束 Microsoft 专用  
  
## 请参阅  
 [dllexport、dllimport](../cpp/dllexport-dllimport.md)