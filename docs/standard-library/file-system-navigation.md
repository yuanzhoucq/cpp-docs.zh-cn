---
title: "文件系统导航 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: f7cc5f5e-a541-4e00-87c7-a3769ef6096d
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 文件系统导航
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\<filesystem\> 标头实施草稿文件系统技术规范 \([ISO\/IEC JTC 1\/SC 22\/WG 21 N4100](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4100.pdf)\)，并具有可用以编写独立于平台的代码从而实现文件系统导航的类型和函数。 因为它是跨平台的，所以包含与 Windows 系统不相关的 API。 例如，这意味着 `is_fifo(const path&)` 在 Windows 上始终返回 `false`。 标头基于草稿技术规范，截至 Visual Studio 2015 RTM，该规范尚未入选 C\+\+17 标准。 其成员都位于 `std::experimental::filesystem::v1` 命名空间中。  
  
## 概述  
 将\<文件系统\> API 用于以下任务：  
  
-   循环访问指定路径下的文件和目录  
  
-   获取有关包含创建时间、大小、扩展名和根目录的文件的信息  
  
-   编写、分解和比较路径  
  
-   创建、复制和删除目录  
  
-   复制和删除文件  
  
 有关使用标准库的文件 IO 的详细信息，请参阅 [iostream 编程](../standard-library/iostream-programming.md)。  
  
## 路径  
  
### 构造和编写路径  
 Windows（自 XP 起）中的路径以 Unicode 格式进行本机存储。[path](../standard-library/path-class-cpp-standard-template-library.md) 类自动执行所有必需的字符串转换。 它同时接受宽字符数组和窄字符数组的参数，以及格式化为 UTF8 或 UTF16 的 `std::string` 和 `std::wstring` 类型。`path` 类还自动标准化路径分隔符。 可在构造函数参数中将单个正斜杠用作目录分隔符。 这样你就能够使用相同的字符串将路径同时存储在 Windows 和 UNIX 环境中：  
  
```cpp  
path pathToDisplay(L"/FileSystemTest/SubDir3"); // OK! path pathToDisplay2(L"\\FileSystemTest\\SubDir3"); // Still OK as always path pathToDisplay3(LR"(\FileSystemTest\SubDir3)"); // Raw string literals are OK, too.  
```  
  
 若要连接两个路径，可使用重载的  `/` 和 `/=` 运算符，它们类似于 `std::string` 和 `std::wstring` 上的 `+` 和 `+=` 运算符。`path` 对象方便提供分隔符（如果你不提供的话）。  
  
```cpp  
path myRoot("C:/FileSystemTest"); // no trailing separator, no problem! myRoot /= path("SubDirRoot"); // C:/FileSystemTest/SubDirRoot  
```  
  
### 检查路径  
 path 类具有多种方法用以返回关于路径本身各个部分的信息，这不同于其可能引用的文件系统实体。 可以获取根、相对路径、文件名、文件扩展名及更多内容。 可循环访问路径对象以检查层次结构中的所有文件夹。 下面的示例演示如何循环访问路径（而非其引用的目录），以及如何检索有关其部件的信息。  
  
```cpp  
  
#include <string> #include <iostream> #include <sstream> #include <filesystem> using namespace std; using namespace std::experimental::filesystem::v1; wstring  DisplayPathInfo() { // This path may or may not refer to an existing file. We are // examining this path string, not file system objects. path pathToDisplay(L"C:/FileSystemTest/SubDir3/SubDirLevel2/File2.txt "); wostringstream wos; int i = 0; wos << L"Displaying path info for: " << pathToDisplay << endl; for (path::iterator itr = pathToDisplay.begin(); itr != pathToDisplay.end(); ++itr) { wos << L"path part: " << i++ << L" = " << *itr << endl; } wos << L"root_name() = " << pathToDisplay.root_name() << endl << L"root_path() = " << pathToDisplay.root_path() << endl << L"relative_path() = " << pathToDisplay.relative_path() << endl << L"parent_path() = " << pathToDisplay.parent_path() << endl << L"filename() = " << pathToDisplay.filename() << endl << L"stem() = " << pathToDisplay.stem() << endl << L"extension() = " << pathToDisplay.extension() << endl; return wos.str(); } void main(int argc, char* argv[]) { wcout << DisplayPathInfo() << endl; // wcout << ComparePaths() << endl; // see following example wcout << endl << L"Press Enter to exit" << endl; wstring input; getline(wcin, input); }  
```  
  
 此代码产生以下输出：  
  
```cpp  
Displaying path info for: C:\FileSystemTest\SubDir3\SubDirLevel2\File2.txt path part: 0 = C: path part: 1 = \ path part: 2 = FileSystemTest path part: 3 = SubDir3 path part: 4 = SubDirLevel2 path part: 5 = File2.txt root_name() = C: root_path() = C:\ relative_path() = FileSystemTest\SubDir3\SubDirLevel2\File2.txt parent_path() = C:\FileSystemTest\SubDir3\SubDirLevel2 filename() = File2.txt stem() = File2 extension() = .txt  
```  
  
### 比较路径  
 `path` 类会重载与 `std::string` 和 `std::wstring` 相同的比较运算符。 比较两个路径时，就是在分隔符已标准化后执行字符串比较。 如果缺少尾部斜杠（或反斜杠），则它不会被添加，并会影响比较。 下面的示例演示如何比较路径值：  
  
