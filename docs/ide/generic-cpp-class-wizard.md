---
title: 泛型 c + + 类向导 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.class.generic
dev_langs:
- C++
helpviewer_keywords:
- Generic C++ Class Wizard [C++]
ms.assetid: aa95be9e-fc1b-45db-a11d-0d32c4929077
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 43e86a4047ef025f49dd01eda90f324623a90752
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="generic-c-class-wizard"></a>泛型 C++ 类向导
向项目添加泛型 c + + 类。 此类不从 ATL 或 MFC 继承。  
  
 **类名**  
 设置新的类的名称。  
  
 **.h 文件**  
 设置新的类的头文件的名称。 默认情况下，此名称基于你在中提供的名称**类名**。 若要将标头文件保存到你选择的位置，或将类声明追加到现有文件，单击省略号按钮 (**...**).如果指定现有文件，则单击**完成**，向导会提示您指定的类声明是否应追加到文件的内容。 若要追加的声明，请单击**是**; 若要将返回到向导和指定另一个文件的名称，请单击**否**。  
  
 **.cpp 文件**  
 设置新的类实现文件的名称。 默认情况下，此名称基于你在中提供的名称**类名**。 若要将实现文件保存到你选择的位置或将类定义追加到现有文件，单击省略号按钮 (**...**).如果指定现有文件，则单击**完成**，向导会提示您指定是否应将类定义追加到文件的内容。 若要追加的定义，请单击**是**; 若要将返回到向导和指定另一个文件的名称，请单击**否**。  
  
 **基类**  
 设置新的类的基类。  
  
 **访问**  
 设置为新类的基类成员的的访问。 访问修饰符是访问的指定的其他类具有指向类成员函数级别的关键字。 有关如何指定访问权限的详细信息，请参阅[成员访问控制](../cpp/member-access-control-cpp.md)。 默认情况下，类访问级别设置为`public`。  
  
-   `public`  
  
-   `protected`  
  
-   `private`  
  
-   **默认**（生成没有访问修饰符。）  
  
 **虚拟的析构函数**  
 指定是否为虚拟类析构函数。 使用虚拟的析构函数帮助确保删除派生类的实例时调用的正确析构函数。  
  
 **内联**  
 标头文件中生成的类构造函数和作为内联函数的类定义。  
  
 **管理**  
 当选中时，将添加托管的类和标头文件。 清除时，将添加本机类和标头文件。  
  
## <a name="see-also"></a>请参阅  
 [添加一般 C++ 类](../ide/adding-a-generic-cpp-class.md)