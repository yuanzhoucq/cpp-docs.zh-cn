---
title: 资源编译器警告 RC4005 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC4005
dev_langs:
- C++
helpviewer_keywords:
- RC4005
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 724764e443d4ab999c1df1247e9f5572ebdb2078
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-warning-rc4005"></a>资源编译器警告 RC4005
identifier： 宏重定义  
  
 标识符被定义两次。 编译器使用在第二个宏的定义。  
  
 可以通过定义宏，在命令行上和中使用的代码导致此警告`#define`指令。 它还可以通过从包含文件导入的宏导致。  
  
 若要消除此警告，请删除其中一个定义，或使用`#undef`指令之前第二个定义。