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
        this.axios.get('static/json/test.json')
          .then((response) => {
            this.data = this.treeData(response.data.rows, 'id','parendId','children');
           
          }).catch((response) => {
            console.log(response);
          })
      },
       treeData(source, id, parentId, children) {
        let cloneData = JSON.parse(JSON.stringify(source))
        return cloneData.filter(father => {
          let branchArr = cloneData.filter(child => father[id] == child[parentId]);
          branchArr.length > 0 ? father[children] = branchArr : ''
          return father[parentId] == 0
        })
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

