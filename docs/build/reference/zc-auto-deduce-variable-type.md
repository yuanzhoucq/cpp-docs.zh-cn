---
title: "/Zc:auto（推导变量类型） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/Zc:auto"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zc 编译器选项 (C++)"
  - "推导变量类型 (C++)"
  - "Zc 编译器选项 (C++)"
  - "-Zc 编译器选项 (C++)"
ms.assetid: 5f5bc102-44c3-4688-bbe1-080594dcee5c
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# /Zc:auto（推导变量类型）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**\/Zc:auto\[\-\]** 编译器选项指示编译器如何使用 [auto 关键字](../../cpp/auto-keyword.md)来声明变量。  如果指定默认选项 **\/Zc:auto**，编译器从其初始化表达式中推导声明的变量的类型。  如果指定  **\/Zc:auto\-**，编译器将该变量分配给自动存储类。  
  
## 语法  
  
```  
/Zc:auto[-]  
```  
  
## 备注  
 C\+\+ 标准为 `auto` 关键字定义了初始和修订的含义。  在 [!INCLUDE[cpp_dev10_long](../../build/includes/cpp_dev10_long_md.md)] 之前，该关键字在自动存储类中声明变量，即具有本地生存期的变量。  先从 [!INCLUDE[cpp_dev10_long](../../build/includes/cpp_dev10_long_md.md)] 开始，关键字可从声明的初始化表达式中推断出变量的类型。使用 **\/Zc:auto\[\-\]** 编译器选项能以指示编译器使用 `auto` 关键字的初始或修订的含义。  
  
 如果所使用的 `auto` 关键字与当前编译器选项发生冲突，编译器会发出适当的诊断消息。  有关详细信息，请参阅[auto 关键字](../../cpp/auto-keyword.md)。  有关使用 Visual C\+\+ 时的一致性问题的更多信息，请参见 [非标准行为](../../cpp/nonstandard-behavior.md)。  
  
### 在 Visual Studio 中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**“配置属性”**节点。  
  
3.  单击**“C\/C\+\+”**节点。  
  
4.  单击**“命令行”**节点。  
  
5.  将 **\/Zc:auto** 或 **\/Zc:auto\-** 添加到**“附加选项:”**窗格中。  
  
## 请参阅  
 [\/Zc（一致性）](../../build/reference/zc-conformance.md)   
 [auto 关键字](../../cpp/auto-keyword.md)