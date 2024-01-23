# 简单 Excel 导入导出工具库

🌈 简单使用， 方便快捷。 支持 `xls` `xlsx` `csv`

依赖：PhpSpreadsheet

## 使用

### 导入

```php
$arr = SimpleExcel::import(dirname(__DIR__) . '/test/test.xlsx', 'xlsx', array(
    '姓名'      => 'name',
    '年龄'      => 'age',
    '性别'      => 'gender'
));
var_dump($arr);
```

### 导出

```php
// 导出到文件
SimpleExcel::export('/tmp/dump.xlsx', 'xlsx', [
    'name'      => '姓名',
    'idcard'    => '身份证',
    'mobile'    => '手机号'
], [
    ['name' => '张三', 'idcard' => '`522131199703213342', 'mobile'=>'18311548011'],
    ['name' => '李四', 'idcard' => '`522131199703213342', 'mobile' => '18311548011'],
    ['name' => '赵五', 'idcard' => '`522131199703213342', 'mobile' => '18311548011'],
],'#ff0000', '#00ff00', '#333333');

// 直接下载导出数据
SimpleExcel::setDownloadHeader('导出数据.xlsx'); // 设置下载文件响应头
SimpleExcel::export('php://output', 'xlsx', [
    'name'      => '姓名',
    'idcard'    => '身份证',
    'mobile'    => '手机号'
], [
    ['name' => '张三', 'idcard' => '`522131199703213342', 'mobile'=>'18311548011'],
    ['name' => '李四', 'idcard' => '`522131199703213342', 'mobile' => '18311548011'],
    ['name' => '赵五', 'idcard' => '`522131199703213342', 'mobile' => '18311548011'],
],'#ff0000', '#00ff00', '#333333');
```