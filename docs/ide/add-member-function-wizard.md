---
title: "添加成员函数向导 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.function.overview
dev_langs: C++
helpviewer_keywords: Add Member Function Wizard [C++]
ms.assetid: 13b6defc-faa6-4d57-83db-9dd854cbea3d
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 775b519b304549b474cd21980ef5a4cbe8f2d4d0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="add-member-function-wizard"></a>添加成员函数向导
此向导将添加到标头文件和所选类的实现文件将存根 （stub） 成员函数实现的成员函数声明。  
  
 一旦你已添加成员函数使用向导，你可以编辑在开发环境中的代码。  
  
 **返回类型**  
 设置要添加的成员函数的返回类型。 你可以提供您自己的返回类型，也可以从可用类型列表中选择。 有关类型的信息，请参阅[基本类型](../cpp/fundamental-types-cpp.md)。  
  
||||  
|-|-|-|  
|`char`|`int`|`unsigned int`|  
|**double**|**long**|`unsigned long`|  
|**float**|**short**|`void`|  
|`HRESULT`|`unsigned char`||  
  
 **函数名称**  
 设置要添加的成员函数的名称。  
  
 **参数类型**  
 如果成员函数具有参数，请设置要添加为成员函数的参数的类型。 你可以提供你自己的参数类型，也可以从可用类型列表中选择。  
  
||||  
|-|-|-|  
|`char`|`int`|`unsigned char`|  
|**double**|**long**|`unsigned int`|  
|**float**|**short**|`unsigned long`|  
  
 **参数名称**  
 如果成员函数具有参数，请设置要添加为成员函数的参数的名称。  
  
 **参数列表**  
 显示已添加到成员函数的参数的列表。 若要将参数添加到列表中，提供的类型和中的名称**参数类型**和**参数名称**框，然后单击**添加**。 若要从列表中删除某一参数，请选择该参数，然后单击**删除**。  
  
 **访问**  
 指向成员函数中设置的访问权限。 访问修饰符是指定其他类具有指向成员函数的访问权限的关键字。 请参阅[成员访问控制](../cpp/member-access-control-cpp.md)有关指定访问的详细信息。 成员函数访问级别设置为**公共**默认情况下。  
  
-   [公用](../cpp/public-cpp.md)  
  
-   [受保护](../cpp/protected-cpp.md)  
  
-   [专用](../cpp/private-cpp.md)  
  
 检查新的成员函数是静态的还是虚拟的以及它是否是内联代码或纯代码。 如果你设置的成员函数是纯，`Virtual`选中复选框，和**内联**复选框变得不可用。 默认值为非静态、 非虚拟成员函数。  
  
|选项|描述|  
|------------|-----------------|  
|[Static](../cpp/storage-classes-cpp.md)|指定函数的作用类似全局和可以调用的类，即使使用没有类实例化的外部。 成员函数具有不能访问非静态成员。 指定为成员函数`Static`不能是虚。|  
|[虚拟](../cpp/virtual-cpp.md)|确保正确的成员函数调用成员函数的对象，而不考虑用来进行成员函数调用的表达式。 指定为成员函数`Virtual`不能为静态。|  
|**纯**|指示没有实现，提供有关正在声明; 的虚拟成员函数因此，**纯**可以仅在虚拟成员函数上指定。 包含至少一个纯虚拟成员函数的类被视为一个抽象类。 从抽象类派生的类必须实现纯虚成员函数，或它们，也是抽象类。|  
|[内联](../cpp/inline-functions-cpp.md)|指示编译器将成员函数主体的副本插入到每个调用成员函数的位置。 指定为成员函数**内联**不能是纯。|  
  
 **.cpp 文件**  
 设置存根成员函数的实现在其中写入的文件位置。 默认情况下，它是写入向其添加成员函数的类的.cpp 文件。 单击省略号按钮以更改文件名称。 成员函数的实现添加到所选文件的内容。  
  
 **注释**  
 提供成员函数的标头文件中的注释。  
  
 **函数签名**  
 当你单击出现在代码中将显示的成员函数**完成**。 无法编辑此框中的文本。 若要更改的成员函数，更改在向导中的相应框。  
  
## <a name="see-also"></a>请参阅  
 [添加成员函数](../ide/adding-a-member-function-visual-cpp.md)