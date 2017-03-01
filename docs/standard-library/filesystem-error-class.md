---
title: "filesystem_error 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- filesystem/std::experimental::filesystem::filesystem_error
dev_langs:
- C++
ms.assetid: c53aac27-c1fa-43e4-8967-48ea8ba1f172
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
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 79a5556d0d0806462893bb4165f7d6fc2d3a986f
ms.lasthandoff: 02/24/2017

---
# <a name="filesystemerror-class"></a>filesystem_error 类
所引发以报告低级系统溢出的全部异常的基类。  
  
## <a name="syntax"></a>语法  
  
```  
class filesystem_error    : public system_error;  
```  
  
## <a name="remarks"></a>备注  
 此类用作引发报告 \<filesystem> 函数中错误的所有异常的基类。 它存储类型为 string 的对象，出于阐释目的将其称为 mymesg。 它还存储两个 path 类型的对象，称为 mypval1 和 mypval2。  
  
## <a name="filesystemerrorfilesystemerror"></a>filesystem_error::filesystem_error  
  
```  
filesystem_error(const string& what_arg,
    error_code ec);

filesystem_error(const string& what_arg,  
    const path& pval1,
    error_code ec);

filesystem_error(const string& what_arg,  
    const path& pval1,
    const path& pval2,
    error_code ec);
```  
  
 第一个构造函数从 what_arg 和 ec 构造其消息。 第二个构造函数从 pval1（存储在 mypval1 中）构造其消息。 第三个构造函数从 pval1（存储在 mypval1）和 pval2（存储在 mypval2 中）构造其消息。  
  
## <a name="filesystemerrorpath1"></a>filesystem_error::path1  
  
```  
const path& path1() const noexcept;  
```  
  
 此成员函数返回 mypval1  
  
## <a name="filesystemerrorpath2"></a>filesystem_error::path2  
  
```  
const path& path2() const noexcept;  
```  
  
 此成员函数返回 mypval2  
  
## <a name="filesystemerrorwhat"></a>filesystem_error::what  
  
```  
const char *what() const noexcept;  
```  
  
 此成员函数返回指向 NTBS 的指针，最好是由 runtime_error::what()、system_error::what()、mymesg、mypval1.native_string() 和 mypval2.native_string() 组成。  
  
## <a name="requirements"></a>要求  
 **标头：** filesystem  
  
 **命名空间：**std::experimental::filesystem  
  
## <a name="see-also"></a>另请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [system_error 类](../standard-library/system-error-class.md)   
 [\<filesystem>](../standard-library/filesystem.md)   
 [\<exception>](../standard-library/exception.md)


