---
title: "/volatile（volatile 关键字解释） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/volatile:iso"
  - "/volatile:ms"
  - "/volatile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/volatile 编译器选项"
  - "/volatile 编译器选项 [C++]"
  - "volatile 编译器选项"
  - "-volatile 编译器选项"
  - "volatile 编译器选项 [C++]"
  - "-volatile 编译器选项 [C++]"
ms.assetid: 9d08fcc6-5bda-44c8-8151-8d8d54f164b8
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# /volatile（volatile 关键字解释）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定如何解释 [volatile](../../cpp/volatile-cpp.md) 关键字。  
  
## 语法  
  
```  
/volatile:{iso|ms}  
```  
  
## Arguments  
 **\/volatile:iso**  
 选择严格的 `volatile` 语义，如 ISO 标准 C\+\+ 语言所定义的一样。  获取\/释放语义无法保证可变访问。  如果编译器面向 ARM，则这是 `volatile` 的默认值解释。  
  
 **\/volatile:ms**  
 选择添加了 ISO 标准 C\+\+ 语言以外的内存顺序调整保证的 Microsoft 扩展 `volatile` 语义。  获取\/释放语义可保证可变访问。  但是，此选项还强制编译器生成硬件内存障碍，这可能会显著添加 ARM 和其他弱内存命令体系结构的开销。  如果编译器面向除 ARM 外的任何平台，则这是 `volatile` 的默认值解释。  
  
## 备注  
 强烈建议您在处理在线程之间共享的内存时，将显式同步基元和固有编译器与 **\/volatile:iso** 一起使用。  有关详细信息，请参阅[volatile](../../cpp/volatile-cpp.md)。  
  
 如果在项目中间移植现有代码或更改此选项，启用警告 [C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md) 标识受语义上差异影响的代码位置。  
  
 没有与 `#pragma` 等效的方法来控制该选项。  
  
### 在 Visual Studio 中设置 \/volatile 编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参阅[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  选择 **C\/C\+\+** 文件夹。  
  
3.  选择**“命令行”**属性页。  
  
4.  在“附加选项”对话框中，添加 `/volatile:iso` 或 `/volatile:ms`。  
  
## 请参阅  
 [volatile](../../cpp/volatile-cpp.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)