总操作流程：
- 1、使用饿了么组件
- 2、写函数
- 3、测试

***

# 使用饿了么组件

> 使用树形的组件

```html
 <el-tree :data="data" :props="defaultProps" @node-click="handleNodeClick"></el-tree>
```
>date
```js
data() {
      return {
        data: [],
        defaultProps: {
          children: 'children',
          label: 'name'
        }
      }
```
# 写函数

```js
getTreeJson() {
        let attr = {//行级json的属性
          id: 'id',
          parendId: 'parendId',
          name: 'name',
          rootId: 1
        };
        this.axios.get('static/json/test.json')
          .then((response) => {
            this.data = this.toTreeData(response.data.rows, attr);
           
          }).catch((response) => {
            console.log(response);
          })
      },
      toTreeData(data, attr) {
        let tree = [];
        let resData = data;
        for (let i = 0; i < resData.length; i++) {
          if (resData[i].parendId === attr.rootId) {
            let obj = {
              id: resData[i][attr.id],
              name: resData[i][attr.name],
              children: []
            };
            tree.push(obj);
            resData.splice(i, 1);
            i--;name
          }
        }
        var run = function (treeArrs) {
          if (resData.length > 0) {
            for (let i = 0; i < treeArrs.length; i++) {
              for (let j = 0; j < resData.length; j++) {
                if (treeArrs[i].id === resData[j][attr.parendId]) {
                  let obj = {
                    id: resData[j][attr.id],
                    name: resData[j][attr.name],
                    children: []
                  };
                  treeArrs[i].children.push(obj);
                  resData.splice(j, 1);
                  j--;
                }
              }
              run(treeArrs[i].children);
            }
          }
        };
        run(tree);
        return tree;
      }
```

> json

```json
{
  "code": "OK",
  "msg": "成功",
  "time": "2019-01-02",
  "offset": 0,
  "page": 1,
  "limit": 10,
  "total": 84,
  "rows": [{
      "id": 3,
      "name": "bbbb",
      "parendId": 1
    },
    {
      "id": 2,
      "name": "aaaaa",
      "parendId": 2
    },
    {
      "id": 4,
      "name": "ccccc",
      "parendId": 1
    },
    {
      "id": 5,
      "name": "ddddd",
      "parendId": 4
    },
    {
      "id": 6,
      "name": "eeeee",
      "parendId": 4
    },
    {
      "id": 7,
      "name": "ffff",
      "parendId": 6
    },
    {
      "id": 8,
      "name": "ggggg",
      "parendId": 3
    },
    {
      "id": 9,
      "name": "hhhhh",
      "parendId": 5
    },
    {
      "id": 10,
      "name": "jjjj",
      "parendId": 6
    }
  ]

}

```

# 测试

运行看效果

