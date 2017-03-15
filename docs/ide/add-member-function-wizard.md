---
title: "添加成员函数向导 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.function.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "添加成员函数向导 [C++]"
ms.assetid: 13b6defc-faa6-4d57-83db-9dd854cbea3d
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 添加成员函数向导
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

该向导将成员函数声明添加到头文件，将存根 \(stub\) 成员函数实现添加到选定类的实现文件。  
  
 使用该向导添加了成员函数后，可以在开发环境中编辑代码。  
  
 **返回类型**  
 设置正在添加的成员函数的返回类型。  可以提供自己的返回类型，或从可用类型列表中选择。  有关类型的信息，请参见[基本类型](../cpp/fundamental-types-cpp.md)。  
  
||||  
|-|-|-|  
|`char`|`int`|`unsigned int`|  
|**double**|**long**|`unsigned long`|  
|**float**|**short**|`void`|  
|`HRESULT`|`unsigned char`||  
  
 **函数名**  
 设置正在添加的成员函数的名称。  
  
 **参数类型**  
 如果正在添加的成员函数有参数，设置该函数的参数类型。  可以提供自己的参数类型，或从可用类型列表中选择。  
  
||||  
|-|-|-|  
|`char`|`int`|`unsigned char`|  
|**double**|**long**|`unsigned int`|  
|**float**|**short**|`unsigned long`|  
  
 **参数名**  
 如果正在添加的成员函数有参数，设置该函数的参数名。  
  
 **参数列表**  
 显示已经添加到成员函数的参数列表。  若要向该列表添加参数，请在“参数类型”和“参数名”框中提供类型和名称并单击“添加”。  若要从该列表中移除某个参数，请选择该参数并单击“移除”。  
  
 **访问**  
 设置对成员函数的访问。  访问修饰符是指定其他类对成员函数的访问的关键字。  有关指定访问的更多信息，请参见[成员访问控制](../cpp/member-access-control-cpp.md)。  默认情况下，成员函数的访问级别设置为 **public**。  
  
-   [public](../cpp/public-cpp.md)  
  
-   [protected](../cpp/protected-cpp.md)  
  
-   [private](../cpp/private-cpp.md)  
  
 检查新成员函数是静态的还是虚拟的，是内联的还是纯的。  如果将成员函数设置为纯函数，则“虚”\(`Virtual`\) 复选框处于选中状态，“内联”\(**Inline**\) 复选框变得不可用。  默认为非静态、非虚成员函数。  
  
|选项|说明|  
|--------|--------|  
|[Static](../misc/static-cpp.md)|指定函数像全局函数一样使用，可以在类的外部调用，即使没有类实例化。  这类成员函数不能访问非静态成员。  被指定为 `Static` 的成员函数不能是虚的。|  
|[Virtual](../cpp/virtual-cpp.md)|确保调用对象的正确成员函数，忽略用于调用成员函数的表达式。  被指定为 `Virtual` 的成员函数不能是静态的。|  
|**纯 \(Pure\)**|指示没有为正在声明的虚成员函数提供实现，因此只能在虚成员函数上指定“纯”。  有关更多信息，请参见[类成员声明语法](../misc/class-member-declaration-syntax.md)。<br /><br /> 包含至少一个纯虚成员函数的类被视为抽象类。  从抽象类导出的类必须实现纯虚成员函数或者它们也是抽象类。|  
|[内联](../cpp/inline-functions-cpp.md)|指示编译器在调用成员函数的每个位置插入该成员函数体的副本。  被指定为“内联”的成员函数不能是纯的。|  
  
 **.cpp 文件**  
 设置存根 \(stub\) 成员函数实现写入的文件位置。  默认情况下，它写入成员函数添加到的类的 .cpp 文件。  单击省略号按钮以更改文件名。  成员函数实现被添加到选定文件的内容中。  
  
 **Comment**  
 提供成员函数头文件中的注释。  
  
 **函数签名**  
 显示单击“完成”时成员函数出现在代码中的样子。  无法编辑此框中的文本。  若要更改成员函数，请在向导中更改适当的框。  
  
## 请参阅  
 [添加成员函数](../ide/adding-a-member-function-visual-cpp.md)