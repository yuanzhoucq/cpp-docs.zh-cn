---
title: "bad_function_call 类| Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- functional/std::bad_function_call
dev_langs:
- C++
helpviewer_keywords:
- bad_function_call class
ms.assetid: b70a0268-43ff-4f3b-a283-faf1cb172d4c
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: c6aa47c6eb3d9fc39eed6b68856641cd86d27ba5
ms.contentlocale: zh-cn
ms.lasthandoff: 10/03/2017

---
# <a name="badfunctioncall-class"></a>bad_function_call 类
报告错误的函数调用。  
  
## <a name="syntax"></a>语法  
  
```  
class bad_function_call  
 : public std::exception {  
 };  
```  
  
## <a name="remarks"></a>备注  
 该类描述引发的异常以指示在 [function 类](../standard-library/function-class.md)上调用 `operator()`

