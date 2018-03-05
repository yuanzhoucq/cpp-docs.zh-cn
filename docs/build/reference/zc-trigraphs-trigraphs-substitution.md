---
title: "-Zc: trigraphs （Trigraphs 替换） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /Zc
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Conformance compiler options
- Zc compiler options (C++)
ms.assetid: e3d6058f-400d-4966-a3aa-800cfdf69cbf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 739e772c87c937a552e07a32fa5bb80b1a1e2508
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="zctrigraphs-trigraphs-substitution"></a>/Zc:trigraphs（Trigraphs 替换）
当**/zc: trigraphs**指定，编译器将通过使用相应的标点字符来替换三元组字符序列。 若要关闭三元组替换，请指定**/Zc:trigraphs-**。 默认情况下， **/zc: trigraphs**处于关闭状态。  
  
## <a name="syntax"></a>语法  
  
```  
/Zc:trigraphs[-]  
```  
  
## <a name="remarks"></a>备注  
 三元祖由两个连续的问号（“??”）后跟一个唯一的第三个字符组成。 例如，编译器会将"??="使用 '#' 字符三元组。 可以在使用字符集的 C 源文件中使用三元祖，该字符集不包含一些标点字符的方便图形表示。  
  
 C/c + + 三字符组和的示例，演示如何使用三字符组的列表，请参阅[三元组](../../c-language/trigraphs.md)。  
  
## <a name="see-also"></a>请参阅  
 [/Zc （一致性）](../../build/reference/zc-conformance.md)   
 [三字符组](../../c-language/trigraphs.md)