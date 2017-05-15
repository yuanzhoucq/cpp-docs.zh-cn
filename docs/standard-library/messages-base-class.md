---
title: "messages_base 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- messages_base
- locale/std::messages_base
dev_langs:
- C++
helpviewer_keywords:
- messages_base class
ms.assetid: 9aad38c6-4c13-445d-b096-364bd0836efb
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 4e10582050f922e880577dc5a19d99a1ac03128e
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

---
# <a name="messagesbase-class"></a>messages_base 类
该基类描述消息目录的 `int` 类型。  
  
## <a name="syntax"></a>语法  
  
```
struct messages_base : locale::facet {
    typedef int catalog;
    explicit messages_base(size_t _Refs = 0)
};
```  
  
## <a name="remarks"></a>备注  
 该类型目录是类型 `int` 的同义词，用于描述 messages:: [do_open](../standard-library/messages-class.md#do_open) 中可能的返回值。  
  
## <a name="requirements"></a>要求  
 **标头：**\<locale>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)




