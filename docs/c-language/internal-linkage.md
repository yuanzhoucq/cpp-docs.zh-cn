---
title: "内部链接 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- internal linkage
- linkage [C++], internal
ms.assetid: 80be7b51-c930-43db-94d6-4f09a64077bf
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e6ca8a9e9804aa6c14077b023d0014062067f324
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="internal-linkage"></a>内部链接
如果对象或函数的文件范围标识符声明包含 storage-class-specifier static，则该标识符具有内部链接。 否则，该标识符具有外部链接。 有关 storage-class-specifier 非终止符的讨论，请参阅[存储类](../c-language/c-storage-classes.md)。  
  
 在一个翻译单元内，带内部链接的标识符的每个实例均表示相同的标识符或函数。 内部链接的标识符对于翻译单元是唯一的。  
  
## <a name="see-also"></a>请参阅  
 [使用 extern 指定链接](../cpp/using-extern-to-specify-linkage.md)