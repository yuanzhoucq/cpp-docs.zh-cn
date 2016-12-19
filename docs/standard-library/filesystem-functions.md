---
title: "&lt;filesystem&gt; 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FILESYSTEM/std::experimental::filesystem::v1::absolute"
  - "std::experimental::filesystem::v1::absolute"
  - "FILESYSTEM/std::experimental::filesystem::v1::canonical"
  - "std::experimental::filesystem::v1::canonical"
  - "FILESYSTEM/std::experimental::filesystem::v1::copy"
  - "std::experimental::filesystem::v1::copy"
  - "FILESYSTEM/std::experimental::filesystem::v1::copy_file"
  - "std::experimental::filesystem::v1::copy_file"
  - "FILESYSTEM/std::experimental::filesystem::v1::copy_symlink"
  - "std::experimental::filesystem::v1::copy_symlink"
  - "FILESYSTEM/std::experimental::filesystem::v1::create_directories"
  - "std::experimental::filesystem::v1::create_directories"
  - "FILESYSTEM/std::experimental::filesystem::v1::create_directory"
  - "std::experimental::filesystem::v1::create_directory"
  - "FILESYSTEM/std::experimental::filesystem::v1::create_directory_symlink"
  - "std::experimental::filesystem::v1::create_directory_symlink"
  - "FILESYSTEM/std::experimental::filesystem::v1::create_hard_link"
  - "std::experimental::filesystem::v1::create_hard_link"
  - "FILESYSTEM/std::experimental::filesystem::v1::create_symlink"
  - "std::experimental::filesystem::v1::create_symlink"
  - "FILESYSTEM/std::experimental::filesystem::v1::current_path"
  - "std::experimental::filesystem::v1::current_path"
  - "FILESYSTEM/std::experimental::filesystem::v1::equivalent"
  - "std::experimental::filesystem::v1::equivalent"
  - "FILESYSTEM/std::experimental::filesystem::v1::exists"
  - "std::experimental::filesystem::v1::exists"
  - "FILESYSTEM/std::experimental::filesystem::v1::file_size"
  - "std::experimental::filesystem::v1::file_size"
  - "FILESYSTEM/std::experimental::filesystem::v1::hard_link_count"
  - "std::experimental::filesystem::v1::hard_link_count"
  - "FILESYSTEM/std::experimental::filesystem::v1::hash_value"
  - "std::experimental::filesystem::v1::hash_value"
  - "FILESYSTEM/std::experimental::filesystem::v1::is_block_file"
  - "std::experimental::filesystem::v1::is_block_file"
  - "FILESYSTEM/std::experimental::filesystem::v1::is_character_file"
  - "std::experimental::filesystem::v1::is_character_file"
  - "FILESYSTEM/std::experimental::filesystem::v1::is_directory"
  - "std::experimental::filesystem::v1::is_directory"
  - "FILESYSTEM/std::experimental::filesystem::v1::is_empty"
  - "std::experimental::filesystem::v1::is_empty"
  - "FILESYSTEM/std::experimental::filesystem::v1::is_fifo"
  - "std::experimental::filesystem::v1::is_fifo"
  - "FILESYSTEM/std::experimental::filesystem::v1::is_other"
  - "std::experimental::filesystem::v1::is_other"
  - "FILESYSTEM/std::experimental::filesystem::v1::is_regular_file"
  - "std::experimental::filesystem::v1::is_regular_file"
  - "FILESYSTEM/std::experimental::filesystem::v1::is_socket"
  - "std::experimental::filesystem::v1::is_socket"
  - "FILESYSTEM/std::experimental::filesystem::v1::is_symlink"
  - "std::experimental::filesystem::v1::is_symlink"
  - "FILESYSTEM/std::experimental::filesystem::v1::last_write_time"
  - "std::experimental::filesystem::v1::last_write_time"
  - "FILESYSTEM/std::experimental::filesystem::v1::permissions"
  - "std::experimental::filesystem::v1::permissions"
  - "FILESYSTEM/std::experimental::filesystem::v1::read_symlink"
  - "std::experimental::filesystem::v1::read_symlink"
  - "FILESYSTEM/std::experimental::filesystem::v1::remove"
  - "std::experimental::filesystem::v1::remove"
  - "FILESYSTEM/std::experimental::filesystem::v1::remove_all"
  - "std::experimental::filesystem::v1::remove_all"
  - "FILESYSTEM/std::experimental::filesystem::v1::rename"
  - "std::experimental::filesystem::v1::rename"
  - "FILESYSTEM/std::experimental::filesystem::v1::resize_file"
  - "std::experimental::filesystem::v1::resize_file"
  - "FILESYSTEM/std::experimental::filesystem::v1::space"
  - "std::experimental::filesystem::v1::space"
  - "FILESYSTEM/std::experimental::filesystem::v1::status"
  - "std::experimental::filesystem::v1::status"
  - "FILESYSTEM/std::experimental::filesystem::v1::status_known"
  - "std::experimental::filesystem::v1::status_known"
  - "FILESYSTEM/std::experimental::filesystem::v1::swap"
  - "std::experimental::filesystem::v1::swap"
  - "FILESYSTEM/std::experimental::filesystem::v1::symlink_status"
  - "std::experimental::filesystem::v1::symlink_status"
  - "FILESYSTEM/std::experimental::filesystem::v1::system_complete"
  - "std::experimental::filesystem::v1::system_complete"
  - "FILESYSTEM/std::experimental::filesystem::v1::temp_directory_path"
  - "std::experimental::filesystem::v1::temp_directory_path"
  - "FILESYSTEM/std::experimental::filesystem::v1::u8path"
  - "std::experimental::filesystem::v1::u8path"
