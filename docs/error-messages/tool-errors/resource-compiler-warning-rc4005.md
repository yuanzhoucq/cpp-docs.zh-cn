---
title: "资源编译器警告 RC4005 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- RC4005
dev_langs:
- C++
helpviewer_keywords:
- RC4005
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8f27de973f0ff18493c182bdf1feb3f2812f39af
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-warning-rc4005"></a>资源编译器警告 RC4005
identifier： 宏重定义  
  
 标识符被定义两次。 编译器使用在第二个宏的定义。  
  
 可以通过定义宏，在命令行上和中使用的代码导致此警告`#define`指令。 它还可以通过从包含文件导入的宏导致。  
  
 若要消除此警告，请删除其中一个定义，或使用`#undef`指令之前第二个定义。