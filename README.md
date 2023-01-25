# SiteInfoDB

## 简介

这个项目旨在收集尽可能多的网站的信息。
收集的信息包括但不限于网站标题、描述、关键词、图标。

所有收集的数据将存储在一个SQLite数据库中，供所有人查询。

同时，我们欢迎任何人向这个数据库中添加、修改和更新信息。**但，除非网站关闭，不得删除任何网站的信息。**

## 数据库结构

### 表的命名

目前，数据库中有一个名为`zh-Hans`的表，里面的所有数据均以简体中文撰写。（但这并不意味着其中只有简体中文网站）

未来，随着支持项目的人变多，数据库可能会新增其他语言的表。
新增加的表需要使用相同形式的命名，来说明表内数据的语言。

### 字段

目前，对于数据库内的一条记录，有以下字段:

| 字段名 | 类型 | 默认值 | 说明 | 是否允许NULL |
| --- | --- | --- | --- | --- |
| URL | TEXT | None | 主键&唯一 | No |
| NAME | TEXT | None | None | No |
| ICON | TEXT | NULL | None | Yes |
| KEYWORD | TEXT | NULL | 用逗号分隔多个关键词 | Yes |
| DESCRIPTION | TEXT | NULL | None | Yes |
| LANG | TEXT | NULL | 对于**单个页面内**支持多语言的网页用逗号分隔，如果网页支持较多语言，则跟随当前表的语言 | Yes |
| REIGON | TEXT | NULL | 网页服务器或其拥有者所在的位置，只能是一个  | Yes |
| POPULARITY | FLOAT | 0 | 网站热度，计算方法为: `log(网站月访问量)`, 四舍五入1位小数 | Yes |
| UPDATE_TIME | TIMESTAMP | current_timestamp | 由数据库内的trigger自动更新 | No |
| CREATE_TIME | TIMESTAMP | current_timestamp | 不得更改 | No |
| UPDATE_TIMES | INT | 0 | 修改次数，由数据库内的trigger自动更新 | No |

未来，我们可能会增加新的字段。添加数据时，至少要提供URL和网站名称。修改数据时，请遵循上表的说明。

---

# SiteInfoDB

## Intro

This project aims to collect a lot of information about websites.
The information includes but is not limited to title, description, keyword, icon.

All collected data will be stored in a SQLite database and will be open to everyone.

We also welcome anyone to add, modify and update information in this database.
**However, no site may be deleted unless the site is closed.**

## Database structure

### Table naming

Currently, there is a table named `zh-Hans` in the database, and all the data in it is written in Simplified Chinese. (But this does not mean that only Simplified Chinese sites are in it)

In the future, as more people join the project, tables in other languages may be added to the database.
Newly added tables should use the same form of naming to show the language of data.

### Fields

Currently, for a record in the database, there are following fields:

| Name | Type | Default Value | Note | Allow NULL |
| --- | --- | --- | --- | --- |
| URL | TEXT | None | Primary Key & Unique | No |
| NAME | TEXT | None | None | No |
| ICON | TEXT | NULL | None | Yes |
| KEYWORD | TEXT | NULL | Separate multiple keywords with commas | Yes |
| DESCRIPTION | TEXT | NULL | None | Yes |
| LANG | TEXT | NULL | Comma-separated for multi-language website **in one page**, if the site has many languages, follow the language of the current table| Yes |
| REIGON | TEXT | NULL | The location of the server or its owner, only one | YES |
| POPULARITY | FLOAT | 0 | The website popularity, calculated as `log(monthly visits)`, and round to 1 decimal place | Yes |
| UPDATE_TIME | TIMESTAMP | current_timestamp | Automatically updated by the trigger in the database | No |
| CREATE_TIME | TIMESTAMP | current_timestamp | cannot be changed | No |
| UPDATE_TIMES | INT | 0 | Number of modifications, automatically updated by the database trigger | No |

In the future, we may add new fields. When adding data, provide at least the URL and website name. When modifying data, please follow the note in the table above.
