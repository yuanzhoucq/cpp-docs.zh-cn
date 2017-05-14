---
title: "directory_entry 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- filesystem/std::experimental::filesystem::directory_entry
- FILESYSTEM/std::experimental::filesystem::directory_entry::operator const std::experimental::filesystem::path &
- FILESYSTEM/std::experimental::filesystem::directory_entry::directory_entry
- FILESYSTEM/std::experimental::filesystem::directory_entry::operator=
- FILESYSTEM/std::experimental::filesystem::directory_entry::assign
- FILESYSTEM/std::experimental::filesystem::directory_entry::replace_filename
- FILESYSTEM/std::experimental::filesystem::directory_entry::path
- FILESYSTEM/std::experimental::filesystem::directory_entry::status
- FILESYSTEM/std::experimental::filesystem::directory_entry::symlink_status
- FILESYSTEM/std::experimental::filesystem::directory_entry::operator<
- FILESYSTEM/std::experimental::filesystem::directory_entry::operator==
- FILESYSTEM/std::experimental::filesystem::directory_entry::operator!=
- FILESYSTEM/std::experimental::filesystem::directory_entry::operator<=
- FILESYSTEM/std::experimental::filesystem::directory_entry::operator>
- FILESYSTEM/std::experimental::filesystem::directory_entry::operator>=
dev_langs:
- C++
ms.assetid: 1827c67b-4137-4548-adb0-f955f7acaf08
caps.latest.revision: 17
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
ms.openlocfilehash: 0bd6b73c99eccffc7661cc4b43f97ab46890c5ee
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

---
# <a name="directoryentry-class"></a>directory_entry 类
描述由 `*X` 返回的对象，其中 *X* 是 [directory_iterator](../standard-library/directory-iterator-class.md) 或 [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md)。  
  
## <a name="syntax"></a>语法  
  
```  
class directory_entry;  
```  
  
## <a name="remarks"></a>备注  
 该类存储 [path](../standard-library/path-class.md) 类型的对象。 存储的 `path` 可以是 [path 类](../standard-library/path-class.md)的实例或从 `path` 派生的类型的实例。 它还存储两个 [file_type](../standard-library/filesystem-enumerations.md#file_type) 值；一个表示有关存储文件名的状态的已知信息，另一个表示有关文件名的符号链接状态的已知信息。  
  
 有关详细信息和代码示例，请参阅[文件系统导航 (C++)](../standard-library/file-system-navigation.md)。  
  
## <a name="assign"></a>assign  
  
```  
void assign(const std::experimental::filesystem::path& pval,  
    file_status stat_arg = file_status(),  
    file_status symstat_arg = file_status());
```  
  
 成员函数将 pval 分配到 mypath，stat 分配到 mystat，并将 symstat 分配到 mysymstat。  
  
## <a name="directoryentry"></a>directory_entry  
  
```  
directory_entry() = default;  
directory_entry(const directory_entry&) = default;  
directory_entry(directory_entry&&) noexcept = default;  
explicit directory_entry(const std::experimental::filesystem::path& pval,  
    file_status stat_arg = file_status(),  
    file_status symstat_arg = file_status());
```  
  
 默认构造函数行为符合预期。 第四个构造函数将 mypath 初始化到 pval，mystat 初始化到 stat_arg，并将 mysymstat 初始化到 symstat_arg。  
  
## <a name="operator"></a>operator!=  
  
```  
bool operator!=(const directory_entry& right) const noexcept;  
```  
  
 此成员函数返回 !(*this == right)。  
  
## <a name="operator"></a>operator=  
  
```  
directory_entry& operator=(const directory_entry&) = default;  
directory_entry& operator=(directory_entry&&) noexcept = default;  
```  
  
 默认成员赋值运算符的行为符合预期。  
  
## <a name="operator"></a>operator==  
  
```  
bool operator==(const directory_entry& right) const noexcept;  
```  
  
 此成员函数返回 mypath == right.mypath。  
  
## <a name="operator"></a>operator<  
  
```  
 
bool operator<(const directory_entry& right) const noexcept;  
```  
  
 此成员函数返回 mypath < right.mypath。  
  
## <a name="operator"></a>operator<=  
  
```  
bool operator<=(const directory_entry& right) const noexcept;  
```  
  
 此成员函数返回 !(right \< *this)。  
  
## <a name="operator"></a>operator>  
  
```  
bool operator>(const directory_entry& right) const noexcept;  
```  
  
 此成员函数返回 right \< *this。  
  
## <a name="operator"></a>operator>=  
  
```  
bool operator>=(const directory_entry& right) const noexcept;  
```  
  
 此成员函数返回 !(*this < right)。  
  
## <a name="operator-const-pathtype"></a>operator const path_type&  
  
``` 
 operator const std::experimental::filesystem::path&() const; 
```  
  
 该成员运算符将返回 mypath。  
  
## <a name="path"></a>path  
  
```  
const std::experimental::filesystem::path& path() const noexcept;  
```  
  
 此成员函数返回 mypath。  
  
## <a name="replacefilename"></a>replace_filename  
  
```  
void replace_filename(
    const std::experimental::filesystem::path& pval,  
    file_status stat_arg = file_status(),  
    file_status symstat_arg = file_status());
```  
  
 此成员函数将 mypath 替换为 mypath.parent_path() / pval，mystat 替换为 stat_arg，并将 mysymstat 替换为 ymstat_arg  
  
## <a name="status"></a>status  
  
```  
file_status status() const; 
file_status status(error_code& ec) const noexcept;  
```  
  
 这两个成员函数均返回第一次可能按如下更改的 mystat：  
  
1.  如果为 status_known(mystat)，则不执行任何操作。  
  
2.  如果为 !status_known(mysymstat) && !is_symlink(mysymstat)，则 mystat = mysymstat。  
  
## <a name="symlinkstatus"></a>symlink_status  
  
```  
file_status symlink_status() const; 
file_status symlink_status(error_code& ec) const noexcept;  
```  
  
 这两个成员函数均返回第一次可能按如下更改的 mysymstat：如果为 status_known(mysymstat)，则不执行任何操作。 否则为 mysymstat = symlink_status(mypval)。  
  
## <a name="requirements"></a>要求  
 **标头：**\<experimental/filesystem>  
  
 **命名空间：**std::experimental::filesystem  
  
## <a name="see-also"></a>另请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<filesystem>](../standard-library/filesystem.md)


