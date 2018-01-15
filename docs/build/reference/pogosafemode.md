---
title: "PogoSafeMode |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: PogoSafeMode
ms.assetid: 2daeeff7-44cb-417f-90eb-6b9edf658533
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5f40dad6feff9e49deeb495e8acbf2584dea3e41
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="pogosafemode"></a>PogoSafeMode
指定是否使用快速模式或安全模式的应用程序分析。  
  
## <a name="syntax"></a>语法  
  
```  
PogoSafeMode  
```  
  
## <a name="remarks"></a>备注  
 按配置优化 (PGO) 的分析阶段有两种可能的模式： 快速模式和安全模式。 分析在快速模式下时，它使用**INC**指令来增加数据计数器。 **INC**指令速度更快，但不是线程安全。 分析在安全模式下时，它使用**锁 INC**指令来增加数据计数器。 **锁 INC**指令具有相同的功能**INC**指令，并且是线程安全的但它是低于**INC**指令。  
  
 默认情况下，PGO 分析会在运行快速模式。 `PogoSafeMode`是仅需要你想要使用安全模式。  
  
 若要运行 PGO 分析在安全模式下，必须使用环境变量`PogoSafeMode`或链接器开关**-PogoSafeMode**，取决于系统。 如果你正在执行分析在 x64 计算机，你必须使用链接器开关。 如果你正在执行分析 x86 计算机，你必须定义环境变量的任何值之前启动优化过程。  
  
## <a name="example"></a>示例  
  
```  
set PogoSafeMode=1  
```  
  
## <a name="see-also"></a>请参阅  
 [按配置优化的环境变量](../../build/reference/environment-variables-for-profile-guided-optimizations.md)   
 [按配置文件优化](../../build/reference/profile-guided-optimizations.md)