---
title: CTime 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTime
- ATLTIME/ATL::CTime
- ATLTIME/ATL::CTime::CTime
- ATLTIME/ATL::CTime::Format
- ATLTIME/ATL::CTime::FormatGmt
- ATLTIME/ATL::CTime::GetAsDBTIMESTAMP
- ATLTIME/ATL::CTime::GetAsSystemTime
- ATLTIME/ATL::CTime::GetCurrentTime
- ATLTIME/ATL::CTime::GetDay
- ATLTIME/ATL::CTime::GetDayOfWeek
- ATLTIME/ATL::CTime::GetGmtTm
- ATLTIME/ATL::CTime::GetHour
- ATLTIME/ATL::CTime::GetLocalTm
- ATLTIME/ATL::CTime::GetMinute
- ATLTIME/ATL::CTime::GetMonth
- ATLTIME/ATL::CTime::GetSecond
- ATLTIME/ATL::CTime::GetTime
- ATLTIME/ATL::CTime::GetYear
- ATLTIME/ATL::CTime::Serialize64
dev_langs:
- C++
helpviewer_keywords:
- CTime class
- shared classes, CTime
ms.assetid: 0a299544-485b-48dc-9d3c-fdc30f57d612
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8ec195c7733255487b08f8b48379abe58e305f61
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="ctime-class"></a>CTime 类
表示绝对时间和日期。  
  
## <a name="syntax"></a>语法  
  
```  
class CTime  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CTime::CTime](#ctime)|构造`CTime`中各种方法的对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CTime::Format](#format)|将转换`CTime`到格式化字符串中的对象-基于本地时区。|  
|[CTime::FormatGmt](#formatgmt)|将转换`CTime`到格式化字符串中的对象-基于 UTC。|  
|[CTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|将转换中存储的时间信息`CTime`与 Win32 兼容 DBTIMESTAMP 结构的对象。|  
|[CTime::GetAsSystemTime](#getassystemtime)|将转换中存储的时间信息`CTime`对象与 Win32 兼容[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)结构。|  
|[CTime::GetCurrentTime](#getcurrenttime)|创建`CTime`对象，表示当前时间 （静态成员函数）。|  
|[CTime::GetDay](#getday)|返回由一天表示`CTime`对象。|  
|[CTime::GetDayOfWeek](#getdayofweek)|返回表示星期几`CTime`对象。|  
|[CTime::GetGmtTm](#getgmttm)|将分解`CTime`为组件的对象-基于 UTC。|  
|[CTime::GetHour](#gethour)|返回表示的小时`CTime`对象。|  
|[CTime::GetLocalTm](#getlocaltm)|将分解`CTime`为组件的对象-基于本地时区。|  
|[CTime::GetMinute](#getminute)|返回表示分钟`CTime`对象。|  
|[CTime::GetMonth](#getmonth)|返回表示月`CTime`对象。|  
|[CTime::GetSecond](#getsecond)|返回由第二个`CTime`对象。|  
|[CTime::GetTime](#gettime)|返回 **__time64_t**值，则为给定`CTime`对象。|  
|[CTime::GetYear](#getyear)|返回所表示的年份`CTime`对象。|  
|[CTime::Serialize64](#serialize64)|序列化或从存档的数据。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[运算符 +-](#operator_add_-)|这些运算符加法和减法`CTimeSpan`和`CTime`对象。|  
|[运算符 + =、 =](#operator_add_eq_-_eq)|这些运算符加法和减法`CTimeSpan`对象与其他这`CTime`对象。|  
|[operator =](#operator_eq)|赋值运算符中。|  
|[运算符 = =、 < 等。](#ctime_comparison_operators)|比较运算符。|  
  
## <a name="remarks"></a>备注  
 `CTime` 没有基类。  
  
 `CTime` 值基于协调世界时 (UTC)，这等同于协调世界时 （格林威治标准时间，格林威治标准时间）。 请参阅[时间管理](../../c-runtime-library/time-management.md)有关如何确定时区信息。  
  
 当你创建`CTime`对象，设置`nDST`参数为 0 来指示标准时间是在起作用，或到的值大于 0 来指示该夏时制是否生效，或为一个值小于零 C 运行时库代码计算机e 是否是标准时间还是夏令时有效。 `tm_isdst` 是必填字段。 如果未设置，未定义其值和返回值从[mktime](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)是不可预知的。 如果`timeptr`指向返回上次调用 tm 结构[asctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)， [_gmtime_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)，或[localtime_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)、`tm_isdst`字段包含正确的值。  
  
 伴生类， [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)，表示一个时间间隔。  
  
 `CTime`和`CTimeSpan`类不用于派生。 因为没有虚拟函数的大小`CTime`和`CTimeSpan`对象是 8 个字节。 大多数成员函数是内联的。  
  
> [!NOTE]
>  上部日期限制为 12/31/3000。 较低的限制是 1970 年 1 月 1 日格林威治标准时间上午 12:00:00。  
  
 有关使用`CTime`，请参阅文章[日期和时间](../../atl-mfc-shared/date-and-time.md)，和[时间管理](../../c-runtime-library/time-management.md)运行时库参考中。  
  
> [!NOTE]
>  `CTime`结构从 MFC 7.1 更改为 MFC 8.0。 如果序列化`CTime`结构使用`operator <<`在 MFC 8.0 或更高版本下，生成的文件不会在较旧版本的 MFC 可读。  
  
## <a name="requirements"></a>要求  
 **标头：** atltime.h  
  
##  <a name="ctime_comparison_operators"></a>  CTime 比较运算符  
 比较运算符。  
  
```  
bool operator==(CTime time) const throw(); 
bool operator!=(CTime time) const throw();
bool operator<(CTime time) const throw();
bool operator>(CTime time) const throw();
bool operator<=(CTime time) const throw();
bool operator>=(CTime time) const throw(); 
```  
  
### <a name="parameters"></a>参数  
 `time`  
 要比较的 `CTime` 对象。  
  
### <a name="return-value"></a>返回值  
 这些运算符比较两个绝对时间，并返回**true**如果条件为 true; 否则为**false**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#161](../../atl-mfc-shared/codesnippet/cpp/ctime-class_1.cpp)]  
  
##  <a name="ctime"></a>  CTime::CTime  
 创建一个新`CTime`对象初始化为指定的时间。  
  
```  
CTime() throw(); 
CTime(__time64_t time) throw();
CTime(int nYear, int nMonth, int nDay,
      int nHour, int nMin, int nSec, int nDST = -1);
