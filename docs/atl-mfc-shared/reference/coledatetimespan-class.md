---
title: "COleDateTimeSpan 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::Format
- ATLCOMTIME/ATL::COleDateTimeSpan::GetDays
- ATLCOMTIME/ATL::COleDateTimeSpan::GetHours
- ATLCOMTIME/ATL::COleDateTimeSpan::GetMinutes
- ATLCOMTIME/ATL::COleDateTimeSpan::GetSeconds
- ATLCOMTIME/ATL::COleDateTimeSpan::GetStatus
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalDays
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalHours
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalMinutes
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalSeconds
- ATLCOMTIME/ATL::COleDateTimeSpan::SetDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::SetStatus
- ATLCOMTIME/ATL::COleDateTimeSpan::m_span
- ATLCOMTIME/ATL::COleDateTimeSpan::m_status
dev_langs:
- C++
helpviewer_keywords:
- timespan
- time span
- shared classes, COleDateTimeSpan
- Date data type, MFC encapsulation of
- COleDateTimeSpan class
ms.assetid: 7441526d-a30a-4019-8fb3-3fee6f897cbe
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 173ae35f49379bcccf552a105b5615378e7a42cd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="coledatetimespan-class"></a>COleDateTimeSpan 类
表示相对时间的时间范围。  
  
## <a name="syntax"></a>语法  
  