dev_langs: 
  - "C++"
ms.assetid: be3cb821-4728-4d47-ab78-858fa8aa5045
caps.latest.revision: 13
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;filesystem&gt; 函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[\<filesystem\>](../standard-library/filesystem.md) 标头中的这些 free 函数对路径、文件、符号链接、目录和卷执行修改和查询操作。 有关详细信息和代码示例，请参阅 [文件系统导航 \(C\+\+\)](../standard-library/file-system-navigation.md)。  
  
## 绝对  
  
```  
path absolute(const path& pval, const path& base = current_path());  
  
```  
  
 该函数返回与 pval 对应的绝对路径名（相对于路径名基）：  
  
1.  如果 pval.has\_root\_name\(\) && pval.has\_root\_directory\(\)，则该函数返回 pval。  
  
2.  如果 pval.has\_root\_name\(\) && \!pval.has\_root\_directory\(\)，则该函数返回 pval.root\_name\(\) \/ absolute\(base\).root\_directory\(\) \/ absolute\(base\).relative\_path\(\) \/ pval.relative\_path\(\)。  
  
3.  如果 \!pval.has\_root\_name\(\) && pval.has\_root\_directory\(\)，则该函数返回 absolute\(base\).root\_name\(\) \/ pval。  
  
4.  如果 \!pval.has\_root\_name\(\) && \!pval.has\_root\_directory\(\)，则该函数返回 absolute\(base\) \/ pval。  
  
5.  
  
## begin  
  
```  
const directory_iterator& begin(const directory_iterator& iter) noexcept;  
const recursive_directory_iterator&  
    begin(const recursive_directory_iterator& iter) noexcept;  
  
```  
  
 两个函数均返回 iter。  
  
## 规范  
  
```  
path canonical(const path& pval, const path& base = current_path());  
path canonical(const path& pval,  
    error_code& ec);  
path canonical(const path& pval, const path& base,  
    error_code& ec);  
```  
  
 这些函数均形成绝对路径名 pabs \= absolute\(pval, base\)（或 pab \= 不使用任何基本参数的重载的 absolute\(pval\)），然后按顺序执行以下步骤，将其简化为规范格式：  
  
1.  is\_symlink\(X\) 为 true 的每个路径组件 X 都替换为 read\_symlink\(X\)。  
  
2.  删除每个路径组件 . （圆点是由以前的路径组件建立的当前目录）。  
  
3.  删除每对路径组件 X\/.. （双园点是由以前的路径组件建立的父目录）。  
  
 然后，该函数返回 pabs。  
  
## copy  
  
```  
void copy(const path& from, const path& to);  
void copy(const path& from, const path& to,  
    error_code& ec) noexcept;  
void copy(const path& from, const path& to, copy_options opts);  
void copy(const path& from, const path& to, copy_options opts,  
    error_code& ec) noexcept;  
```  
  
 这些函数都可能在 opts 参数的控制下将 from 处的一个或多个文件复制或链接到 to，对于没有 opts 参数的重载，该参数被视为 copy\_options::none。 opts 应最多包含一个以下项：  
  
-   skip\_existing、overwrite\_existing 或 update\_existing  
  
-   copy\_symlinks 或 skip\_symlinks  
  
-   directories\_only、create\_symlinks 或 create\_hard\_links  
  
 函数首先确定 file\_status 值 f（表示 from）和 t（表示 to）：  
  
