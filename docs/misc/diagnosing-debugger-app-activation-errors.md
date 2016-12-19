---
title: "诊断调试器应用程序激活错误 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.app_activation_failure"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 558ddc6d-0952-4617-84b8-0838717febcc
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "susanno"
manager: "douge"
---
# 诊断调试器应用程序激活错误
当你尝试在 Visual Studio 调试器中启动 Windows 应用商店应用时，可能会收到下列错误之一：  
  
 **8061**  
  
```  
Unable to activate Windows Store app 'AppName'. The ProcessName process started, but the activation request failed with error 'ErrorNumber'  
```  
  
 **8062**  
  
```  
Unable to activate Windows Store app 'AppName'. The activation request failed with error 'ErrorNumber'  
```  
  
## 诊断这些错误  
 无法通过可靠方式纠正这些错误。  使用这些技术诊断问题。  
  
### 使用事件查看器  
  
1.  打开事件查看器（在 Windows“开始”菜单上搜索**事件查看器**。）在事件查看器中，在树中导航到**“Application and Services Log\\Microsoft\\Windows\\Apps”**文件夹。  
  
2.  将视图筛选到事件 ID：5900\-6000  
  
3.  查看日志并了解发生了什么。  
  
### 使用本机调试器  
 将项目配置为在本机调试器下运行。  
  
 在 Visual Studio 中，在启动项目的属性页的**“调试”**（在 C 和 JavaScript 中为**“调试”**）页上，将**“调试器类型”**设置为**“仅限本机”**。  
  
 通过查看输出窗口来查看引发的异常。  你可能希望将调试器配置为在引发这些异常时停止。  
  
## 修复应用许可证错误  
 你可能会看到包含“由于许可证出现问题，导致此应用无法运行”的激活错误。可以尝试以下解决方法：  
  
-   在**“生成”**菜单上，选择**“清理解决方案”**，然后在文件资源管理器中打开解决方案文件夹，再删除 **bin** 和 **obj** 文件夹。  然后，依次选择**“生成”**、**“重新生成解决方案”**。  通过重新生成解决方案来重新创建所需的文件夹。  
  
-   在“开始”屏幕上选择相应的应用，然后在应用栏上选择“卸载”。  清除并重新生成解决方案。  
  
-   在使用管理员特权运行的命令提示符下，使用 PowerShell 命令来移除并重新安装开发人员许可证。  清除并重新生成解决方案。  请参阅[在命令提示符下获取开发人员许可证](http://msdn.microsoft.com/library/windows/apps/Hh974578.aspx#getting_a_developer_license_at_a_command_prompt)。