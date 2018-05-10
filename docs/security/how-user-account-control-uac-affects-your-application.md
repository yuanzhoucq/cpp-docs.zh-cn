---
title: 用户帐户控制 (UAC) 如何影响你的应用程序 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- UAC [C++]
- security [C++], User Account Control
- user accounts [C++]
- User Account Control [C++]
ms.assetid: 0d001870-253e-4989-b689-f78035953799
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 020a7a16e38ee40c99a7a5b77c88002e3135bfa1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="how-user-account-control-uac-affects-your-application"></a>用户帐户控制 (UAC) 如何影响应用程序
用户帐户控制 (UAC) 是 Windows Vista 的一项功能，其中用户帐户具有有限的特权。 可以在下列站点找到关于 UAC 的详细信息：  
  
-   [Windows Vista 用户帐户控制分步指南](http://go.microsoft.com/fwlink/p/?linkid=53781)  
  
-   [开发人员最佳做法和最小特权环境中的应用程序的指导原则](http://go.microsoft.com/fwlink/p/?linkid=82444)  
  
-   [了解和 Windows Vista 中配置用户帐户控制](http://go.microsoft.com/fwlink/p/?linkid=82445)  
  
## <a name="building-projects-after-enabling-uac"></a>在启用 UAC 后生成项目  
 如果在禁用 UAC 的 Windows Vista 中生成 Visual C++ 项目，并在以后启用 UAC，则必须清除并重新生成项目，该项目才能正常工作。  
  
## <a name="applications-that-require-administrative-privileges"></a>需要管理特权的应用程序  
 默认情况下，Visual C++ 链接器将 UAC 片段嵌入具有 `asInvoker` 执行级别的应用程序清单。 如果应用程序需要管理特权才能正确运行（例如，修改注册表的 HKLM 节点或者写入磁盘的受保护区域，如 Windows 目录），则必须修改应用程序。  
  
 第一个选项是修改要更改到将执行级别的清单的 UAC 片段*requireAdministrator*。 然后，应用程序在运行之前将提示用户提供管理凭据。 有关如何执行此操作的信息，请参阅[/MANIFESTUAC （将 UAC 信息嵌入在清单中）](../build/reference/manifestuac-embeds-uac-information-in-manifest.md)。  
  
 第二个选项是不通过指定将 UAC 片段嵌入到清单 **/manifestuac: no**链接器选项。 在这种情况下，应用程序将以虚拟化方式运行。 在应用程序结束后，对注册表或文件系统的任何更改将不会保留。  
  
 下面的流程图描述了应用程序的运行方式取决于是否启用了 UAC 和应用程序是否有 UAC 清单：  
  
 ![Windows Vista 加载程序行为](media/uacflowchart.png "UACflowchart")  
  
## <a name="see-also"></a>请参阅  
 [安全性最佳做法](security-best-practices-for-cpp.md)