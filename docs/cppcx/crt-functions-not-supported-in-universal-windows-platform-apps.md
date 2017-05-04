---
title: "通用 Windows 平台应用中不支持的 CRT 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cbfc957d-6c60-48f4-97e3-1ed8526743b4
caps.latest.revision: 15
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 15
---
# 通用 Windows 平台应用中不支持的 CRT 函数
生成通用 Windows 平台 \(UWP\) 应用时，许多 C 运行时 \(CRT\) 函数不可用。 在某些情况下，有解决方法是可用（例如，可以使用 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]或 Win32 API）。 但是在其他情况下，CRT 函数被禁止使用，因为对应于它们的功能或支持 API 不适用于 UWP 应用。  
  
 下表列出了在生成 UWP 应用时不可用的 CRT 函数，并指出了任何适用的解决方法。  
  
## 不支持的 CRT 函数  
  
||||  
|-|-|-|  
|\_beep \_sleep \_seterrormode|这些函数在以前版本的 CRT 中已过时。 此外，对应 Win32 API 不可用于 UWP 应用。|无解决方法。|  
|chdir \_chdrive getcwd|这些函数已过时或不是线程安全的。|使用 \_chdir、\_getcwd 及相关函数。|  
|\_cgets \_cgets\_s \_cgetws \_cgetws\_s \_cprintf \_cprintf\_l \_cprintf\_p \_cprintf\_p\_l \_cprintf\_s \_cprintf\_s\_l \_cputs \_cputws \_cscanf \_cscanf\_l \_cscanf\_s \_cscanf\_s\_l \_cwait \_cwprintf \_cwprintf\_l \_cwprintf\_p \_cwprintf\_p\_l \_cwprintf\_s \_cwprintf\_s\_l \_cwscanf \_cwscanf\_l \_cwscanf\_s \_cwscanf\_s\_l \_vcprintf \_vcprintf\_l \_vcprintf\_p \_vcprintf\_p\_l \_vcprintf\_s \_vcprintf\_s\_l \_vcwprintf \_vcwprintf\_l \_vcwprintf\_p \_vcwprintf\_p\_l \_vcwprintf\_s \_vcwprintf\_s\_l \_getch \_getch\_nolock \_getche \_getche\_nolock \_getwch \_getwch\_nolock \_getwche \_getwche\_nolock \_putch \_putch\_nolock \_putwch \_putwch\_nolock \_ungetch \_ungetch\_nolock \_ungetwch \_ungetwch\_nolock \_kbhit kbhit putch cgets cprintf cputs cscanf cwait getch getche ungetch|这些函数用于直接从控制台读取和写入控制台。 UWP 应用仅限 GUI；它们不支持控制台。|无解决方法。|  
|getpid|此函数已过时。|使用 \_getpid 或 Win32 API `GetCurrentProcessId()`。|  
|\_getdiskfree|不可用。|使用 Win32 API `GetDiskFreeSpaceExW()`。|  
|\_getdrive \_getdrives|对应 API 不可用于 UWP 应用。|无解决方法。|  
|\_inp \_inpd \_inpw \_outp \_outpd \_outpw inp inpd inpw outp outpd outpw|UWP 应用中不支持端口 IO。|无解决方法。|  
|\_ismbcalnum \_ismbcalnum\_l \_ismbcalpha \_ismbcalpha\_l \_ismbcdigit \_ismbcdigit\_l \_ismbcgraph \_ismbcgraph\_l \_ismbchira \_ismbchira\_l \_ismbckata \_ismbckata\_l \_ismbcl0 \_ismbcl0\_l \_ismbcl1 \_ismbcl1\_l \_ismbcl2 \_ismbcl2\_l \_ismbclegal \_ismbclegal\_l \_ismbclower \_ismbclower\_l \_ismbcprint \_ismbcprint\_l \_ismbcpunct \_ismbcpunct\_l \_ismbcspace \_ismbcspace\_l \_ismbcsymbol \_ismbcsymbol\_l \_ismbcupper \_ismbcupper\_l \_mbbtombc \_mbbtombc\_l \_mbbtype \_mbbtype\_l \_mbccpy \_mbccpy\_l \_mbccpy\_s \_mbccpy\_s\_l \_mbcjistojms \_mbcjistojms\_l \_mbcjmstojis \_mbcjmstojis\_l \_mbclen \_mbclen\_l \_mbctohira \_mbctohira\_l \_mbctokata \_mbctokata\_l \_mbctolower \_mbctolower\_l \_mbctombb \_mbctombb\_l \_mbctoupper \_mbctoupper\_l \_mbsbtype \_mbsbtype\_l \_mbscat \_mbscat\_l \_mbscat\_s \_mbscat\_s\_l \_mbschr \_mbschr\_l \_mbscmp \_mbscmp\_l \_mbscoll \_mbscoll\_l \_mbscpy \_mbscpy\_l \_mbscpy\_s \_mbscpy\_s\_l \_mbscspn \_mbscspn\_l \_mbsdec \_mbsdec\_l \_mbsicmp \_mbsicmp\_l \_mbsicoll \_mbsicoll\_l \_mbsinc \_mbsinc\_l \_mbslen \_mbslen\_l \_mbslwr \_mbslwr\_l \_mbslwr\_s \_mbslwr\_s\_l \_mbsnbcat \_mbsnbcat\_l \_mbsnbcat\_s \_mbsnbcat\_s\_l \_mbsnbcmp \_mbsnbcmp\_l \_mbsnbcnt \_mbsnbcnt\_l \_mbsnbcoll \_mbsnbcoll\_l \_mbsnbcpy \_mbsnbcpy\_l \_mbsnbcpy\_s \_mbsnbcpy\_s\_l \_mbsnbicmp \_mbsnbicmp\_l \_mbsnbicoll \_mbsnbicoll\_l \_mbsnbset \_mbsnbset\_l \_mbsnbset\_s \_mbsnbset\_s\_l \_mbsncat \_mbsncat\_l \_mbsncat\_s \_mbsncat\_s\_l \_mbsnccnt \_mbsnccnt\_l \_mbsncmp \_mbsncmp\_l \_mbsncoll \_mbsncoll\_l \_mbsncpy \_mbsncpy\_l \_mbsncpy\_s \_mbsncpy\_s\_l \_mbsnextc \_mbsnextc\_l \_mbsnicmp \_mbsnicmp\_l \_mbsnicoll \_mbsnicoll\_l \_mbsninc \_mbsninc\_l \_mbsnlen \_mbsnlen\_l \_mbsnset \_mbsnset\_l \_mbsnset\_s \_mbsnset\_s\_l \_mbspbrk \_mbspbrk\_l \_mbsrchr \_mbsrchr\_l \_mbsrev \_mbsrev\_l \_mbsset \_mbsset\_l \_mbsset\_s \_mbsset\_s\_l \_mbsspn \_mbsspn\_l \_mbsspnp \_mbsspnp\_l \_mbsstr \_mbsstr\_l \_mbstok \_mbstok\_l \_mbstok\_s \_mbstok\_s\_l \_mbsupr \_mbsupr\_l \_mbsupr\_s \_mbsupr\_s\_l is\_wctype|UWP 应用中不支持多字节字符串。|改为使用 Unicode 字符串。|  
|\_pclose \_pipe \_popen \_wpopen|管道功能不可用于 UWP 应用。|无解决方法。|  
|\_resetstkoflw|支持 Win32 API 不可用于 UWP 应用。|无解决方法。|  
|\_getsystime \_setsystime|这些是以前 CRT 版本中的已过时 API。 此外，用户无法在 UWP 应用中设置系统时间，因为缺少权限。|若要只获取系统时间，请使用 Win32 API `GetSystemTime`。 无法设置系统时间。|  
|\_environ \_putenv \_putenv\_s \_searchenv \_searchenv\_s \_dupenv\_s \_wputenv \_wputenv\_s \_wsearchenv getenv getenv\_s putenv \_wdupenv\_s \_wenviron \_wgetenv \_wgetenv\_s \_wsearchenv\_s tzset|环境变量不可用于 UWP 应用。|无解决方法。 若要设置时区，请使用 \_tzset。|  
|\_loaddll \_getdllprocaddr \_unloaddll|这些是以前 CRT 版本中的已过时函数。 此外，用户无法加载 DLL（同一个应用程序包中的 DLL 除外）。|使用 Win32 API `LoadPackagedLibrary`、`GetProcAddress` 和 `FreeLibrary` 加载和使用打包的 DLL。|  
|\_wexecl \_wexecle \_wexeclp \_wexeclpe \_wexecv \_wexecve \_wexecvp \_wexecvpe \_execl \_execle \_execlp \_execlpe \_execv \_execve \_execvp \_execvpe \_spawnl \_spawnle \_spawnlp \_spawnlpe \_spawnv \_spawnve \_spawnvp \_spawnvpe \_wspawnl \_wspawnle \_wspawnlp \_wspawnlpe \_wspawnv \_wspawnve \_wspawnvp \_wspawnvpe \_wsystem execl execle execlp execlpe execv execve execvp execvpe spawnl spawnle spawnlp spawnlpe spawnv spawnve spawnvp spawnvpe system|该功能在 UWP 应用中不可用。 UWP 应用无法调用另一个 UWP 应用或桌面应用。|无解决方法。|  
|\_heapwalk \_heapadd \_heapchk \_heapset \_heapused|这些函数通常用于处理堆。 但是，UWP 应用中不支持对应 Win32 API。 而且，应用无法再创建或使用专用堆。|无解决方法。 但是，`_heapwalk` 在 DEBUG CRT 中可用（仅用于进行调试）。 这些函数无法在上载到 Windows 应用商店的应用中使用。|  
  
 以下函数在 CRT 中可用于 UWP 应用，但应仅当无法使用对应 Win32 或 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] API 时才使用（例如，要移植大型基本代码时）。  
  