```
class COleDateTimeSpan
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[COleDateTimeSpan::COleDateTimeSpan](#coledatetimespan)|构造 `COleDateTimeSpan` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[COleDateTimeSpan::Format](#format)|生成的格式化的字符串表示形式`COleDateTimeSpan`对象。|  
|[COleDateTimeSpan::GetDays](#getdays)|返回范围的日部分此`COleDateTimeSpan`对象所表示。|  
|[COleDateTimeSpan::GetHours](#gethours)|返回范围的小时部分此`COleDateTimeSpan`对象所表示。|  
|[COleDateTimeSpan::GetMinutes](#getminutes)|返回范围的分钟部分此`COleDateTimeSpan`对象所表示。|  
|[COleDateTimeSpan::GetSeconds](#getseconds)|返回范围的第二个部分此`COleDateTimeSpan`对象所表示。|  
|[COleDateTimeSpan::GetStatus](#getstatus)|获取此状态 （有效期）`COleDateTimeSpan`对象。|  
|[COleDateTimeSpan::GetTotalDays](#gettotaldays)|此返回的天数`COleDateTimeSpan`对象所表示。|  
|[COleDateTimeSpan::GetTotalHours](#gettotalhours)|返回的小时数这`COleDateTimeSpan`对象所表示。|  
|[COleDateTimeSpan::GetTotalMinutes](#gettotalminutes)|返回的分钟数这`COleDateTimeSpan`对象所表示。|  
|[COleDateTimeSpan::GetTotalSeconds](#gettotalseconds)|返回的秒数这`COleDateTimeSpan`对象所表示。|  
|[COleDateTimeSpan::SetDateTimeSpan](#setdatetimespan)|设置此值`COleDateTimeSpan`对象。|  
|[COleDateTimeSpan::SetStatus](#setstatus)|设置的状态 （有效期） 这`COleDateTimeSpan`对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|||  
|-|-|  
|[运算符 +、-](#operator_add_-)|添加、 subtract、 和更改符号`COleDateTimeSpan`值。|  
|[运算符 + =、 =](#operator_add_eq_-_eq)|加法和减法`COleDateTimeSpan`从此值`COleDateTimeSpan`值。|  
|[运算符 =](#operator_eq)|副本`COleDateTimeSpan`值。|  
|[运算符 = =、 <、 < =](#coledatetimespan_relational_operators)|比较两个`COleDateTimeSpan`值。|  
|[运算符 double](#operator_double)|将此转换`COleDateTimeSpan`值赋给**double**。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[COleDateTimeSpan::m_span](#m_span)|包含基础**double**此`COleDateTimeSpan`对象。|  
|[COleDateTimeSpan::m_status](#m_status)|包含此状态`COleDateTimeSpan`对象。|  
  
## <a name="remarks"></a>备注  
 `COleDateTimeSpan`没有基类。  
  
 A`COleDateTimeSpan`将以天为单位的时间。  
  
 `COleDateTimeSpan`适用于其伴生类[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)。 `COleDateTime`封装**日期**OLE 自动化的数据类型。 `COleDateTime`表示绝对时间值。 所有`COleDateTime`计算涉及`COleDateTimeSpan`值。 这些类之间的关系相当于间的一个[CTime](../../atl-mfc-shared/reference/ctime-class.md)和[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)。  
  
 有关详细信息`COleDateTime`和`COleDateTimeSpan`类，请参阅文章[日期和时间： 自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。  
  
## <a name="requirements"></a>惠?  
 **标头：** ATLComTime.h  
  
##  <a name="coledatetimespan_relational_operators"></a>COleDateTimeSpan 关系运算符  
 比较运算符。  
  
```
bool operator==(const COleDateTimeSpan& dateSpan) const throw();
bool operator!=(const COleDateTimeSpan& dateSpan) const throw();
bool operator<(const COleDateTimeSpan& dateSpan) const throw();
bool operator>(const COleDateTimeSpan& dateSpan) const throw();
bool operator<=(const COleDateTimeSpan& dateSpan) const throw();
bool operator>=(const COleDateTimeSpan& dateSpan) const throw();
```  
  
### <a name="parameters"></a>参数  
 *dateSpan*  
 要比较的 `COleDateTimeSpan`。  
  
### <a name="return-value"></a>返回值  
 这些运算符比较两个日期/时间范围值，并返回**true**如果条件为 true; 否则为**false**。  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  如果任一操作数是无效，将发生 ATLASSERT。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#25](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_1.cpp)]  
  
 [!code-cpp[NVC_ATLMFC_Utilities#26](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_2.cpp)]  
  
##  <a name="coledatetimespan"></a>COleDateTimeSpan::COleDateTimeSpan  
 构造 `COleDateTimeSpan` 对象。  
  
```
COleDateTimeSpan() throw();
COleDateTimeSpan(double dblSpanSrc) throw();
COleDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```  
  
### <a name="parameters"></a>参数  
 `dblSpanSrc`  
 要复制到新的天数`COleDateTimeSpan`对象。  
  
 `lDays`, `nHours`, `nMins`, `nSecs`  
 指示要复制到新的日期和时间值`COleDateTimeSpan`对象。  
  
### <a name="remarks"></a>备注  
 所有这些构造函数创建新`COleDateTimeSpan`对象初始化为指定的值。 这些构造函数的简要描述如下所示：  
  
- **COleDateTimeSpan （)**构造`COleDateTimeSpan`对象初始化为 0。  
  
- **COleDateTimeSpan (** `dblSpanSrc` **)**构造`COleDateTimeSpan`从浮点值的对象。  
  
- **COleDateTimeSpan (** `lDays` **，** `nHours` **，** `nMins` **，** `nSecs` **)** 构造`COleDateTimeSpan`对象初始化为指定的数字值。  
  
 新的状态`COleDateTimeSpan`对象设置为有效。  
  
 有关详细信息有关的边界`COleDateTimeSpan`值，请参阅文章[日期和时间： 自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#14](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_3.cpp)]  
  
##  <a name="format"></a>COleDateTimeSpan::Format  
 生成的格式化的字符串表示形式`COleDateTimeSpan`对象。  
  
```
CString Format(LPCTSTR pFormat) const;
CString Format(UINT nID) const;
```  
  
### <a name="parameters"></a>参数  
 `pFormat`  
 格式设置字符串类似于`printf`格式化字符串。 格式设置代码，前面是百分比 ( `%`) 登录，替换为相应`COleDateTimeSpan`组件。 格式设置字符串中的其他字符被复制到返回的字符串不变。 值和含义的格式设置代码**格式**如下所示：  
  
- **%H**在当天的小时数  
  
- **%M**当前小时内的分钟数  
  
- **%S**当前分钟的秒数  
  
- **%%**百分比符号  
  
 上面列出的四个格式代码都将接受格式的唯一代码。  
  
-  
  
 `nID`  
 格式控件字符串资源 ID。  
  
### <a name="return-value"></a>返回值  
 A`CString`包含带格式的日期/时间范围值。  
  
### <a name="remarks"></a>备注  
 调用这些函数来创建时间跨度值的格式的表示。 如果此状态`COleDateTimeSpan`对象为 null，则返回值为空字符串。 如果状态为无效，将返回的字符串指定通过字符串资源**IDS_INVALID_DATETIMESPAN**。  
  
 此函数的窗体的简短说明如下所示：  
  
 **格式 (** `pFormat` **)**  
 此窗体使用包含以百分号 （%） 开头的特殊格式设置代码格式字符串的值设置为在`printf`。 格式设置字符串作为参数传递给函数。  
  
 **格式 (** `nID` **)**  
 此窗体使用包含以百分号 （%） 开头的特殊格式设置代码格式字符串的值设置为在`printf`。 格式设置字符串是一个资源。 此字符串资源的 ID 作为参数传递。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#15](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_4.cpp)]  
  
##  <a name="getdays"></a>COleDateTimeSpan::GetDays  
 检索此日期/时间跨度值的日部分。  
  
```
LONG GetDays() const throw();
```  
  
### <a name="return-value"></a>返回值  
 此日期/时间跨度值的日部分。  
  
### <a name="remarks"></a>备注  
 返回值从之间此函数范围大约-3,615,000 和 3,615,000。  
  
 查询的值的其他函数`COleDateTimeSpan`对象，请参阅以下成员函数：  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#16](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_5.cpp)]  
  
##  <a name="gethours"></a>COleDateTimeSpan::GetHours  
 检索此日期/时间跨度值的小时部分。  
  
```
LONG GetHours() const throw();
```  
  
### <a name="return-value"></a>返回值  
 此日期/时间跨度值的小时数部分。  
  
### <a name="remarks"></a>备注  
 -23 到 23 之间的此函数范围中的返回值。  
  
 查询的值的其他函数`COleDateTimeSpan`对象，请参阅以下成员函数：  
  
- [GetDays](#getdays)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#17](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_6.cpp)]  
  
##  <a name="getminutes"></a>COleDateTimeSpan::GetMinutes  
 检索此日期/时间跨度值的分钟部分。  
  
```
LONG GetMinutes() const throw();
```  
  
### <a name="return-value"></a>返回值  
 此日期/时间跨度值的分钟部分。  
  
### <a name="remarks"></a>备注  
 -59 到 59 之间的此函数范围中的返回值。  
  
 查询的值的其他函数`COleDateTimeSpan`对象，请参阅以下成员函数：  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#18](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_7.cpp)]  
  
##  <a name="getseconds"></a>COleDateTimeSpan::GetSeconds  
 检索此日期/时间跨度值的第二个部分。  
  
```
LONG GetSeconds() const throw();
```  
  
### <a name="return-value"></a>返回值  
 此日期/时间跨度值的秒部分。  
  
### <a name="remarks"></a>备注  
 -59 到 59 之间的此函数范围中的返回值。  
  
 查询的值的其他函数`COleDateTimeSpan`对象，请参阅以下成员函数：  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#19](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_8.cpp)]  
  
##  <a name="getstatus"></a>COleDateTimeSpan::GetStatus  
 获取此状态 （有效期）`COleDateTimeSpan`对象。  
  
```
DateTimeSpanStatus GetStatus() const throw();
```  
  
### <a name="return-value"></a>返回值  
 此状态`COleDateTimeSpan`值。  
  
### <a name="remarks"></a>备注  
 返回值定义通过**DateTimeSpanStatus**枚举类型，在其中定义`COleDateTimeSpan`类。  
  
```  
enum DateTimeSpanStatus{  
   valid = 0,  
   invalid = 1,  
   null = 2,  
};  
```  
  
 有关这些状态值的简短说明，请参阅下面的列表：  
  
- **COleDateTimeSpan::valid**指示此`COleDateTimeSpan`对象是否有效。  
  
- **COleDateTimeSpan::invalid**指示此`COleDateTimeSpan`对象无效; 即，其值可能不正确。  
  
- **COleDateTimeSpan::null**指示此`COleDateTimeSpan`对象为 null，也就是说，已为此对象中提供任何值。 (这是在数据库的意义上的"having 没有值，"，而不 c + +"null" **NULL**。)  
  
 状态`COleDateTimeSpan`对象在是在以下情况下无效：  
  
-   如果此对象已溢出或下溢在过程中遇到算术赋值操作，也就是说，`+=`或`-=`。  
  
-   如果无效的值分配给此对象。  
  
-   如果已显式设置此对象的状态为无效的使用`SetStatus`。  
  
 有关可能会将状态设置为无效的操作的详细信息，请参阅[COleDateTimeSpan::operator +、-](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-)和[COleDateTimeSpan::operator + =、-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq)。  
  
 有关详细信息有关的边界`COleDateTimeSpan`值，请参阅文章[日期和时间： 自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。  
  
##  <a name="gettotaldays"></a>COleDateTimeSpan::GetTotalDays  
 检索此以天数表示的日期/时间范围值。  
  
```
double GetTotalDays() const throw();
```  
  
### <a name="return-value"></a>返回值  
 以天数表示此日期/时间范围值。 尽管此函数的原型返回双精度值，它将始终返回一个整数值。  
  
### <a name="remarks"></a>备注  
 大约-3.65e6 和 3.65e6 之间此函数范围中的返回值。  
  
 查询的值的其他函数`COleDateTimeSpan`对象，请参阅以下成员函数：  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#20](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_9.cpp)]  
  
##  <a name="gettotalhours"></a>COleDateTimeSpan::GetTotalHours  
 检索此日期/时间范围值，以小时为单位。  
  
```
double GetTotalHours() const throw();
```  
  
### <a name="return-value"></a>返回值  
 此日期/时间范围值，以小时为单位。 尽管此函数的原型返回双精度值，它将始终返回一个整数值。  
  
### <a name="remarks"></a>备注  
 大约-8.77e7 和 8.77e7 之间此函数范围中的返回值。  
  
 查询的值的其他函数`COleDateTimeSpan`对象，请参阅以下成员函数：  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>示例  
 请参阅示例[GetTotalDays](#gettotaldays)。  
  
##  <a name="gettotalminutes"></a>COleDateTimeSpan::GetTotalMinutes  
 检索此以分钟为单位表示的日期/时间范围值。  
  
```
double GetTotalMinutes() const throw();
```  
  
### <a name="return-value"></a>返回值  
 以分钟为单位表示此日期/时间范围值。 尽管此函数的原型返回双精度值，它将始终返回一个整数值。  
  
### <a name="remarks"></a>备注  
 大约-5.26e9 和 5.26e9 之间此函数范围中的返回值。  
  
 查询的值的其他函数`COleDateTimeSpan`对象，请参阅以下成员函数：  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>示例  
 请参阅示例[GetTotalDays](#gettotaldays)。  
  
##  <a name="gettotalseconds"></a>COleDateTimeSpan::GetTotalSeconds  
 检索此用秒数表示的日期/时间范围值。  
  
```
double GetTotalSeconds() const throw();
```  
  
### <a name="return-value"></a>返回值  
 此日期/时间范围值，以秒为单位。 尽管此函数的原型返回双精度值，它将始终返回一个整数值。  
  
### <a name="remarks"></a>备注  
 此函数的返回值的范围介于之间大约-3.16e11 到 3.16e11。  
  
 查询的值的其他函数`COleDateTimeSpan`对象，请参阅以下成员函数：  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
### <a name="example"></a>示例  
 请参阅示例[GetTotalDays](#gettotaldays)。  
  
##  <a name="m_span"></a>COleDateTimeSpan::m_span  
 基础**double**值为`COleDateTime`对象。  
  
```
double m_span;
```  
  
### <a name="remarks"></a>备注  
 此值表示日期/时间范围以天为单位。  
  
> [!CAUTION]
>  更改中的值**double**数据成员将更改此值`COleDateTimeSpan`对象。 它不会更改此状态`COleDateTimeSpan`对象。  
  
##  <a name="m_status"></a>COleDateTimeSpan::m_status  
 此数据成员的类型是枚举的类型**DateTimeSpanStatus**，其定义内`COleDateTimeSpan`类。  
  
```
DateTimeSpanStatus m_status;
```  
  
### <a name="remarks"></a>备注  
  
```  
enum DateTimeSpanStatus{  
   valid = 0,  
   invalid = 1,  
   null = 2,  
   };  
