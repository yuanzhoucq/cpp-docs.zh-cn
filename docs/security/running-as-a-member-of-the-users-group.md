---
title: "作为用户组的成员运行 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PRJ0050
- VCD0047
dev_langs:
- C++
helpviewer_keywords:
- Users Group [C++]
- security [C++], Users Group
- Windows accounts [C++]
- non administrator users [C++]
- user accounts [C++]
- administrator (not running as) [C++]
ms.assetid: e48a03ec-d345-49f6-809a-1a291eecbc81
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ff2a33cd113b631ab6c17cdb02fb29e27d663c1e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="running-as-a-member-of-the-users-group"></a>作为用户组的成员运行
本主题说明将 Windows 用户帐户配置为用户组（与管理员组相对）的成员如何通过减少受恶意代码感染的机会来增强安全性。  
  
## <a name="security-risks"></a>安全风险  
 作为管理员运行使您的系统很容易受到几种类型的安全攻击，如“木马”和“缓冲区溢出”。 仅作为管理员访问 Internet 站点可能会损坏系统，因为从 Internet 站点下载的恶意代码可能攻击你的计算机。 如果攻击成功，则继承您的管理员权限，然后可以执行诸如删除所有文件、重新格式化硬盘以及创建具有管理员访问权限的新用户帐户等操作。  
  
## <a name="non-administrator-user-groups"></a>非管理员用户组  
 应将开发人员通常使用的 Windows 用户帐户添加到用户组或超级用户组。 还应将开发人员添加到调试组。 作为用户组的成员，您可以执行例程任务，包括在使您的计算机免受不必要的风险的情况下运行程序以及访问 Internet 站点。 作为超级用户组的成员，你也可以执行任务，如应用程序的安装、打印机的安装和大多数“控制面板”的操作。 如果你需要执行管理员任务（如升级操作系统或配置系统参数），应登录到管理员帐户，登录时间以足够完成执行管理任务为宜。 或者，Windows **runas**命令可以用于启动具有管理访问权限的特定应用程序。  
  
## <a name="exposing-customers-to-security-risks"></a>向客户公开安全风险  
 不作为管理员组的一部分对于开发人员来说尤其重要，除保护开发的计算机外，还防止开发人员因疏忽而编写了要求客户加入管理员组以执行所开发的应用程序的代码。 如果开发过程中引入需要管理员访问权限的代码，它将在运行时失败，并将应用程序现在需要客户作为管理员运行这一事实通知您。  
  
## <a name="code-that-requires-administrator-privileges"></a>需要管理员特权的代码  
 为了执行某些代码，可能需要管理员访问权限。 如果可能，应继续选择此代码。 需要管理员访问权限的代码操作示例如下：  
  
-   写入文件系统的保护区域，如 Windows 或 Program Files 目录  
  
-   写入注册表的保护区域，如 HKEY_LOCAL_MACHINE  
  
-   在全局程序集缓存 (GAC) 中安装程序集  
  
 通常，这些操作应限于应用程序的安装程序。 这使得用户只能临时使用管理员状态。  
  
## <a name="debugging"></a>调试  
 您可以通过成为调试组的一部分以非管理员身份调试在 Visual Studio（本机和托管）内启动的任何应用程序。 这包括可使用 Attach to Process 命令附加到正在运行的应用程序。 但是，为了调试由其他用户启动的本机或托管应用程序而成为管理员组的一部分是必要的。  
  
## <a name="see-also"></a>请参阅  
 [安全性最佳做法](security-best-practices-for-cpp.md)