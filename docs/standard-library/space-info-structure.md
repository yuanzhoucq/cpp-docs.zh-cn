---
title: "space_info 结构 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- filesystem/std::tr2::sys::space_info
dev_langs:
- C++
ms.assetid: f2b35b42-06ff-45bd-8617-39a0f5358a54
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: e8573fab6f0d1a1ad43a9be2e3be1ddd8f556748
ms.contentlocale: zh-cn
ms.lasthandoff: 04/19/2017

---
# <a name="spaceinfo-structure"></a>space_info 结构
保存有关卷的信息。  
  
## <a name="syntax"></a>语法  
  
```  
struct space_info    {
    uintmax_t capacity;
    uintmax_t free;
    uintmax_t available;
    };  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|`unsigned long long available`|表示可用于表示卷上数据的字节数。|  
|`unsigned long long capacity`|表示卷可以表示的字节总数。|  
|`unsigned long long free`|表示不用于表示卷上数据的字节数。|  
  
## <a name="requirements"></a>要求  
 **标头︰** \<文件系统 >  
  
 **命名空间：**std::experimental::filesystem  
  
## <a name="see-also"></a>另请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<filesystem>](../standard-library/filesystem.md)   
 [空间](http://msdn.microsoft.com/en-us/7fce0b0e-523b-4598-b218-47245d0204ca)   
 [文件系统导航 (C++)](../standard-library/file-system-navigation.md)


