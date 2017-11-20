# 前端页面代码生成器
托拽定制的组件生成页面。

## 组件
编辑组件时显示的 HTML。此 HTML 和生成代码的 HTML 没有关系。
```
{
  html: '',
  editPoint: {
    'root': [{
      key: 'pic',
      name: '编辑字段的描述'
      value: xxx
    },{

    }],
    '.item': [{
      
    }]
    
  }
}
```

根据 editPoint 的配置，点击组件下的内容，右侧显示响应的配置内容。

editPoint 的配置规则是，
```
选择器: [{
  key: // 修改的属性的值
  name: // 编辑字段的描述
  type: // 类型。有 string, number, select, list, icon。 如果是icon，则选 icon。
  options: [{ // type 为 select 时，下拉框选型
    name: // 显示的文字
    value: // 值
  }, ...]
  itemType: // type 为 list 时。有 string, number, select, icon, object
  itemOptions: // itemType 为 select 时
  itemScheme: [{ // itemType 是 object 时
    name: ,
    type: , // 和 options 一致
    options: 
  }]
}]
```

选择器的值是 root 时，表示点根节点，显示的内容。目前暂时只支持 root。


CSS 会统一写在一个文件里。

## 组件列表
* 幻灯
* 搜索。输入框+按钮那。
* 导航列表。图标+文字。
* 底部导航

## 页面
根据配置文件生成代码。

配置文件,形如

```
{
  target: 'mobile', // 生成页面类型。手机，PC。
  framework: 'Vue', // jQuery, Vue等。
  importResourceType: 'import', //加载组件资源的方式。 raw： 用原生的写法，link，script。import ： 用 import 的方式。
  components: [{
    name: 'slider',// 幻灯组件
    config: {
      items: ['xx.jpg', 'xx.png'],
      iterval: 3000
    }
  }, {
    name: 'footerNav', // 底部
    config: {
      items: [{
        icon: 'home'
        name: '首页',
        href: 'xxxx'
      }, {
        icon: 'shop',
        name: '购物车',
        href: 'xxx'
      }
      ]
    }
  },
  ...]
}
```

第一版，framework 只支持 Vue， importResourceType 只支持 import。

## 其他
自带图标的资源。

