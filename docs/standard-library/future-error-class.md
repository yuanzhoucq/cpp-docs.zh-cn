---
title: "future_error 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- future/std::future_error
dev_langs:
- C++
ms.assetid: 6071c545-ac2a-49ef-9967-07b0125da861
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: 07d01d2efc3aadf1d8b5a585b7f4c7b8b76d87cc
ms.contentlocale: zh-cn
ms.lasthandoff: 04/19/2017

---
# <a name="futureerror-class"></a>future_error 类
描述可由管理 [future](../standard-library/future-class.md) 对象的类型方法引发的异常对象。  
  
## <a name="syntax"></a>语法  
  
```
class future_error : public logic_error {
public:
    future_error(error_code code);

const error_code& code() const throw();

const char *what() const throw();

};
```  
  
## <a name="requirements"></a>要求  
 **标头︰** \<将来 >  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [logic_error 类](../standard-library/logic-error-class.md)   
 [error_code 类](../standard-library/error-code-class.md)

