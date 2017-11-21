---
title: "DCOM 历史记录 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Remote Automation, DCOM
- DCOM, about DCOM
- DCOM
ms.assetid: c21aa0ea-1396-4b52-b77f-88fb0fdd2a5c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9e5607fd240c7a97691189b8a3afa5e7c0171e26
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="history-of-dcom"></a>DCOM 历史记录
当自动化于早期 1993年问世时，已支持的使用仅在同一台计算机上运行的应用程序之间。 但是，因为它共享 OLE，即，COM （或组件对象模型） 的其余部分所在的同一个基础结构，它始终本来，COM 本身已更新为包括远程处理功能时，它将变得"远程"。 它原来的计划，从纯粹的本地操作转换为分布式操作需要很少或没有更改现有代码。  
  
 因此而言有什么用途"进行远程处理本地 COM 规定接口的使用者，驻留在该接口的提供程序所在的同一计算机上和执行。 例如，Microsoft Visual Basic 可以控制在台式计算机上的 Microsoft Excel 副本，但它不是支持将定向 Excel 在其他计算机上的执行。 与分布式 COM 的开发，接口的使用者不再需要驻留在与接口提供程序在其上执行相同的计算机上。  
  
 一旦 COM 改写，以便跨网络，然后任何接口未与本地执行模型 (某些接口已具有对本地计算机设施的固有依赖，例如那些绘制接口的方法具有形式的设备上下文的句柄参数） 都要分发的功能。 接口使用者会使给定的接口; 的请求其他计算机上，运行的 （或运行） 的实例可能提供该接口。 在 COM 分发机制将连接到这种方式中的提供程序的使用者，所做的使用者的方法调用将出现在提供程序结束时，将在其中执行它们。 任何返回值将然后发送回使用者。 为所有何种目的，分发的行为是透明的使用者和提供程序。  
  
 此类的 COM 各种现在存在。 DCOM （针对"分布式 COM") 具有附带的 Windows NT 4.0 版开头并包括 Windows 2000 的版本。 自后期 1996 年，它也已经提供面向 Windows 9x x。 在这两种情况下，DCOM 使用某些实用工具，提供本地和远程 COM 功能包括一套更换和其他 Dll。 它现在因此是基于 Win32 的平台的固有部分，并将可在其他平台上由其他组织随着时间的推移。  
  
## <a name="in-this-section"></a>本节内容  
 [远程自动化放置何处](where-does-remote-automation-fit-in-q.md)  
  
 [远程自动化提供什么](what-does-remote-automation-provide-q.md)  
  
## <a name="see-also"></a>另请参阅  
 [远程自动化](../mfc/remote-automation.md)
