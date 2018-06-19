---
title: 具有块范围的名称中的链接 |Microsoft 文档
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
- block scope [C++]
- external linkage, scope linkage rules
ms.assetid: 73efa91a-f761-47f7-bbd9-9f9e3508e218
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ab7758e962c028c4746836e470ee43eaab510f9e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418882"
---
# <a name="linkage-in-names-with-block-scope"></a>具有块范围的名称中的链接
下列链接规则适用于具有块范围的名称（本地名称）：  
  
-   名称声明为`extern`具有外部链接，除非它们以前声明为**静态**。  
  
-   没有块范围的所有其他名称都没有链接。  
  
## <a name="see-also"></a>请参阅  
 [程序和链接](../cpp/program-and-linkage-cpp.md)