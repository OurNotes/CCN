总操作流程;
- 1、[写代码](#vue.js-01)
- 2、[测试](#vue.js-02)

***

- 项目目录结构

![](image/21-1.png)

# <a name="vue.js-01" href="#" >写代码</a>

> 1、sql server的sql

```sql

-- ----------------------------
-- Table structure for MENU
-- ----------------------------
IF EXISTS (SELECT * FROM sys.all_objects WHERE object_id = OBJECT_ID(N'[dbo].[MENU]') AND type IN ('U'))
	DROP TABLE [dbo].[MENU]
GO

CREATE TABLE [dbo].[MENU] (
  [menuID] bigint  NOT NULL,
  [menuParent] bigint  NOT NULL,
  [menuName] varchar(255) COLLATE Chinese_PRC_CI_AS  NOT NULL,
  [menuUrl] varchar(255) COLLATE Chinese_PRC_CI_AS  NULL,
  [menuIcon] varchar(255) COLLATE Chinese_PRC_CI_AS  NULL,
  [menuIs] int  NULL,
  [menuCode] varchar(255) COLLATE Chinese_PRC_CI_AS  NULL,
  [createTime] datetime  NULL,
  [updateTime] datetime  NULL,
  [lastLoginTime] datetime  NULL
)
GO

ALTER TABLE [dbo].[MENU] SET (LOCK_ESCALATION = TABLE)
GO


-- ----------------------------
-- Records of MENU
-- ----------------------------
INSERT INTO [dbo].[MENU]  VALUES (N'1', N'0', N'系统管理', N'', N'iconfont icon-xitongshezhi', N'1', N'', N'2019-04-17 15:41:11.000', N'2019-04-17 15:41:14.000', N'2019-04-17 15:41:16.000')
GO

INSERT INTO [dbo].[MENU]  VALUES (N'2', N'1', N'用户管理', N'@/components/use/UserContainers', N'iconfont icon-yonghuguanli', N'0', N'UserContainers', N'2019-04-17 15:41:49.000', N'2019-04-17 15:41:51.000', N'2019-04-17 15:41:54.000')
GO

INSERT INTO [dbo].[MENU]  VALUES (N'3', N'1', N'权限管理', N'@/components/permissions/PermissionsContainers', N'iconfont icon-quanxianguanli', N'0', N'PermissionsContainers', N'2019-04-17 15:42:26.000', N'2019-04-17 15:42:29.000', N'2019-04-17 15:42:31.000')
GO

INSERT INTO [dbo].[MENU]  VALUES (N'4', N'1', N'菜单管理', N'@/components/menu/MenuContainers', N'iconfont icon-caidanguanli_', N'0', N'MenuContainers', N'2019-04-17 15:43:02.000', N'2019-04-17 15:43:04.000', N'2019-04-17 15:43:06.000')
GO

INSERT INTO [dbo].[MENU]  VALUES (N'5', N'0', N'业务管理', N'', N'iconfont icon-xitongyewuguanli', N'1', N'', N'2019-04-17 15:56:53.000', N'2019-04-17 15:56:55.000', N'2019-04-17 15:56:57.000')
GO

INSERT INTO [dbo].[MENU]  VALUES (N'6', N'5', N'制作管理', N'', N'iconfont icon-xiangmushenbao', N'1', N'', N'2019-04-17 15:57:17.000', N'2019-04-17 15:57:19.000', N'2019-04-17 15:57:21.000')
GO

INSERT INTO [dbo].[MENU]  VALUES (N'7', N'6', N'生产进度', N'@/components/menu/MenuContainers1', N'iconfont icon-icon-p_mrpjinduzhuizong', N'0', N'MenuContainers1', N'2019-04-17 15:58:07.000', N'2019-04-17 15:58:10.000', N'2019-04-17 15:58:12.000')
GO


-- ----------------------------
-- Primary Key structure for table MENU
-- ----------------------------
ALTER TABLE [dbo].[MENU] ADD CONSTRAINT [PK__MENU__3B407E942F10007B] PRIMARY KEY CLUSTERED ([menuID])
WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON)  
ON [PRIMARY]
GO


```

> 2、vue引用

```html
<ThreeMenu :menu="menu" @three="three"></ThreeMenu>
```

```js
import menuu from '@/components/home/threeMenu'

```

```js
components: {
      menuu,
    },
    methods: {
three(val) { //左边点击切换内容
        console.log(val);
      },
    }

    
```

```js
getJson() { //获取后台json数据
        const that = this;
        this.axios({
            method: "get",
            headers: {
              'Content-Type': 'application/json'
            },
            url: 'http://localhost:8089/menu/getMenu'

          })
          .then((response) => {
            let dataJson = that.treeData(response.data.rows, 'menuID', 'menuParent', 'children');
            console.log(dataJson);
            that.menu = dataJson;
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


>3、vue的递归方式的组件

```html
<template>
  <el-menu class="el-menu-vertical-demo" default-active="1" unique-opened @select="handleSelect">
    <template v-for="list in menu">
      <el-submenu v-if="list.children" :index="String(list.menuID)" :key="list.menuID">
        <template slot="title">
          <i :class="list.menuIcon"></i>
          <span>{{list.menuName}}</span>
        </template>
        <el-menu-item-group>
          <Menu :menu="list.children" v-if="list.children" @three="(menuCode)=>$emit('three',menuCode)"></Menu>
        </el-menu-item-group>
      </el-submenu>
      <el-menu-item v-else :index="String(list.menuCode)" :key="list.menuID">
        <i :class="list.menuIcon"></i><span>{{list.menuName}}</span>
      </el-menu-item>
    </template>
  </el-menu>
</template>

<script>
  export default {
    name: 'Menu',
    props: {
      menu: null
    },
    data() {
      return {
        menucode: ''
      }
    },
    watch: {
      menucode: function (newVal, oldVal) {
        if (newVal != oldVal) {
          this.$emit('three', this.menucode);
        }
      }
    },
    methods: {
      handleSelect(key, keyPath) {
        this.menucode = key;
      }

    }
  }
</script>

<style>


</style>

```

# <a name="vue.js-02" href="#" >测试</a>

运行测试


