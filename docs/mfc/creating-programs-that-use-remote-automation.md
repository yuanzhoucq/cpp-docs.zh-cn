---
title: "创建使用远程自动化的程序 | Microsoft Docs"
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
helpviewer_keywords: 
  - "远程自动化, 创建程序"
ms.assetid: 8eb31320-1037-4029-b1f3-fdc9406dbaf1
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 创建使用远程自动化的程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

不重新编译应用，需要不负责重新链接的所有自动的，需要对象和自动化任何控制器，则可以使用远程的自动化不会更改其任何到源代码中。  一旦具有本地工作的设置 \(即在同一计算机\)，则需要执行一些步骤仅远程执行。  
  
#### 执行远程的自动化对象  
  
1.  注册在客户端计算机或的应用程序。  
  
2.  配置客户端访问使用远程服务器。  
  
3.  安装和注册服务器计算机上或计算机的应用程序。  
  
4.  服务器允许远程配置的激活。  
  
5.  安装服务器计算机管理器的自动化。  
  
6.  对服务器上的自动化管理器。  
  
7.  对客户的应用程序。  
  
 步骤 1 通过加载和执行服务器应用程序可以轻松地实现上客户端，因为多数服务器是自注册。  如果预先测试设置局部，此阶段已完成。  如果服务器应用不是注册的自，您可能希望这样使其成为。  否则，您需要提供本地用户运行此步骤执行的方式。  如果您不执行这些操作，您或管理员需要手动编辑注册表，对于所有推荐的过程，但最高级用户。  
  
 步骤 2 对涉及使用远程连接自动化 \(RAC\) 管理器。  运行 RAC 管理器并确保服务器连接选项卡为最高。  接下来，请查找服务器对象的输入在 **OLE Classes** 窗格中单击。  然后移至 **网络地址** 组合框并输入远程的可执行文件运行将服务器计算机的名称。  例如，您可以键入\\\\MyServer 示。  然后从提供的列表中选择适当的 Web 协议。  您可能需要检查与网络管理员确定建议使用的协议。  在大多数情况下，这会是 TCP\/IP。  最后，您可能还希望选择身份验证级别。  在大多数情况下，这会将 \(无\) 或默认。  现在请在 **OLE Classes** 窗格的服务器。  这将导致您可以选择本地或远程操作的快捷菜单。  SELECT 远程。  
  
 步骤 3 对涉及正确安装和注册所选服务器计算机或计算机的服务器应用程序。  同样，如果应用程序自行注册，执行一次它还将注册该文件。  
  
 步骤 4 中配置该服务器允许远程执行。  运行服务器计算机的 RAC 管理器，并且确保 **Client Access** 选项卡具有焦点。  选择想要激活的模型 \(通常是 **Allow Remote Creates by Key**。  如果选择此选项，则还需要单击 **Allow Remote Activation** 复选框设置注册表项的值“Y”。  如果运行的 Windows NT 或 Windows 2000 和选择允许远程创建 \(ACL\) 选项，您也可以选择编辑 ACL 按 **Edit ACL** 按钮。  
  
 若要允许远程的自动化工作，然后需要确保自动化管理器是已安装并运行在服务器计算机或计算机。  如果未安装，请复制 AUTMGR32.EXE 为 Windows 系统目录。  有关如何执行此操作的信息，请参见 [远程安装的自动化](../mfc/remote-automation-installation.md)。  若要开始远程的自动化，请执行自动管理器。  它将显示的许多消息中显示的一个小的"状态"窗口。  一旦启动，要最小化。  如果要继续查看状态信息，可以在任务栏的 **Automation Manager** 选项卡还原窗口。  
  
 最后一步是对客户端应用程序的客户端。  如果您按照上述步骤，其应连接到服务器对象和精确执行，则局部较慢的一个点。  
  
 请注意 RAC 管理器还可以切换远程的自动化和分布式 COM \(DCOM 之间，DCOM\) 上支持的这些平台与单选按钮的单击。  如果选择了 DCOM，可以将各种配置选项。  有关详细信息，请参见 DCOM 文档。  
  
## 请参阅  
 [远程自动化](../mfc/remote-automation.md)   
 [使用 AUTOCLIK 和 AUTODRIV 运行远程自动化](../mfc/running-remote-automation-using-autoclik-and-autodriv.md)