CTime(WORD wDosDate, WORD wDosTime, int nDST = -1);
CTime(const SYSTEMTIME& st, int nDST = - 1) throw();
CTime(const FILETIME& ft, int nDST = - 1);
CTime(const DBTIMESTAMP& dbts,int nDST = -1) throw();
```  
  
### <a name="parameters"></a>参数  
 `timeSrc`  
 指示`CTime`已存在的对象。  
  
 `time`  
 A **__time64_t**时间值，该值是 UTC 1970 年 1 月 1 日之后的秒数。 请注意这将调整为你的本地时间。 例如，如果你位于纽约，创建`CTime`对象将为 0，参数传递[CTime::GetMonth](#getmonth)将返回 12。  

  
 `nYear`, `nMonth`, `nDay`, `nHour`, `nMin`, `nSec`  
 指示要复制到新的日期和时间值`CTime`对象。  
  
 `nDST`  
 指示夏令时是否有效。 可以具有三个值之一：  
  
- `nDST` 设置为 0Standard 时间将发挥作用。  
  
- `nDST` 设置为值大于 0Daylight 实际上是节省时间。  
  
- `nDST` 设置为小于 0The 默认值。 自动计算是否是标准时间还是夏令时有效。  
  
 `wDosDate`, `wDosTime`  
 MS-DOS 日期和时间值被转换为日期/时间值并复制到新`CTime`对象。  
  
 `st`  
 A [SYSTEMTIME](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/d6609fff-1931-4818-8a26-f042630af0b0/locales/en-us)结构转换为日期/时间值并复制到新`CTime`对象。  
  
 `ft`  
 A [FILETIME](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/979ce746-dc17-4147-89f8-41d05c5fcc5f/locales/en-us)结构转换为日期/时间值并复制到新`CTime`对象。  
  
 dbts  
 包含当前本地时间的 DBTIMESTAMP 结构引用。  
  
### <a name="remarks"></a>备注  
 下面描述了每个构造函数：  
  
- **CTime();** 构造未经初始化即`CTime`对象。 此构造函数允许你定义`CTime`对象数组。 在使用之前的有效时间与此类阵列，你应将其初始化。  
  
- **CTime (const CTime （& a));** 构造`CTime`从另一个对象`CTime`值。  
  
- **CTime (__time64_t);** 构造`CTime`对象 **__time64_t**类型。 此构造函数需要 UTC 时间，并将结果存储在之前将结果转换为本地时间。  
  
- **CTime （int、 int、...）;** 构造`CTime`从本地时间与每个组件的组件的对象限制为以下范围：  
  
    |组件|范围|  
    |---------------|-----------|  
    |`nYear`|1970-3000|  
    |`nMonth`|1-12|  
    |`nDay`|1-31|  
    |`nHour`|0-23|  
    |`nMin`|0-59|  
    |`nSec`|0-59|  
  
     此构造函数生成的合适转换为 UTC。 Microsoft 基础类库的调试版本断言如果一个或多个时间组件超出范围。 你必须验证之前调用的自变量。 此构造函数需要本地时间。  
  
- **CTime （WORD、 WORD）;** 构造`CTime`从指定的 MS-DOS 日期和时间值的对象。 此构造函数需要本地时间。  
  
- **CTime (const SYSTEMTIME （& a));** 构造`CTime`对象`SYSTEMTIME`结构。 此构造函数需要本地时间。  
  
- **CTime (const FILETIME （& a));** 构造`CTime`对象`FILETIME`结构。 你最有可能将不会使用`CTime FILETIME`直接初始化。 如果你使用`CFile`对象操作文件，`CFile::GetStatus`为你通过检索文件时间戳`CTime`使用初始化对象`FILETIME`结构。 此构造函数采用基于 UTC 的时间，并自动将值转换为本地时间，并将结果存储之前。  
  
    > [!NOTE]
    >  构造函数使用**DBTIMESTAMP**参数包含 OLEDB.h 时才可用。  
  
 有关详细信息，请参阅[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)和[FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284) Windows SDK 中的结构。 另请参阅[MS-DOS 日期和时间](http://msdn.microsoft.com/library/windows/desktop/ms724503)Windows SDK 中的条目。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#148](../../atl-mfc-shared/codesnippet/cpp/ctime-class_2.cpp)]  
  
##  <a name="format"></a>  CTime::Format  
 调用此成员函数来创建的日期时间值的格式的表示。  
  
```  
CString Format(LPCTSTR pszFormat) const; 
CString Format(UINT nFormatID) const; 
```  
  
### <a name="parameters"></a>参数  
 `pszFormat`  
 格式设置字符串类似于`printf`格式化字符串。 格式设置代码，前面是百分比 ( `%`) 登录，替换为相应`CTime`组件。 格式设置字符串中的其他字符被复制到返回的字符串不变。 请参阅运行时函数[strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)有关格式设置代码的列表。  
  
 `nFormatID`  
 标识此格式的字符串的 ID。  
  
### <a name="return-value"></a>返回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md)包含格式的时间。  
  
### <a name="remarks"></a>备注  
 如果此状态`CTime`对象为 null，则返回值为空字符串。  
  
 此方法将引发异常，如果要设置格式的日期时间值超出范围从 1970 年 1 月 1 日通过 3000 年 12 月 31 日午夜协调世界时 (UTC)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#149](../../atl-mfc-shared/codesnippet/cpp/ctime-class_3.cpp)]  
  
##  <a name="formatgmt"></a>  CTime::FormatGmt  
 生成与对应于此的格式化的字符串`CTime`对象。  
  
```  
CString FormatGmt(LPCTSTR pszFormat) const; 
CString FormatGmt(UINT nFormatID) const; 
```  
  
### <a name="parameters"></a>参数  
 `pszFormat`  
 指定的格式设置字符串类似于`printf`格式化字符串。 请参阅运行时函数[strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)有关详细信息。  
  
 `nFormatID`  
 标识此格式的字符串的 ID。  
  
### <a name="return-value"></a>返回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md)包含格式的时间。  
  
### <a name="remarks"></a>备注  
 时间值不会进行转换，并因此反映 UTC。  
  
 此方法将引发异常，如果要设置格式的日期时间值超出范围从 1970 年 1 月 1 日通过 3000 年 12 月 31 日午夜协调世界时 (UTC)。  
  
### <a name="example"></a>示例  
 请参阅示例[CTime::Format](#format)。  
  
##  <a name="getasdbtimestamp"></a>  CTime::GetAsDBTIMESTAMP  
 调用此成员函数将转换中存储的时间信息`CTime`与 Win32 兼容 DBTIMESTAMP 结构的对象。  
  
```  
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```  
  
### <a name="parameters"></a>参数  
 `dbts`  
 包含当前本地时间的 DBTIMESTAMP 结构引用。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 将所得到的时间存储在引用的 `dbts` 结构中。 **DBTIMESTAMP**由此函数初始化的数据结构将包含其**分数**成员设置为零。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#150](../../atl-mfc-shared/codesnippet/cpp/ctime-class_4.cpp)]  
  
##  <a name="getassystemtime"></a>  CTime::GetAsSystemTime  
 调用此成员函数将转换中存储的时间信息`CTime`对象与 Win32 兼容[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)结构。  
  
```  
bool GetAsSystemTime(SYSTEMTIME& st) const throw();
```  
  
### <a name="parameters"></a>参数  
 *timeDest*  
 对引用[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)结构，它将保存转换后的日期/时间值的`CTime`对象。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为 true否则为 false。  
  
### <a name="remarks"></a>备注  
 `GetAsSystemTime` 将所生成的时间存储在引用*timeDest*结构。 `SYSTEMTIME`由此函数初始化的数据结构将包含其**wMilliseconds**成员设置为零。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#151](../../atl-mfc-shared/codesnippet/cpp/ctime-class_5.cpp)]  
  
##  <a name="getcurrenttime"></a>  CTime::GetCurrentTime  
 返回`CTime`对象，表示当前时间。  
  
```  
static CTime WINAPI GetCurrentTime() throw();
```  
  
### <a name="remarks"></a>备注  
 返回当前系统日期和时间以协调世界时 (UTC)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#152](../../atl-mfc-shared/codesnippet/cpp/ctime-class_6.cpp)]  
  
##  <a name="getday"></a>  CTime::GetDay  
 返回由一天表示`CTime`对象。  
  
```  
int GetDay() const throw(); 
```  
  
### <a name="return-value"></a>返回值  
 返回的月份，基于本地时间，范围从 1 到 31 天。  
  
### <a name="remarks"></a>备注  
 此函数将调用`GetLocalTm`，它使用的内部、 静态分配的缓冲区。 在此缓冲区中的数据覆盖彼此的调用由于`CTime`成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#153](../../atl-mfc-shared/codesnippet/cpp/ctime-class_7.cpp)]  
  
##  <a name="getdayofweek"></a>  CTime::GetDayOfWeek  
 返回表示星期几`CTime`对象。  
  
```  
int GetDayOfWeek() const throw(); 
```  
  
### <a name="return-value"></a>返回值  
 返回基于本地时间; 星期几1 = 星期日，2 = 星期一，到 7 = 星期六。  
  
### <a name="remarks"></a>备注  
 此函数将调用`GetLocalTm`，它使用内部静态分配缓冲区。 在此缓冲区中的数据覆盖彼此的调用由于`CTime`成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#154](../../atl-mfc-shared/codesnippet/cpp/ctime-class_8.cpp)]  
  
##  <a name="getgmttm"></a>  CTime::GetGmtTm  
 获取**结构 tm**包含包含在此时间的分解`CTime`对象。  
  
```  
struct tm* GetGmtTm(struct tm* ptm) const; 
```  
  
### <a name="parameters"></a>参数  
 `ptm`  
 指向以将接收时间数据的缓冲区。 此指针为时**NULL**，将引发异常。  
  
### <a name="return-value"></a>返回值  
 指向已填写的指针**结构 tm**定义在包含文件时间。H。 请参阅[gmtime、 _gmtime32、 _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)结构布局。  
  
### <a name="remarks"></a>备注  
 `GetGmtTm` 返回 UTC。  
  
 `ptm` 不能为 `NULL`。 如果你想要还原到旧行为，在其中`ptm`可能是`NULL`若要指示应使用的内部、 静态分配的缓冲区，然后取消定义`_SECURE_ATL`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#155](../../atl-mfc-shared/codesnippet/cpp/ctime-class_9.cpp)]  
  
##  <a name="gethour"></a>  CTime::GetHour  
 返回表示的小时`CTime`对象。  
  
```  
int GetHour() const throw(); 
```  
  
### <a name="return-value"></a>返回值  
 返回表示小时，基于本地时间，范围在 0 到 23。  
  
### <a name="remarks"></a>备注  
 此函数将调用`GetLocalTm`，它使用内部静态分配缓冲区。 在此缓冲区中的数据覆盖彼此的调用由于`CTime`成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#156](../../atl-mfc-shared/codesnippet/cpp/ctime-class_10.cpp)]  
  
##  <a name="getlocaltm"></a>  CTime::GetLocalTm  
 获取**结构 tm**包含包含在此时间的分解`CTime`对象。  
  
```  
struct tm* GetLocalTm(struct tm* ptm) const; 
```  
  
### <a name="parameters"></a>参数  
 `ptm`  
 指向以将接收时间数据的缓冲区。 此指针为时**NULL**，将引发异常。  
  
### <a name="return-value"></a>返回值  
 指向已填写的指针**结构 tm**定义在包含文件时间。H。 请参阅[gmtime、 _gmtime32、 _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)结构布局。  
  
### <a name="remarks"></a>备注  
 `GetLocalTm` 返回本地时间。  
  
 `ptm` 不能为 `NULL`。 如果你想要还原到旧行为，在其中`ptm`可能是`NULL`若要指示应使用的内部、 静态分配的缓冲区，然后取消定义`_SECURE_ATL`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#157](../../atl-mfc-shared/codesnippet/cpp/ctime-class_11.cpp)]  
  
##  <a name="getminute"></a>  CTime::GetMinute  
 返回表示分钟`CTime`对象。  
  
```  
int GetMinute() const throw(); 
```  
  
### <a name="return-value"></a>返回值  
 返回分钟，基于本地时间，范围在 0 到 59。  
  
### <a name="remarks"></a>备注  
 此函数将调用`GetLocalTm`，它使用内部静态分配缓冲区。 在此缓冲区中的数据覆盖彼此的调用由于`CTime`成员函数。  
  
### <a name="example"></a>示例  
 请参阅示例[GetHour](#gethour)。  
  
##  <a name="getmonth"></a>  CTime::GetMonth  
 返回表示月`CTime`对象。  
  
```  
int GetMonth() const throw(); 
```  
  
### <a name="return-value"></a>返回值  
 返回基于本地时间，范围从 1 到 12 的月份 (1 = 年 1 月)。  
  
### <a name="remarks"></a>备注  
 此函数将调用`GetLocalTm`，它使用内部静态分配缓冲区。 在此缓冲区中的数据覆盖彼此的调用由于`CTime`成员函数。  
  
### <a name="example"></a>示例  
 请参阅示例[GetDay](#getday)。  
  
##  <a name="getsecond"></a>  CTime::GetSecond  
 返回由第二个`CTime`对象。  
  
```  
int GetSecond() const throw(); 
```  
  
### <a name="return-value"></a>返回值  
 返回第二个，基于本地时间，范围在 0 到 59。  
  
### <a name="remarks"></a>备注  
 此函数将调用`GetLocalTm`，它使用内部静态分配缓冲区。 在此缓冲区中的数据覆盖彼此的调用由于`CTime`成员函数。  
  
### <a name="example"></a>示例  
 请参阅示例[GetHour](#gethour)。  
  
##  <a name="gettime"></a>  CTime::GetTime  
 返回 **__time64_t**值，则为给定`CTime`对象。  
  
```  
__time64_t GetTime() const throw(); 
```  
  
### <a name="return-value"></a>返回值  
 **GetTime**将返回当前之间的秒数`CTime`对象和自 1970 年 1 月 1 日。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#158](../../atl-mfc-shared/codesnippet/cpp/ctime-class_12.cpp)]  
  
##  <a name="getyear"></a>  CTime::GetYear  
 返回所表示的年份`CTime`对象。  
  
```  
int GetYear();
```  
  
### <a name="return-value"></a>返回值  
 返回年份，基于本地时间，在范围内年 1 月 1,1970，到 2038 年 1 月 18，（含）。  
  
### <a name="remarks"></a>备注  
 此函数将调用`GetLocalTm`，它使用内部静态分配缓冲区。 在此缓冲区中的数据覆盖彼此的调用由于`CTime`成员函数。  
  
### <a name="example"></a>示例  
 请参阅示例[GetDay](#getday)。  
  
##  <a name="operator_eq"></a>  CTime::operator =  
 赋值运算符中。  
  
```  
CTime& operator=(__time64_t time) throw();
```  
  
### <a name="parameters"></a>参数  
 `time`  
 新的日期/时间值中。  
  
### <a name="return-value"></a>返回值  
 已更新`CTime`对象。  
  
### <a name="remarks"></a>备注  
 此重载的赋值运算符将源时间复制到此`CTime`对象。 中的内部时间存储`CTime`对象所在的时区无关。 在分配期间不需要时区转换。  
  
##  <a name="operator_add_-"></a>  CTime::operator +、-  
 这些运算符加法和减法`CTimeSpan`和`CTime`对象。  
  
```  
CTime operator+(CTimeSpan timeSpan) const throw(); 
CTime operator-(CTimeSpan timeSpan) const throw(); 
CTimeSpan operator-(CTime time) const throw(); 
```  
  
### <a name="parameters"></a>参数  
 *时间跨度*  
 `CTimeSpan`要加上或减去对象。  
  
 `time`  
 `CTime`要减去的对象。  
  
### <a name="return-value"></a>返回值  
 A`CTime`或`CTimeSpan`表示操作的结果对象。  
  
### <a name="remarks"></a>备注  
 `CTime` 对象表示绝对时间，`CTimeSpan`对象表示相对时间。 前两个运算符使您得以加法和减法`CTimeSpan`对象来回`CTime`对象。 第三个运算符，你可以减去`CTime`从另一个用来生成对象`CTimeSpan`对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#159](../../atl-mfc-shared/codesnippet/cpp/ctime-class_13.cpp)]  
  
##  <a name="operator_add_eq_-_eq"></a>  CTime::operator + =、 =  
 这些运算符加法和减法`CTimeSpan`对象与其他这`CTime`对象。  
  
```  
CTime& operator+=(CTimeSpan span) throw();
CTime& operator-=(CTimeSpan span) throw();
```  
  
### <a name="parameters"></a>参数  
 `span`  
 `CTimeSpan`要加上或减去对象。  
  
### <a name="return-value"></a>返回值  
 已更新`CTime`对象。  
  
### <a name="remarks"></a>备注  
 这些运算符使您得以加法和减法`CTimeSpan`对象与其他这`CTime`对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#160](../../atl-mfc-shared/codesnippet/cpp/ctime-class_14.cpp)]  
  
##  <a name="serialize64"></a>  CTime::Serialize64  
  
> [!NOTE]
>  此方法仅在 MFC 项目中可用。  
  
 序列化到或从存档的成员变量与关联的数据。  
  
```  
CArchive& Serialize64(CArchive& ar);
```  
  
### <a name="parameters"></a>参数  
 `ar`  
 `CArchive`你想要更新的对象。  
  
### <a name="return-value"></a>返回值  
 已更新`CArchive`对象。  
  
## <a name="see-also"></a>请参阅  
 [asctime_s、_wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [_ftime_s、 _ftime32_s、 _ftime64_s](../../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)   
 [gmtime_s、_gmtime32_s、_gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime_s、_localtime32_s、_localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [strftime、wcsftime、_strftime_l、_wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [CTimeSpan 类](../../atl-mfc-shared/reference/ctimespan-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)


