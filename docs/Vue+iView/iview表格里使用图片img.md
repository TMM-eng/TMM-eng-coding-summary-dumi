# iview表格(table)里使用图片(img)

1.方法一

 ```json
{
    title: '头像',
    key: 'avatar',
    columns: {
        'width':'50px'
    },
    render: (h, params) => {
        return h('div', [
            h('img', {
                attrs: {
                    src: params.row.avatar
                },
                style: {
                    width: '30px',
                    height: '30px'
                }
            }),
        ]);
    }
}
```

2. 方法二

```json
{
    title: '头像',
    key: 'avatar',
    columns: {
        'width':'50px'
    },
    render: (h, params) => {
      return h('div', [
          h('img', {
            domProps: {
            'src': params.row.avatar
          },
          style: {
            width: '30px',
            height: '30px'
          },
      })
    ])
    }
}
```