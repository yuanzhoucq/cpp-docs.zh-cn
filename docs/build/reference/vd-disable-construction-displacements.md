---
title: "/vd（禁用构造置换） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/vd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/vd0 编译器选项 [C++]"
  - "/vd1 编译器选项 [C++]"
  - "/vdn（禁用结构置换）编译器选项"
  - "构造函数置换"
  - "“禁用结构置换”编译器选项"
  - "置换编译器选项"
  - "vd0 编译器选项 [C++]"
  - "-vd0 编译器选项 [C++]"
  - "vd1 编译器选项 [C++]"
  - "-vd1 编译器选项 [C++]"
  - "vtordisp 字段"
ms.assetid: 93258964-14d7-4b1c-9cbc-d6f4d74eab69
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# /vd（禁用构造置换）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
/vdn  
```  
  
## Arguments  
 `0`  
 取消 vtordisp 构造函数\/析构函数置换成员。  仅在确定所有的类构造函数和析构函数实际调用虚函数时选择此选项。  
  
 `1`  
 启用创建隐藏 vtordisp 构造函数\/析构函数置换成员。  此选项为默认选项。  
  
 `2`  
 允许对正在构造的对象使用 [dynamic\_cast 运算符](../../cpp/dynamic-cast-operator.md)。  例如，从虚拟基类到派生类的 dynamic\_cast。  
  
 当虚拟基有虚函数时，**\/vd2** 添加 vtordisp 字段。  **\/vd1** 应是足够的。  最常见的需要 **\/vd2** 的情况是虚拟基中的唯一虚函数是析构函数。  
  
## 备注  
 这些选项仅适用于使用虚拟基的 C\+\+ 代码。  
  
 [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] 在使用虚拟继承的情况下实现 C\+\+ 构造置换支持。  构造置换解决在构造其他派生类期间，从构造函数调用在虚拟基中声明并在派生类中重写的虚函数时产生的问题。  
  
 问题是：由于对类的虚拟基的置换与对其派生类的置换之间有差异，可能会向虚函数传递错误的 `this` 指针。  该解决方案向类的各个虚拟基提供称作 vtordisp 字段的单个构造置换调整。  
  
 默认情况下，每当代码定义用户定义的构造函数和析构函数并且还重写虚拟基的虚函数时，引入 vtordisp 字段。  
  
 这些选项影响整个源文件。  使用 [vtordisp](../../preprocessor/vtordisp.md) 可在每个类的基础上取消然后重新启用 vtordisp 字段。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“命令行”**属性页。  
  
4.  在**“附加选项”**框中键入编译器选项。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)