```cpp  
  
wstring ComparePaths() { path p0(L"C:/Documents"); // no trailing separator path p1(L"C:/Documents/"); //p0 < p1 path p2(L"C:/Documents/2013/"); // p1 < p2 path p3(L"C:/Documents/2013/Reports/"); // p2 < p3 path p4(L"C:/Documents/2014/");  // p3 < p4 path p5(L"D:/Documents/2013/Reports/"); // p4 < p5 wostringstream wos; wos << boolalpha << p0.wstring() << L" < " << p1.wstring() << L": " << (p0 < p1) << endl << p1.wstring() << L" < " << p2.wstring() << L": " << (p1 < p2) << endl << p2.wstring() << L" < " << p3.wstring() << L": " << (p2 < p3) << endl << p3.wstring() << L" < " << p4.wstring() << L": " << (p3 < p4) << endl << p4.wstring() << L" < " << p5.wstring() << L": " << (p4 < p5) << endl; return wos.str(); } /* Output: C:\Documents < C:\Documents\: true C:\Documents\ < C:\Documents\2013\: true C:\Documents\2013\ < C:\Documents\2013\Reports\: true C:\Documents\2013\Reports\ < C:\Documents\2014\: true C:\Documents\2014\ < D:\Documents\2013\Reports\: true */  
```  
  
 若要运行此代码，请将其粘贴到上面的完整示例中，并取消注释在 main 中调用它的行。  
  
### 在路径和字符串类型之间进行转换  
 `path` 对象可隐式转换为 `std::wstring` 或 `std::string`。 这意味着可以将路径传递给如 [wofstream::open](../Topic/basic_ofstream::open.md) 等函数，如此示例中所示：  
  
```cpp  
wchar_t* p = L"C:/test"; path filePath(p); filePath /= L"NewFile.txt"; // Open, write to, and close the file. wofstream myFile; myFile.open(filePath); myFile << L"Lorem ipsum..."; myFile.close  
  
```  
  
## 循环访问目录和文件  
 \<文件系统\>标头提供 [directory\_iterator](../standard-library/directory-iterator-class.md) 类型以循环访问单个目录，以及提供 [recursive\_directory\_iterator](../standard-library/recursive-directory-iterator-class.md) 类以递归方式循环访问目录及其子目录。 通过向迭代器传递一个 `path` 对象来构造该迭代器之后，该迭代器指向路径中的第一个 directory\_entry。 通过调用默认构造函数创建结尾迭代器。  
  
 当循环访问一个目录时，可能会遇到几种类型的项，其中包括但不限于目录、文件、符号链接和套接字文件。`directory_iterator` 将其项返回为 [directory\_entry](../standard-library/directory-entry-class.md) 对象，且每个对象都具有一个 [status\(\)](http://msdn.microsoft.com/zh-cn/a70a3c55-3a76-417f-abaf-862ff94b2056) 成员，该成员会告知你正在查看哪种类型的项。 通过检查这个值，可以决定要为任何特定项执行的操作。 下面的示例循环访问单个目录，如果目录项是常规文件，该代码会输出一些关于该文件的信息。 如果项是目录，则只显示名称。  
  
```cpp  
#include <string> #include <iostream> #include <iomanip> #include <filesystem> #include <chrono> #include <time.h> using namespace std; using namespace std::experimental::filesystem::v1; // Display the last write time for the file wstring LastWriteTimeToLocalTime(const path& file_path) { const auto last = chrono::system_clock::to_time_t(last_write_time(file_path)); tm timeinfo; localtime_s(&timeinfo, &last); wchar_t buf[56]; _wasctime_s(buf, 56, &timeinfo); // appends '\n' return wstring{ buf }; } // List files and directories in the specified path void DisplayFolderContents(const path& p) { wcout << L"Begin iterating " << p.wstring() << endl; for (const auto& entry : directory_iterator{ p }) { if (is_regular_file(entry.status())) { wcout << L" File: " << entry.path().filename() << " : " << LastWriteTimeToLocalTime(entry.path()); } else if (is_directory(entry.status())) { wcout << L" Dir: " << entry.path().filename() << endl; } } } void main() { wstring dir{ LR"(C:\users\public\documents\)" }; path p{ dir }; if (!is_directory(p)) { wcout << L"No such directory: " << dir << endl; return; } DisplayFolderContents(p); // IterateFolderRecursively(p); // see example wcout << endl << L"Press Enter to exit" << endl; wstring input; getline(wcin, input); }  
```  
  
### 以递归方式循环访问目录树  
 下面的示例演示如何以递归方式循环访问目录树。 若要运行此函数，请将其粘贴到 DisplayFolderContents 函数之后的上一个代码示例中，并取消注释在 main 中调用它的行。  
  
```cpp  
// List files and directories recursively in the path void IterateFolderRecursively(const path& p) { wcout << L"Begin iterating " << p.wstring() << " recursively" << endl; for (recursive_directory_iterator it{ p }, end; it != end; ++it) { if (is_regular_file(it->status())) { wcout << setw(it.depth()) << L" " << L"File: " << it->path().filename() << L" : " << LastWriteTimeToLocalTime(it->path()); } else if (is_directory(it->status())) { wcout << setw(it.depth()) << L" " << L"Dir: " << it->path().filename() << endl; } } }  
```  
  
### 处理符号链接  
 Visual Studio 2015 及之前版本中的 Visual C\+\+ 尚不支持符号链接检测。