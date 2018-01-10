---
title: "当前时间： 常规用途类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- time, setting current
- current time, CTime object
- procedures, getting current time
- initializing objects, with the current time
- time, getting current
ms.assetid: c39e6775-6a92-4b27-95a7-5c86ed371d8a
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a6c43ffd60d837bdd8f061057cf1c36340b6e6af
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="current-time-general-purpose-classes"></a>当前时间： 常规用途类
下面的过程演示如何创建`CTime`对象并将其初始化与当前时间。  
  
#### <a name="to-get-the-current-time"></a>若要获取当前时间  
  
1.  分配`CTime`对象，，如下所示：  
  
     [!code-cpp[NVC_ATLMFC_Utilities#171](../atl-mfc-shared/codesnippet/cpp/current-time-general-purpose-classes_1.cpp)]  
  
    > [!NOTE]
    >  未初始化`CTime`对象初始化为有效的时间。  
  
2.  调用`CTime::GetCurrentTime`函数可从操作系统获取当前时间。 此函数将返回`CTime`可以用于设置的值的对象`CTime`、，如下所示：  
  
     [!code-cpp[NVC_ATLMFC_Utilities#172](../atl-mfc-shared/codesnippet/cpp/current-time-general-purpose-classes_2.cpp)]  
  
     由于`GetCurrentTime`是从静态成员函数`CTime`类，你必须使用限定其名称与类和范围解析运算符的名称 (`::`)， `CTime::GetCurrentTime()`。  
  
 当然，所述的两个步骤以前可以合并成单个程序语句，如下所示：  
  
 [!code-cpp[NVC_ATLMFC_Utilities#173](../atl-mfc-shared/codesnippet/cpp/current-time-general-purpose-classes_3.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [日期和时间：通用类](../atl-mfc-shared/date-and-time-general-purpose-classes.md)



