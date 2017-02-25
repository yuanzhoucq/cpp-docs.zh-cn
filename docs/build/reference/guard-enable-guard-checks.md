---
title: "/GUARD（启用防护检查） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 72758e23-70ac-4616-94d7-d767477406d1
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# /GUARD（启用防护检查）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在可执行映像中，为控制流防护检查指定支持。  
  
## 语法  
  
```  
/GUARD:{CF|NO}  
```  
  
## 备注  
 当指定 \/GUARD:CF 时，链接器将修改 .dll 或 .exe 的标头，以指示支持控制流防护 \(CFG\) 运行时检查。  链接器还会将所需的控制流目标地址数据添加到标头。  默认情况下，禁用 \/GUARD:CF。  可以通过使用 \/GUARD:NO 显式禁用。  为提高效率，\/GUARD:CF 还需要 [\/DYNAMICBASE（使用地址空间布局随机化功能）](../../build/reference/dynamicbase-use-address-space-layout-randomization.md) 链接器选项，该选项默认处于启用状态。  
  
 当使用 [\/guard:cf](../../build/reference/guard-enable-control-flow-guard.md) 选项编译源代码时，编译器将通过检查对可能目标地址的所有间接调用来分析控制流。  编译器将插入代码，以验证间接调用指令的目标地址在运行时是否处于已知的目标地址列表中。  支持 CFG 的操作系统将停止未能通过 CFG 运行时检查的程序。  这提高了攻击者使用数据损坏来更改调用目标，以执行恶意代码的难度。  
  
 必须对编译器和链接器指定 \/GUARD:CF 选项，以创建支持 CFG 的可执行映像。  编译但未使用 \/GUARD:CF 链接的代码会产生运行时检查开销，但不会启用 CFG 保护。  当对 `cl` 命令指定 \/GUARD:CF 选项以一次性完成编译和链接时，编译器会将标志传递给链接器。  当在 Visual Studio 中设置了**“控制流防护”**属性时，将向编译器和链接器传递 \/GUARD:CF 选项。  当单独编译对象文件或库时，必须在`链接`命令中显式指定选项。  
  
### 在 Visual Studio 中设置此链接器选项  
  
1.  打开项目“属性页”对话框。  有关详细信息，请参阅[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  依次展开**“配置属性”**、**“链接器”**、**“命令行”**。  
  
3.  在**“其他选项”**中，输入 `/GUARD:CF`。  
  
## 请参阅  
 [\/guard（启用控制流保护）](../../build/reference/guard-enable-control-flow-guard.md)   
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)