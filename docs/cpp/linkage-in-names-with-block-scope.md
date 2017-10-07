---
title: "具有块范围的名称中的链接 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- scope [C++], linkage rules
- linkage [C++], scope linkage rules
- names [C++], scope linkage rules
- block scope [C++]
- external linkage, scope linkage rules
ms.assetid: 73efa91a-f761-47f7-bbd9-9f9e3508e218
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: de093c90e0da4a906d8aefebfb7048733c1a1f1d
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="linkage-in-names-with-block-scope"></a>具有块范围的名称中的链接
下列链接规则适用于具有块范围的名称（本地名称）：  
  
-   名称声明为`extern`具有外部链接，除非它们以前声明为**静态**。  
  
-   没有块范围的所有其他名称都没有链接。  
  
## <a name="see-also"></a>另请参阅  
 [程序和链接](../cpp/program-and-linkage-cpp.md)