```  
  
 有关这些状态值的简短说明，请参阅下面的列表：  
  
- **COleDateTimeSpan::valid**指示此`COleDateTimeSpan`对象是否有效。  
  
- **COleDateTimeSpan::invalid**指示此`COleDateTimeSpan`对象无效; 即，其值可能不正确。  
  
- **COleDateTimeSpan::null**指示此`COleDateTimeSpan`对象为 null，也就是说，已为此对象中提供任何值。 (这是在数据库的意义上的"having 没有值，"，而不 c + +"null" **NULL**。)  
  
 状态`COleDateTimeSpan`对象在是在以下情况下无效：  
  
-   如果此对象已溢出或下溢在过程中遇到算术赋值操作，也就是说，`+=`或`-=`。  
  
-   如果无效的值分配给此对象。  
  
-   如果已显式设置此对象的状态为无效的使用[SetStatus](#setstatus)。  
  
 有关可能会将状态设置为无效的操作的详细信息，请参阅[COleDateTimeSpan::operator +、-](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-)和[COleDateTimeSpan::operator + =、-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq)。  
  
> [!CAUTION]
>  此数据成员是高级编程的情况下。 应使用内联成员函数[GetStatus](#getstatus)和[SetStatus](#setstatus)。 请参阅`SetStatus`的有关显式设置该数据成员的其他注意事项。  
  
 有关详细信息有关的边界`COleDateTimeSpan`值，请参阅文章[日期和时间： 自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。  
  
##  <a name="operator_eq"></a>COleDateTimeSpan::operator =  
 副本`COleDateTimeSpan`值。  
  
```
COleDateTimeSpan& operator=(double dblSpanSrc) throw();
```  
  
### <a name="remarks"></a>备注  
 此重载的赋值运算符将源日期/时间跨度值复制到此`COleDateTimeSpan`对象。  
  
##  <a name="operator_add_-"></a>COleDateTimeSpan::operator +、-  
 添加、 subtract、 和更改符号`COleDateTimeSpan`值。  
  
```
COleDateTimeSpan operator+(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-() const throw();
```  
  
### <a name="remarks"></a>备注  
 前两个运算符，可以添加并将日期/时间跨度值相减。 第三个可让你更改日期/时间跨度值的符号。  
  
 如果任一操作数是 null，生成的状态`COleDateTimeSpan`值为 null。  
  
 如果任一操作数无效，且另一个则不为 null，生成的状态`COleDateTimeSpan`值是否无效。  
  
 有关有效、 无效，和 null 的状态值的详细信息，请参阅[m_status](#m_status)成员变量。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#23](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_10.cpp)]  
  
##  <a name="operator_add_eq_-_eq"></a>COleDateTimeSpan::operator + =、 =  
 加法和减法`COleDateTimeSpan`从此值`COleDateTimeSpan`值。  
  
```
COleDateTimeSpan& operator+=(const COleDateTimeSpan dateSpan) throw();
COleDateTimeSpan& operator-=(const COleDateTimeSpan dateSpan) throw();
```  
  
### <a name="remarks"></a>备注  
 这些运算符用于添加和将从此日期/时间跨度值相减`COleDateTimeSpan`对象。 如果任一操作数是 null，生成的状态`COleDateTimeSpan`值为 null。  
  
 如果任一操作数无效，且另一个则不为 null，生成的状态`COleDateTimeSpan`值是否无效。  
  
 有关有效、 无效，和 null 的状态值的详细信息，请参阅[m_status](#m_status)成员变量。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#24](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_11.cpp)]  
  
##  <a name="operator_double"></a>COleDateTimeSpan::operator double  
 将此转换`COleDateTimeSpan`值赋给**double**。  
  
```
operator double() const throw();
```  
  
### <a name="remarks"></a>备注  
 此运算符返回的值`COleDateTimeSpan`作为天浮点数的值。  
  
##  <a name="setdatetimespan"></a>COleDateTimeSpan::SetDateTimeSpan  
 设置此日期/时间跨度值的值。  
  
```
void SetDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```  
  
### <a name="parameters"></a>参数  
 `lDays`, `nHours`, `nMins`, `nSecs`  
 指示要复制到这的日期范围和时间跨度值`COleDateTimeSpan`对象。  
  
### <a name="remarks"></a>备注  
 有关查询的值的函数`COleDateTimeSpan`对象，请参阅以下成员函数：  
  
- [GetDays](#getdays)  
  
- [GetHours](#gethours)  
  
- [GetMinutes](#getminutes)  
  
- [GetSeconds](#getseconds)  
  
- [GetTotalDays](#gettotaldays)  
  
- [GetTotalHours](#gettotalhours)  
  
- [GetTotalMinutes](#gettotalminutes)  
  
- [GetTotalSeconds](#gettotalseconds)  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#21](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_12.cpp)]  
  
##  <a name="setstatus"></a>COleDateTimeSpan::SetStatus  
 设置的状态 （有效期） 这`COleDateTimeSpan`对象。  
  
```
void SetStatus(DateTimeSpanStatus status) throw();
```  
  
### <a name="parameters"></a>参数  
 *status*  
 此新状态值为`COleDateTimeSpan`对象。  
  
### <a name="remarks"></a>备注  
 *状态*参数值由定义**DateTimeSpanStatus**枚举类型，在其中定义`COleDateTimeSpan`类。  
  
```  
enum DateTimeSpanStatus{  
   valid = 0,  
   invalid = 1,  
   null = 2,  
   };  
```  
  
 有关这些状态值的简短说明，请参阅下面的列表：  
  
- **COleDateTimeSpan::valid**指示此`COleDateTimeSpan`对象是否有效。  
  
- **COleDateTimeSpan::invalid**指示此`COleDateTimeSpan`对象无效; 即，其值可能不正确。  
  
- **COleDateTimeSpan::null**指示此`COleDateTimeSpan`对象为 null，也就是说，已为此对象中提供任何值。 (这是在数据库的意义上的"having 没有值，"，而不 c + +"null" **NULL**。)  
  
    > [!CAUTION]
    >  此函数是高级编程的情况下。 此函数不会更改此对象中的数据。 它通常用于在将状态设置为`null`或**无效**。 请注意，赋值运算符 ([运算符 =](#eq)) 和[SetDateTimeSpan](#setdatetimespan)不要设置基于源值的对象的状态。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATLMFC_Utilities#22](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_13.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [COleDateTime 类](../../atl-mfc-shared/reference/coledatetime-class.md)   
 [CTime 类](../../atl-mfc-shared/reference/ctime-class.md)   
 [CTimeSpan 类](../../atl-mfc-shared/reference/ctimespan-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)