|||  
|-|-|  
|单字节字符串函数（例如，`strcat`、`strcpy`、`strlwr` 等）。|使 UWP 应用严格遵循 Unicode 标准，因为公开的所有 Win32 API 和 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] API 都仅使用 Unicode 字符集。 保留了单字节函数，以便用于移植大型基本代码，但在其他情况下应避免使用，并且应尽可能改用对应的宽字符函数。|  
|流 IO 和低级文件 IO 函数（例如，`fopen`、`open` 等）。|这些函数是同步的，不推荐用于 UWP 应用。 在 UWP 应用中，使用异步 API 打开、读取和写入文件，以防止锁定 UI 线程。 这类 API 的示例是在 `Windows::Storage::FileIO` 类中的一个。|  
  
## Windows 8.x 应用商店应用和 Windows Phone 8.x 应用  
 除了前面提到的 API 之外，以下 API 在 Windows 8.x 应用商店应用和 Windows Phone 8.x 应用中不可用。  
  
||||  
|-|-|-|  
|\_beginthread \_beginthreadex \_endthread \_endthreadex|线程处理 Win32 API 在 Windows 8.x 应用商店应用中不可用。|改用 `Windows Runtime Windows::System::Threading::ThreadPool` 或 `concurrency::task`。|  
|\_chdir \_wchdir \_getcwd \_getdcwd \_wgetcwd \_wgetdcwd|工作目录的概念不适用于 Windows 8.x 应用商店应用。|改用完整路径。|  
|\_getpid|此函数在以前版本的 CRT 中已过时。|使用 Win32 API `GetCurrentProcessId()`|  
|\_isleadbyte\_l \_ismbbalnum, \_ismbbalnum\_l, \_ismbbalpha, \_ismbbalpha \_ismbbalpha\_l \_ismbbgraph \_ismbbgraph\_l \_ismbbkalnum \_ismbbkalnum\_l \_ismbbkana \_ismbbkana\_l \_ismbbkprint \_ismbbkprint\_l \_ismbbkpunct \_ismbbkpunct\_l \_ismbblead \_ismbblead\_l \_ismbbprint \_ismbbprint\_l \_ismbbpunct \_ismbbpunct\_l \_ismbbtrail \_ismbbtrail\_l \_ismbslead \_ismbslead\_l \_ismbstrail \_ismbstrail\_l \_mbsdup isleadbyte|Windows 8.x 应用商店应用中不支持多字节字符串。|改为使用 Unicode 字符串。|  
|\_tzset|环境变量不可用于 Windows 8.x 应用商店应用。|无解决方法。|  
|\_get\_heap\_handle、\_heapmin|Windows 8.x 应用商店应用中不支持对应 Win32 API。 而且，应用无法再创建专用堆。|无解决方法。 但是，`_get_heap_handle` 在 DEBUG CRT 中可用（仅用于进行调试）。|