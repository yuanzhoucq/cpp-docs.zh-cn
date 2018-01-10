---
title: "命令宏和选项宏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- options macros
- command macros in NMAKE
- macros, options macros
- macros, command macros
ms.assetid: 50dff03c-0dc3-4a8a-9a17-57e0e4ea9bac
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 06f5d48395c0395a85c90096bf2dbad8627ac41a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="command-macros-and-options-macros"></a>命令宏和选项宏
命令宏是 Microsoft 产品的预定义的。 选项宏表示这些产品的选项，并且默认情况下未定义。 同时使用预定义的推理规则中，可以用于描述块或用户定义的推理规则中。 可以重新定义命令宏来表示部分或全部命令行，其中包括选项。 如果未定义，options 宏将生成一个 null 字符串。  
  
|Microsoft 产品|命令宏|定义为|选项宏|  
|-----------------------|-------------------|----------------|-------------------|  
|宏汇编程序|**为**|ml|**AFLAGS**|  
|基本编译器|**业务连续性**|业务连续性|**BFLAGS**|  
|C 编译器|**抄送**|Cl|**CFLAGS**|  
|C++ 编译器|**CPP**|Cl|**CPPFLAGS**|  
|C++ 编译器|**CXX**|Cl|**CXXFLAGS**|  
|资源编译器|**RC**|rc|**RFLAGS**|  
  
## <a name="see-also"></a>请参阅  
 [特殊 NMAKE 宏](../build/special-nmake-macros.md)