-   如果 opts & \(copy\_options::create\_symlinks &#124; copy\_options::skip\_symlinks\)，则通过调用 symlink\_status  
  
-   否则，通过调用状态  
  
-   否则报告错误。  
  
 如果 \!exists\(f\) &#124;&#124; equivalent\(f, t\) &#124;&#124; is\_other\(f\) &#124;&#124; is\_other\(t\) &#124;&#124; is\_directory\(f\)&& is\_regular\_file\(t\)，则这些函数随后报告错误（不执行任何其他操作）。  
  
 否则，如果 is\_symlink\(f\)，则：  
  
-   如果 options & copy\_options::skip\_symlinks，则不执行任何操作。  
  
-   否则，如果 \!exists\(t\)&& options & copy\_options::copy\_symlinks ，则 copy\_symlink\(from, to, opts\)。  
  
-   否则报告错误。  
  
 否则，如果 is\_regular\_file\(f\)，则：  
  
-   如果 opts & copy\_options::directories\_only，则不执行任何操作。  
  
-   否则，如果 opts & copy\_options::create\_symlinks，则 create\_symlink\(to, from\)。  
  
-   否则，如果 opts & copy\_options::create\_hard\_links，则 create\_hard\_link\(to, from\)。  
  
-   否则，如果 is\_directory\(f\)，则 copy\_file\(from, to \/ from.filename\(\), opts\)。  
  
-   否则，copy\_file\(from, to, opts\)。  
  
 否则，如果 is\_directory\(f\) && \(opts & copy\_options::recursive &#124;&#124; \!opts\)，则：  
  
-   ```  
    if (!exists(t))  
        {  // copy directory contents recursively  
        create_directory(to, from, ec);  
        for (directory_iterator next(from), end;  
            ec == error_code() && next != end; ++next)  
            copy(next->path(),  
                to / next->path().filename(), opts, ec);  
        }  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>bool copy_file(const path& from, const path& to);  
bool copy_file(const path& from, const path& to,  
    error_code& ec) noexcept;  
bool copy_file(const path& from, const path& to, copy_options opts);  
bool copy_file(const path& from, const path& to, copy_options opts,  
    error_code& ec) noexcept;  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>void copy_symlink(const path& from, const path& to);  
void copy_symlink(const path& from, const path& to,  
    error_code& ec) noexcept;  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>bool create_directories(const path& pval);  
bool create_directories(const path& pval,  
    error_code& ec) noexcept;  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>bool create_directory(const path& pval);  
bool create_directory(const path& pval,  
    error_code& ec) noexcept;  
bool create_directory(const path& pval, const path& attr);  
bool create_directory(const path& pval, const path& attr,  
    error_code& ec) noexcept;  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>void create_directory_symlink(const path& to, const path& link);  
void create_directory_symlink(const path& to, const path& link),  
    error_code& ec) noexcept;  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>void create_hard_link(const path& to, const path& link);  
void create_hard_link(const path& to, const path& link),  
    error_code& ec) noexcept;  
<CodeContentPlaceHolder>10</CodeContentPlaceHolder>void create_symlink(const path& to, const path& link);  
void create_symlink(const path& to, const path& link),  
    error_code& ec) noexcept;  
<CodeContentPlaceHolder>11</CodeContentPlaceHolder>path current_path();  
path current_path(  
    error_code& ec);  
void current_path(const path& pval);  
void current_path(const path& pval,  
    error_code& ec) noexcept;  
<CodeContentPlaceHolder>12</CodeContentPlaceHolder>directory_iterator& end(const directory_iterator& iter) noexcept;  
recursive_directory_iterator&  
    end(const recursive_directory_iterator& iter) noexcept;  
<CodeContentPlaceHolder>13</CodeContentPlaceHolder>bool equivalent(const path& left, const path& right);  
bool equivalent(const path& left, const path& right,  
    error_code& ec) noexcept;  
<CodeContentPlaceHolder>14</CodeContentPlaceHolder>bool exists(file_status stat) noexcept;  
bool exists(const path& pval);  
bool exists(const path& pval,  
    error_code& ec) noexcept;  
<CodeContentPlaceHolder>15</CodeContentPlaceHolder>uintmax_t file_size(const path& pval);  
uintmax_t file_size(const path& pval,  
    error_code& ec) noexcept;  
<CodeContentPlaceHolder>16</CodeContentPlaceHolder>uintmax_t hard_link_count(const path& pval);  
uintmax_t hard_link_count(const path& pval,  
    error_code& ec) noexcept;  
<CodeContentPlaceHolder>17</CodeContentPlaceHolder>size_t hash_value(const path& pval) noexcept;  
<CodeContentPlaceHolder>18</CodeContentPlaceHolder>bool is_block_file(file_status stat) noexcept;  
bool is_block_file(const path& pval);  
bool is_block_file(const path& pval,  
    error_code& ec) noexcept;  
  
<CodeContentPlaceHolder>19</CodeContentPlaceHolder>  
bool is_character_file(file_status stat) noexcept;  
bool is_character_file(const path& pval);  
bool is_character_file(const path& pval,  
    error_code& ec) noexcept;  
  
<CodeContentPlaceHolder>20</CodeContentPlaceHolder>  
bool is_directory(file_status stat) noexcept;  
bool is_directory(const path& pval);  
bool is_directory(const path& pval,  
    error_code& ec) noexcept;  
  
<CodeContentPlaceHolder>21</CodeContentPlaceHolder>  
bool is_empty(file_status stat) noexcept;  
bool is_empty(const path& pval);  
bool is_empty(const path& pval,  
    error_code& ec) noexcept;  
  
<CodeContentPlaceHolder>22</CodeContentPlaceHolder>bool is_fifo(file_status stat) noexcept;  
bool is_fifo(const path& pval);  
bool is_fifo(const path& pval,  
    error_code& ec) noexcept;  
  
<CodeContentPlaceHolder>23</CodeContentPlaceHolder>bool is_other(file_status stat) noexcept;  
bool is_other(const path& pval);  
bool is_other(const path& pval,  
    error_code& ec) noexcept;  
  
<CodeContentPlaceHolder>24</CodeContentPlaceHolder>  
bool is_regular_file(file_status stat) noexcept;  
bool is_regular_file(const path& pval);  
bool is_regular_file(const path& pval,  
    error_code& ec) noexcept;  
  
<CodeContentPlaceHolder>25</CodeContentPlaceHolder>  
bool is_socket(file_status stat) noexcept;  
bool is_socket(const path& pval);  
bool is_socket(const path& pval,  
    error_code& ec) noexcept;  
  
<CodeContentPlaceHolder>26</CodeContentPlaceHolder>  
bool is_symlink(file_status stat) noexcept;  
bool is_symlink(const path& pval);  
bool is_symlink(const path& pval,  
    error_code& ec) noexcept;  
  
<CodeContentPlaceHolder>27</CodeContentPlaceHolder>  
file_time_type last_write_time(const path& pval);  
file_time_type last_write_time(const path& pval,  
    error_code& ec) noexcept;  
void last_write_time(const path& pval, file_time_type new_time);  
void last_write_time(const path& pval, file_time_type new_time,  
    error_code& ec) noexcept;  
  
<CodeContentPlaceHolder>28</CodeContentPlaceHolder>void permissions(const path& pval, perms mask);  
void permissions(const path& pval, perms mask,  
    error_code& ec) noexcept;  
  
<CodeContentPlaceHolder>29</CodeContentPlaceHolder>path read_symlink(const path& pval);  
path read_symlink(const path& pval.  
    error_code& ec);  
<CodeContentPlaceHolder>30</CodeContentPlaceHolder>bool remove(const path& pval);  
bool remove(const path& pval,  
    error_code& ec) noexcept;  
<CodeContentPlaceHolder>31</CodeContentPlaceHolder>uintmax_t remove_all(const path& pval);  
uintmax_t remove_all(const path& pval,  
    error_code& ec) noexcept;  
  
<CodeContentPlaceHolder>32</CodeContentPlaceHolder>void rename(const path& from, const path& to);  
void rename(const path& from, const path& to,  
    error_code& ec) noexcept;  
<CodeContentPlaceHolder>33</CodeContentPlaceHolder>void resize(const path& pval, uintmax_t size);  
void resize(const path& pval, uintmax_t size,  
    error_code& ec) noexcept;  
<CodeContentPlaceHolder>34</CodeContentPlaceHolder>space_info space(const path& pval);  
space_info space(const path& pval,  
    error_code& ec) noexcept;  
<CodeContentPlaceHolder>35</CodeContentPlaceHolder>file_status status(const path& pval);  
file_status status(const path& pval,  
    error_code& ec) noexcept;  
  
<CodeContentPlaceHolder>36</CodeContentPlaceHolder>bool status_known(file_status stat) noexcept;  
<CodeContentPlaceHolder>37</CodeContentPlaceHolder>void swap(path& left, path& right) noexcept;  
  
<CodeContentPlaceHolder>38</CodeContentPlaceHolder>file_status symlink_status(const path& pval);  
file_status symlink_status(const path& pval,  
    erroxr_code& ec) noexcept;  
  
<CodeContentPlaceHolder>39</CodeContentPlaceHolder>path system_complete(const path& pval);  
path system_complete(const path& pval,  
    error_code& ec);  
  
<CodeContentPlaceHolder>40</CodeContentPlaceHolder>path temp_directory_path();  
path temp_directory_path(  
    error_code& ec);  
  
<CodeContentPlaceHolder>41</CodeContentPlaceHolder>template<class Source>  
    path u8path(const Source& source);  
template<class InIt>  
    path u8path(InIt first, InIt last);  
  
```  
  
 第一个函数的行为与 path\(source\) 相同，第二个函数的行为与 path\(first, last\) 相同，只是每种情况中的指定源被视为编码为 UTF\-8 的 char 元素序列（无论是何种文件系统）。