---
title: "time_base 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- locale/std::time_base
dev_langs:
- C++
helpviewer_keywords:
- time_base class
ms.assetid: 9ae37f0b-9a42-496e-9870-3d9b71bab8fb
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: c1c7c6c708087827c853234dcbd4519c79fba2bf
ms.contentlocale: zh-cn
ms.lasthandoff: 10/03/2017

---
# <a name="timebase-class"></a>time_base 类
一种充当模板类 time_get 的 facet 基类的类，用于仅定义枚举的类型 **dateorder** 以及此类型的几个常量。  
  
## <a name="syntax"></a>语法  
  
```
class time_base : public locale::facet {
public:
    enum dateorder {no_order,
    dmy,
 mdy,
    ymd,
 ydm};
    time_base(
 size_t _Refs = 0)
 ~time_base();

};
```  
  
## <a name="remarks"></a>备注  
 每个常量以不同的方式对日期组件进行排序。 这些常量包括：  
  
- **no_order**：指示没有特定顺序。  
  
- **dmy**：指示顺序为日月年，例如，2 日，12 月，1979 年。  
  
- **dmy**：指示顺序为月日年，例如，12 月2 号，1979 年。  
  
- **ymd**：指示顺序为年月日，例如 1979/12/2。  
  
- **ydm**：指示顺序为年日月，例如，1979 年，2 日，12 月。  
  
## <a name="requirements"></a>要求  
 **标头：**\<locale>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)




