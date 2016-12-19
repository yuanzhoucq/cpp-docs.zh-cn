---
title: "如何：针对 64 位平台配置 Visual C++ 项目 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "平台 [C++], 64 位"
  - "64 位编程 [C++], 配置项目"
  - "项目配置 [C++]"
ms.assetid: 2b9ae001-df36-4750-83b2-982145d632ad
caps.latest.revision: 22
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 如何：针对 64 位平台配置 Visual C++ 项目
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以使用 Visual Studio 中的项目配置来设置面向 64 位平台的 C\+\+ 应用程序。 还可以将 Win32 项目设置迁移到 64 位项目配置。  
  
### 设置项目以面向 64 位平台  
  
1.  打开要配置的 C\+\+ 项目。  
  
2.  打开该项目的属性页面。 有关详细信息，请参阅[如何：打开项目属性页](../misc/how-to-open-project-property-pages.md)。  
  
    > [!NOTE]
    >  对于.NET 项目，请确保在“\<项目名称\>属性页面”对话框中选择“配置属性”节点或一个子节点；否则“配置管理器”按钮仍然不可用。  
  
3.  选择“配置管理器”按钮以打开“配置管理器”对话框。  
  
4.  在“活动解决方案平台”下拉列表中，选择“\<新建…\>”选项来打开“新建解决方案平台”对话框。  
  
5.  在“键入或选择新平台”下拉列表中，选择 64 位平台。  
  
    > [!NOTE]
    >  在“新建解决方案平台”对话框中，可以使用“从此处复制设置”选项将现有项目设置复制到新的 64 位项目配置中。  
  
6.  选择**“确定”**按钮。 前一步中选择的平台出现在“配置管理器”对话框的“活动解决方案平台”下。  
  
7.  请在“配置管理器”对话框中选择“关闭”按钮，然后在“\<项目名称\>属性页面”对话框中选择“确定”按钮。  
  
### 将 Win32 项目设置复制到 64 位项目配置中  
  
-   当设置面向 64 位平台的项目时，如果“新建解决方案平台”对话框处于打开状态，请在“从此处复制设置”下拉列表中选择“Win32”。 在项目级别会自动更新这些项目设置：  
  
    -   [\/MACHINE](../build/reference/machine-specify-target-platform.md) 链接器选项设置为 **\/MACHINE:X64**。  
  
    -   关闭“注册输出”。 有关详细信息，请参阅[“链接器”属性页](../ide/linker-property-pages.md)。  
  
    -   “目标环境”设置为 **\/env x64**。 有关详细信息，请参阅[MIDL 属性页：常规](../ide/midl-property-pages-general.md)。  
  
    -   “验证参数”被清除并且重置为默认值。 有关详细信息，请参阅[MIDL 属性页：高级](../ide/midl-property-pages-advanced.md)。  
  
    -   如果在 Win32 项目配置中已将“调试信息格式”设置为 **\/ZI**，则在 64 位项目配置中将设置为 **\/Zi**。 有关详细信息，请参阅[\/Z7、\/Zi、\/ZI（调试信息格式）](../build/reference/z7-zi-zi-debug-information-format.md)。  
  
    > [!NOTE]
    >  如果在文件级重写，则不会更改这些项目属性。  
  
## 请参阅  
 [64 位应用程序](../Topic/64-bit%20Applications.md)   
 [配置 64 位的程序](../build/configuring-programs-for-64-bit-visual-cpp.md)   
 [调试 64 位应用程序](../Topic/Debug%2064-Bit%20Applications.md)