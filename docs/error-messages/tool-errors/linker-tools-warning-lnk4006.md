---
title: "链接器工具警告 LNK4006 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4006"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4006"
ms.assetid: 3a637d17-1676-4ea6-bd8b-290137d28d3b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具警告 LNK4006
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

符号已在对象中定义；已忽略第二个定义  
  
 以修饰形式显示的给定 `symbol` 被多次定义。  遇到此警告时，`symbol` 将被添加两次，但只使用它的第一个形式。  
  
 尝试将两个导入库合并为一个库时会得到此警告。  
  
 如果您正在重新生成 C 运行库，则可以忽略此消息。  
  
### 通过使用下面可能的解决方案进行修复  
  
1.  给定的 `symbol` 可能是封装函数，通过用 [\/Gy](../../build/reference/gy-enable-function-level-linking.md) 进行编译创建的。  该符号包括在多个文件中，但在各编译间已改变。  重新编译所有包含 `symbol` 的文件。  
  
2.  可能以不同的形式在不同库中的两个成员对象中定义给定 `symbol`。  
  
3.  绝对符号可能被定义了两次，每次定义的值不同。  
  
4.  如果在组合库时收到该错误信息，则所添加的库中已有 `symbol`。