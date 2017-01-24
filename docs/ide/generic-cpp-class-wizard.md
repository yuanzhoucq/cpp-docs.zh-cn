---
title: "一般 C++ 类向导 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.class.generic"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "一般 C++ 类向导 [C++]"
ms.assetid: aa95be9e-fc1b-45db-a11d-0d32c4929077
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 一般 C++ 类向导
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将一般 C\+\+ 类添加到项目。  类不继承 ATL 或MFC。  
  
 **类名**  
 设置新类的名称。  
  
 **.h 文件**  
 设置新类的头文件名。  默认情况下，此名称基于在“类名”中提供的名称。  若要保存头文件到所选位置，或将类声明追加到现有文件，单击省略号按钮 \(**...**\)。  如果指定现有文件，则单击**“完成”**时，向导会提示指定是否应向该文件的内容中追加类声明。  单击**“是”**追加该文件；单击**“否”**返回到向导并指定另一个文件名。  
  
 **.cpp 文件**  
 为新类别的执行文件设置名称。  默认情况下，此名称基于在“类名”中提供的名称。  若要保存实现文件到所选位置，或将类定义追加到现有文件，单击省略号按钮 \(**...**\)。  如果指定现有文件，则单击**“完成”**时，向导会提示指定是否应向该文件的内容中追加类声明。  单击**“是”**追加该文件；单击**“否”**返回到向导并指定另一个文件名。  
  
 **基类**  
 设置新类的基类。  
  
 **访问**  
 设置对新类的基类成员的访问。  访问修饰符是指定其他类对类成员函数的访问级别的关键字。  关于如何指定访问的更多信息，请参见 [成员访问控制](../cpp/member-access-control-cpp.md)。  默认情况下，类访问级别设置为`public`。  
  
-   `public`  
  
-   `protected`  
  
-   `private`  
  
-   **“默认值”**（不生成访问修饰符）。  
  
 **虚析构函数**  
 指定类析构函数是否是虚的。  使用虚析构函数帮助确保当删除导出类的实例时调用正确的析构函数。  
  
 **内联**  
 将类构造函数和类定义两者生成为头文件中的内联函数。  
  
 **Managed**  
 选定后，将添加一个托管类和标题文件。  删除后，添加本机类和标题文件。  
  
## 请参阅  
 [添加一般 C\+\+ 类](../ide/adding-a-generic-cpp-class.md)