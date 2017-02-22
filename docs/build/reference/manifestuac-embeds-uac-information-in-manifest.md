---
title: "/MANIFESTUAC（将 UAC 信息嵌入到清单中） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.UACUIAccess"
  - "VC.Project.VCLinkerTool.UACExecutionLevel"
  - "VC.Project.VCLinkerTool.EnableUAC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/MANIFESTUAC 链接器选项"
  - "MANIFESTUAC 链接器选项"
  - "-MANIFESTUAC 链接器选项"
ms.assetid: 2d243c39-fa13-493c-b56f-d0d972a1603a
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /MANIFESTUAC（将 UAC 信息嵌入到清单中）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定是否将用户帐户控制 \(UAC\) 信息嵌入到程序清单中。  
  
## 语法  
  
```  
/MANIFESTUAC  
/MANIFESTUAC:NO  
/MANIFESTUAC:fragment  
/MANIFESTUAC:level=_level  
/MANIFESTUAC:uiAccess=_uiAccess  
```  
  
#### 参数  
 `fragment`  
 一个字符串，它包含 `level` 和 `uiAccess` 值。  有关更多信息，请参见本主题中后面的“备注”部分。  
  
 `_level`  
 asInvoker、highestAvailable 或 requireAdministrator 之一。  默认为 asInvoker。  有关更多信息，请参见本主题中后面的“备注”部分。  
  
 `_uiAccess`  
 如果您希望应用程序绕过用户界面保护级别并将输入引导到桌面上的更高权限窗口，则为 `true`；否则为 `false`。  默认为 `false`。  仅针对用户界面辅助功能应用程序设置为 `true`。  
  
## 备注  
 如果您在命令行上指定多个 \/MANIFESTUAC 选项，则最后输入的选项优先级最高。  
  
 \/MANIFESTUAC:level 的选项包括：  
  
-   `asInvoker`：应用程序将使用与启动它的进程相同的权限运行。  可通过选择**“以管理员身份运行”**将应用程序提升为更高权限。  
  
-   highestAvailable：应用程序将使用可能的最高权限级别运行。  如果启动该应用程序的用户为管理员组的一个成员，则此选项与 requireAdministrator 相同。  如果可用的最高权限级别高于打开进程的级别，则系统将提示提供凭据。  
  
-   requireAdministrator：应用程序将使用管理员权限运行。  启动该应用程序的用户必须是管理员组的一个成员。  如果打开进程未使用管理权限运行，则系统将提示提供凭据。  
  
 您可以通过使用 \/MANIFESTUAC:fragment 选项在一个步骤中指定 level 和 uiAccess 值。  代码片段的格式必须是：  
  
```  
"level=[ asInvoker | highestAvailable | requireAdministrator ] uiAccess=[ true | false ]"  
```  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展开**“配置属性”**节点。  
  
3.  展开**“链接器”**节点。  
  
4.  选择**“清单文件”**属性页。  
  
5.  修改**“启用用户帐户控制\(UAC\)”**、**“UAC 执行级别”**和**“UAC 绕过 UI 保护”**属性。  
  
### 以编程方式设置此链接器选项  
  
1.  请参见 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableUAC%2A>、<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACExecutionLevel%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACUIAccess%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)