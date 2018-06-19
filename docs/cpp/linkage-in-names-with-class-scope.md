---
title: 具有类范围的名称中的链接 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9eb58f87e998fbe1eeeb9b26eb0da75046a9079d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418967"
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