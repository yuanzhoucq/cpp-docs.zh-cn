---
title: "/vmm、/vms、/vmv（通用表示形式） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/vms"
  - "/vmm"
  - "/vmv"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/vmm 编译器选项 [C++]"
  - "/vms 编译器选项 [C++]"
  - "/vmv 编译器选项 [C++]"
  - "通用目的表示形式编译器选项"
  - "“单一继承”编译器选项"
  - "“虚拟继承”编译器选项"
  - "vmm 编译器选项 [C++]"
  - "-vmm 编译器选项 [C++]"
  - "vms 编译器选项 [C++]"
  - "-vms 编译器选项 [C++]"
  - "vmv 编译器选项 [C++]"
  - "-vmv 编译器选项 [C++]"
ms.assetid: 0fcd7ae0-3031-4c62-a2a8-e154c8685dae
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /vmm、/vms、/vmv（通用表示形式）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当选择 [\/vmb、\/vmg（表示方法）](../../build/reference/vmb-vmg-representation-method.md)作为[表示方法](../../build/reference/vmb-vmg-representation-method.md)时使用。  这些选项指示尚未遇到的类定义的继承模型。  
  
## 语法  
  
```  
/vmm  
/vms  
/vmv  
```  
  
## 备注  
 下表描述了这些选项。  
  
|选项|说明|  
|--------|--------|  
|**\/vmm**|指定指向类成员的指针的最通用表示形式为使用多重继承的表示形式。<br /><br /> [\#pragma pointers\_to\_members](../../preprocessor/pointers-to-members.md) 相应的 [inheritance](../../cpp/inheritance-keywords.md) 关键字和参数是 **multiple\_inheritance**。<br /><br /> 此表示形式比单一继承需要的表示形式大。<br /><br /> 如果类定义（已为其声明指向成员的指针）的继承模型为虚拟，编译器将生成错误。|  
|**\/vms**|指定指向类成员的指针的最通用表示形式为不使用继承或使用单一继承的表示形式。<br /><br /> [\#pragma pointers\_to\_members](../../preprocessor/pointers-to-members.md) 相应的 [inheritance 关键字](../../cpp/inheritance-keywords.md)和参数是 **single\_inheritance**。<br /><br /> 这是指向类成员的指针的最小可能表示形式。<br /><br /> 如果类定义（已为其声明指向成员的指针）的继承模型为多重或虚拟，编译器将生成错误。|  
|**\/vmv**|指定指向类成员的指针的最通用表示形式为使用虚拟继承的表示形式。  它从不导致错误并且为默认设置。<br /><br /> [\#pragma pointers\_to\_members](../../preprocessor/pointers-to-members.md) 相应的 [inheritance 关键字](../../cpp/inheritance-keywords.md)和参数是 **virtual\_inheritance**。<br /><br /> 与其他选项相比，此选项需要较大的指针和解释该指针的附加代码。|  
  
 当指定这些继承模型选项之一时，该模型用于所有指向类成员的指针，而不管它们的继承类型或指针是在类前还是类后声明。  因此，如果总是使用单一继承类，则可以通过用 **\/vms** 编译来减小代码大小；然而，如果要使用最通用的情形（以数据表示形式最大为代价），请用  **\/vmv** 编译。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“命令行”**属性页。  
  
4.  在**“附加选项”**框中键入编译器选项。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [\/vmb、\/vmg（表示方法）](../../build/reference/vmb-vmg-representation-method.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)