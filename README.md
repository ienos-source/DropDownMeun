# DropDownMeun

[![License](https://img.shields.io/badge/license-MIT-brightgreen.svg)](https://github.com/iOS-PPG/OC-Code/blob/master/LICENSE)    ![Platforms](https://img.shields.io/badge/platforms-iOS-orange.svg)  ![pod](https://img.shields.io/cocoapods/v/DropDownMeun.svg?style=plastic)

一个下拉筛选的控件

-------

### 预览
![Demo](/DropDownMeun/Resource/demo.gif)


### 基本说明
> HJDropDownMeun 的 frame 为顶部视图的 frame, 下拉菜单的视图添加在 HJDropDownMeun 的父视图上，frame 根据 HJDropDownMeun 向下铺满

### 层级说明
```
{
  Column {
    Section {
      Row
    }
  }
}
```

| NAME | EXPLAIN |
|:---:|:---:|
| Column | 顶部列表 |
| Section | 若为单级列表，numberOfSection = 1; 若为双级列表，numberOfSection > 1 |
| Row | 若为单级列表, numberOfRow 为行数；若为双级列表，numberOfRow 为第二级行数 |

### 使用方法


| PROPERTY | EXPLAIN |
|:---:|:---:|
| selectColor | item 选中的颜色 |
| normalColor | item 正常状态的颜色 |



**实现 HJDropDownMeunDataSource 的方法：**

```Objective-C
// [Required] - 返回顶部列表的个数
- (NSInteger)numberOfColumnsInDropDownMeun:(HJDropDownMeun *)meun

// [Optional] - 返回 1 时（默认），展示单列表；> 1 时，为双级列表的第一级行数
- (NSInteger)dropDownMeun:(HJDropDownMeun *)meun numberSectionInColumn:(NSInteger)column;

// [Required] - 返回子级列表个数：单级列表行数、双级列表的第二级行数
- (NSInteger)dropDownMeun:(HJDropDownMeun *)meun numberRowInSectionAtIndexPath:(HJIndexPath *)indexPath

// [Required] - 返回顶部列表对应 index 的标题
- (NSString *)dropDownMeun:(HJDropDownMeun *)meun titleForColumn:(NSInteger)column;

// [Optional] - 返回 Section 列表对应 index 的标题
- (NSString *)dropDownMeun:(HJDropDownMeun *)meun titleForSectionAtIndexPath:(HJIndexPath *)indexPath;

// [Required] - 返回 Row 列表对应 index 的标题
- (NSString *)dropDownMeun:(HJDropDownMeun *)meun titleForRowAtIndexPath:(HJIndexPath *)indexPath;

// [Optional] - 返回 Column 列表的字体
- (UIFont *)dropDownMeun:(HJDropDownMeun *)meun fontForColumn:(NSInteger)column;

// [Optional] - 返回 Section 列表的字体
- (UIFont *)dropDownMeun:(HJDropDownMeun *)meun fontForSection:(NSInteger)section;

// [Optional] - 返回 Row 列表的字体
- (UIFont *)dropDownMeun:(HJDropDownMeun *)meun fontForRow:(NSInteger)row;
```


**实现 HJDropDownMeunDelegate 的方法 [Optional]:**


```Objective-C
// 点击 Row 回调
- (void)dropDownMeun:(HJDropDownMeun *)meun didSelectRowAtIndexPath:(HJIndexPath *)indexPath;

// 返回 Column 的宽度
- (CGFloat)dropDownMeun:(HJDropDownMeun *)meun widthForColumn:(NSInteger)column;

// 返回 Section 的高度
- (CGFloat)heigtForSectionInDropDownMeun:(HJDropDownMeun *)meun;

// 返回 Row 的高度
- (CGFloat)heigtForRowInDropDownMeun:(HJDropDownMeun *)meun;
```
