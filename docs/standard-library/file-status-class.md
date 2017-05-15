---
title: "file_status 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- file_status
- filesystem/std::experimental::filesystem::v1::file_status
- filesystem/std::experimental::filesystem::v1::file_status::operator=
- filesystem/std::experimental::filesystem::v1::file_status::type
- filesystem/std::experimental::filesystem::v1::file_status::permissions
dev_langs:
- C++
ms.assetid: 9781840e-ad22-44dd-ad79-0fabaa94bac4
caps.latest.revision: 15
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
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 1095fbeeceb33fd9dedf0ad1217eab1a052f5ba1
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

---
# <a name="filestatus-class"></a>file_status 类
包装 [file_type](../standard-library/filesystem-enumerations.md#file_type) 和文件 [perms](../standard-library/filesystem-enumerations.md#perms)。  
  
## <a name="syntax"></a>语法  
  
```cpp  
class file_status;  
```  
  
## <a name="filestatusfilestatus"></a>file_status::file_status  
  
```cpp  
explicit file_status(  
   file_type ftype = file_type::none,  
   perms mask = perms::unknown) noexcept;  
  
file_status(const file_status&) noexcept = default;  
  
file_status(file_status&&) noexcept = default; 

~file_status() noexcept = default; 
```  
  
## <a name="filestatusoperator"></a>file_status::operator=  
  
```cpp  
file_status& operator=(const file_status&) noexcept = default;  
file_status& operator=(file_status&&) nexcept = default;  
```  
  
 默认成员赋值运算符的行为符合预期。  
  
## <a name="type"></a>类型  
  
```cpp  
file_type type() const noexcept  
void type(file_type ftype) noexcept  
```  
  
 获取或设置 file_type。  
  
## <a name="permissions"></a>权限  
  
```cpp  
perms permissions() const noexcept  
void permissions(perms mask) noexcept   
```  
  
 获取或设置文件权限。  
  
 使用资源库将文件设置为只读，或删除只读特性。  
  
## <a name="requirements"></a>要求  
 **标头︰** \<文件系统 >  
  
 **Namespace:** std::experimental::filesystem、 std::experimental::filesystem::v1  
  
## <a name="see-also"></a>另请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [path 类](../standard-library/path-class.md)   
 [\<filesystem>](../standard-library/filesystem.md)


