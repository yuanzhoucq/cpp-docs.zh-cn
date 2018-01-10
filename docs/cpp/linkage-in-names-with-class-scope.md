---
title: "具有类范围的名称中的链接 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- scope [C++], linkage rules
- linkage [C++], scope linkage rules
- names [C++], scope linkage rules
- classes [C++], scope
- external linkage, scope linkage rules
- class names [C++], linkage
- classes [C++], names
- scope [C++], class names
- class scope [C++], linkage in names with
ms.assetid: 45275ff3-6e94-4967-82c8-ba540ef4da28
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 20e8204510f6f6e924e205b89dc9f95734b4b893
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linkage-in-names-with-class-scope"></a>具有类范围的名称中的链接
下列链接规则将应用于具有类范围的名称：  
  
-   静态类成员具有外部链接。  
  
-   类成员函数具有外部链接。  
  
-   枚举器和 `typedef` 名称没有链接。  
  
 **Microsoft 专用**  
  
-   声明为 `friend` 的函数必须具有外部链接。 将静态函数声明为 `friend` 将生成错误。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [程序和链接](../cpp/program-and-linkage-cpp.md)